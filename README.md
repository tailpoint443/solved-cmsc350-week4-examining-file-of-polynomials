Download Link: https://assignmentchef.com/product/solved-cmsc350-week4-examining-file-of-polynomials
<br>
The second programming project involves writing a program that examines a file of polynomials and determines whether the polynomials in that file are in strictly ascending order using two different methods of comparison.

Each line of the input file will contain one polynomial. On each line will be the terms of the polynomial. Each term will be represented as a pair of values. The first element of that pair is a real value that represents the coefficient and the second an integer value, which is its corresponding exponent. For example, 5.6 3 4 1 8.3 0 represents the polynomial 5.6<em>x</em><sup>3</sup> + 4<em>x</em> + 8.3. They are intended to be written from the highest exponent to the lowest, but ensuring that is true is a program requirement. Exponents with zero coefficients will be omitted

The program for this project should consist of four outer classes. The <sub>Polynomial</sub> class is the first of those four. Instances of the <sub>Polynomial</sub> class should define an individual polynomial. <sub>Polynomial</sub> objects should be represented internally by a singly linked list. Each node of that linked list should contain one term of the polynomial consisting of its coefficient and exponent. You are not permitted to use the predefined Java

LinkedList class, but instead must create the nodes of the linked list as instances of a static nested class inside the Polynomial class. The Polynomial class must implement both the Iterable and Comparable interfaces. It must have four public methods.

<ol>

 <li>A constructor that accepts a string that defines one polynomial in the same format as provided in the input file.</li>

 <li>A <sub>compareTo</sub> method that compares two polynomials. If the two polynomials have different highest order exponents, the one with the highest exponent is the greatest. If their highest exponents are the same, their coefficients are compared. If two polynomials have the same highest order exponent with the same coefficients the next highest exponent is examined, and so on.</li>

 <li>An <sub>iterator</sub> method that produces an iterator the iterates across the terms of the polynomial from highest exponent to lowest and returns and an object that contains only the coefficient and exponent of the next term.</li>

 <li>A <sub>toString</sub> method that converts a polynomial to a string. Terms with 0 coefficients should be omitted entirely. The exponent of the term with an exponent of 1 should omit the exponent and the term with exponent 0 should omit the variable <em>x</em> as well. As an example, the polynomial “5.6 3 4 1 8.3 0” should be converted to the following string “5.6x^3 + 4x + 8.3”.</li>

</ol>

The second class is <sub>InvalidPolynomialSyntax</sub>, which defines an unchecked exception that contains a constructor that allows a message to be supplied. It is thrown by the constructor of the <sub>Polynomial</sub> class should the supplied string contain coefficients or exponents of an improper type or should the exponents fail to be listed in strictly descending order.

The third class is <sub>OrderedList</sub>, which is a utility class that contains two overloaded implementations of a

method named <sub>checkSorted</sub>, which determines whether a <sub>List</sub> object, supplied as a parameter, is in strictly ascending order. Both methods should be class (static) methods. The first of the overloaded methods should accept a list that contains elements that implement <sub>Comparable</sub>. The second should instead be supplied an additional parameter that is an object of a class that implements the <sub>Comparator</sub> interface. Refer to the signatures of the two <sub>sort</sub> methods in the predefined Java <sub>Collections</sub> class as a model for how these two methods should be defined. Do not duplicate code, but instead ensure that first overloaded method calls the second..

The fourth outer class is the class that contains the main method. The main method should allow the user to select the input file from the default directory by using an object of the <sub>JFileChooser</sub> class. It should then populate an <sub>ArrayList</sub> of objects of type <sub>Polynomial</sub> as it reads in the lines of the file. As the polynomials are read in, they should also be displayed in the format provided by the <sub>toString</sub> method. Should the InvalidPolynomialSyntax exception be thrown, it should be caught and a JOptionPane message should be displayed containing the reason for the invalid syntax. The list of polynomials should be then checked to see whether it is in sorted order according to two orderings. The first check is the one that uses the <sub>compareTo</sub> method of the <sub>Polynomial</sub> class. We refer to this first ordering as the strong order. The second results from the use of a comparator. We refer to it as the weak order. It should display whether it fails to be sorted by either of both of the two orderings or if it is sorted according to both.

Inside the main class, a named lambda expession should be defined that implements the <sub>Comparator</sub> interface. Its <sub>compare</sub> method should consider only the exponents and not the coefficients in comparing the polynomials, much like how functions are categorized by Big-O.

As an example, consider the following list of polynomials:

4.0<em>x</em><sup>3</sup> + 2.5<em>x</em> + 8.0

5.0<em>x</em><sup>4</sup> + 5.0

4.5<em>x</em><sup>4</sup> + 5.7<em>x</em><sup>2</sup> + 8.6

This list fails to be sorted by the strong order that considers both the coefficients and exponents because the third polynomial is less than the second because of the coefficients on the <em>x</em><sup>4</sup> terms. The coefficient on that term in the second polynomial is 5.0, which is greater than 4.5, the coefficient on the corresponding term in the third polynomial.

They are sorted by the weak order that considers only the exponents, however. The third polynomial is greater than the second because the third has a <em>x</em><sup>2</sup> term and the second one does not.