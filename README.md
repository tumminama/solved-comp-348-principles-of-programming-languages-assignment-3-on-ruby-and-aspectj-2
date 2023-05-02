Download Link: https://assignmentchef.com/product/solved-comp-348-principles-of-programming-languages-assignment-3-on-ruby-and-aspectj-2
<br>
<h1><a name="_Toc7294"></a>1          General Information</h1>

Date posted: Wednesday June 11<sup>th</sup>, 2020.

Date due: Thursday June 24<sup>th</sup>, 2020, by 23:59<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>.

Weight: 5% of the overall grade.

<h1><a name="_Toc7295"></a>2          Introduction</h1>

This assignment targets two programming paradigms: 1) Multi-Paradigm Programming with Ruby, 2) Aspect Oriented Programming with AspectJ.

<h1><a name="_Toc7296"></a>3          Ground rules</h1>

You are allowed to work on a team of 3 students at most (including yourself). Each team should designate a leader who will submit the assignment electronically. See Submission Notes for the details.

ONLY one copy of the assignment is to be submitted by the team leader. Upon submission, you must book an appointment with the marker team and demo the assignment. All members of the team must be present during the demo to receive the credit. Failure to do so may result in zero credit.

This is an assessment exercise. You may not seek any assistance from others while expecting to receive credit. You must work strictly within your team). Failure to do so will result in penalties or no credit.

<h1><a name="_Toc7297"></a>4          Your Assignment</h1>

Your assignment is given in two parts, as follows. 1) Multi-Paradigm Programming with Ruby, 2) Aspect Oriented Programming with AspectJ.

<h2><a name="_Toc7298"></a>4.1         Multi-Paradigm Programming with Ruby</h2>

This section consists of three parts that are related, but may be implemented independently.

Q 1. Classes in Ruby

De ne the following class hierarchy in Ruby

<ol>

 <li>Shape

  <ul>

   <li>the class constructors receives no parameter.</li>

   <li>id: a read-only integer id, automatically assigned to all shapes upon creating; rst object: 1, second object 2, and so on.</li>

   <li>method print(): prints the id and the name of the shape, the perimeter, and thearea. The name of the shape is the class name (i.e. Shape for this class). This method must dynamically read the class name at runtime. In child classes this method correctly prints the class name (without explicitly being implemented).</li>

   <li>method perimeter(): default method to be implemented by child classes; returningnil by default.</li>

   <li>method area(): default method to be implemented by child classes; returning nilby default.</li>

  </ul></li>

 <li>Circle

  <ul>

   <li>the class constructor receives the radius as the only parameter.</li>

   <li>method perimeter(): overridden, returns the perimeter of the circle.</li>

   <li>method area(): overridden, returns the area of the circle.</li>

  </ul></li>

 <li>Ellipse

  <ul>

   <li>the class constructor receives the semi-major and semi-minor axes: <em>a </em>and <em>b</em>, in an arbitrary order. The greater and the lesser values of the two parameters are to be assigned to the semi-major and the semi-minor axes, respectively.</li>

   <li>method perimeter(): not to be implemented.</li>

   <li>method area(): overridden, returns the area of the ellipse: <em>A </em>= <em>πab</em>.</li>

   <li>method eccentricity(): additional method that returns the linear eccentricity of</li>

  </ul></li>

</ol>

√

the ellipse: <em>c </em>= <em>a</em><sup>2 </sup>− <em>b</em><sup>2</sup>. In case of error, the method returns nil.

<ol start="4">

 <li>Rhombus

  <ul>

   <li>the class constructor receives the two diagonals.</li>

   <li>method perimeter(): overridden, returns the perimeter of the rhombus.</li>

   <li>method area(): overridden, returns the area of the rhombus.</li>

   <li>method inradius(): calculating the radius of a circle inscribed in the rhombus:</li>

  </ul></li>

</ol>

<em>r </em>= <em>p </em>· <em>q/</em>(2<sup>p</sup><em>p</em><sup>2 </sup>+ <em>q</em><sup>2</sup>), where <em>p,q </em>denote the diagonals. In case of error, the method returns nil.

Q 2. File / Text Processing

Write a Ruby program that reads text le that contains the shape information (see previous question). Every line in the text le consist of shape name and parameters to construct the shape. The program creates the shapes and calls the print method for each newly created shape and displays the result on the screen. In case the shape is an ellipse, the linear eccentricity is displayed in the following line. In case of a rhombus, the in-radius of the rhombus is displayed in the next line. In case of errors (i.e. having negative values for axes, radii, etc.), the object is created, however an error message is displayed on the console. As such, no further detail is to be displayed (i.e. no eccentricity is shown for an invalid ellipse).

An example given below:

Input:

shape

rhombus 10 20 circle 2 ellipse 2 4

shape

ellipse -1 4 rhombus 5 0

Output:

1: Shape, perimeter: undefined, area: undefined

2: Rhombus, perimeter: 44.72136, area: 100 in-radius: 8.16497

3: Circle, perimeter: 12.56637, area: 12.56637

4: Ellipse, perimeter: undefined, area: 25.13274 linear eccentricity: 3.46410

5: Shape, perimeter: undefined, area: undefined

Error: Invalid Ellipse

6: Ellipse, perimeter: undefined, area: undefined

7: Rhombus, perimeter: 10, area: 0

in-radius: 0

Q 3. Arrays and Hash

Extend the above program to display the statistics after processing the le. The statistics contain the total number of shapes per item, ordered alphabetically, followed by the total number of shapes . An example is given below.

Output:

Statistics:

Circle(s): 1

Ellipse(s): 2

Rhombus(es): 2

—

Shape(s): 7

Use hashes to implement the above structure in memory.

Note that rhombuses, circles, and ellipses are counted as shapes as well.

<h2><a name="_Toc7299"></a>4.2         Aspect Oriented Programming with AspectJ</h2>

Consider the code base and the driver code in sections 4.2.7 and 4.2.6. The code base provides an implementation for two classes: Circle and Rectangle, neither of which implement any interface. As a result, executing the driver code will produce the following output:

Error: Rectangle cannot be cast to class Shape

The task of this assignment is to make the output look like to the following, as instructed by the following sections.

The area of Rectangle(2, 1) is 2.0

The perimeter of Rectangle(-2, 8) is 0.0

The perimeter of Circle(-1) is 0.0

The area of Circle(2) is 12.56637

The last shape ID: 3

IMPORTANT: All changes must strictly be applied via aspects. Neither the code base

nor the driver code may be modi ed. All of the following sections may be implemented within a single aspect.

4.2.1          Introducing Shape Parent

Q 4. Using aspects, introduce Shape as a parent interface to both Circle and Rectangle.

To implement getName() method, the Circle object returns Circleand the Rectangle object returns Rectangle.

4.2.2          Overriding toString()

Q 5. Using aspects, override the toString() method in both Circle and Rectangle classes.

The toString() methods call the getName() in 4.2.1 and generates a string, representing the object.

Examples:

A Circle with a radius of 2 is represented as the string Circle(2).

A Rectangle with a width of 2 and a height of 1 is represented as Rectangle(2, 1).

4.2.3           Implementing Circle.getArea()

Q 6. The logic for calculating the area of the circle has not been implemented (as it currently throws a RuntimeException). Using aspects, implement it.

4.2.4          Handling Negative Values

Q 7. Using aspects, make sure passing a negative value to a radius of a Circle or to either width or height of a Rectangle results in 0 for the values of the shape’s area and perimeter.

4.2.5          Introducing Shape IDs

We want to generate a unique ID for every shape that is created. The shape IDs start at 0 and is incremented automatically upon creating of every new shape. To do so, a private static counter may be implemented in an aspect that is incremented upon calling the constructors of Circle and Rectangle.

Q 8. Using aspects, introduce Identifiable as a second parent interface to both Circle and Rectangle; and implement the getId() method in both classes.

4.2.6       Driver

public class Main {

public static void main(String[] args) {

try { Shape s; s = (Shape) new Rectangle(2, 1);

System.out.println(“The area of ” + s + ” is ” + s.getArea()); s = (Shape) new Rectangle(-2, 8);

System.out.println(“The perimeter of ” + s


” is ” + s.getPerimeter());

s = (Shape) new Circle(-1);

System.out.println(“The perimeter of ” + s


” is ” + s.getPerimeter());

s = (Shape) new Circle(2);

System.out.println(“The area of ” + s + ” is ” + s.getArea());

Identifiable i = (Identifiable)s;

if(i != null) {

System.out.println(“The last shape ID: ” + i.getId());

} }

catch(Exception e) {

System.out.println(“Error: ” + e.getMessage());

}

}

}

4.2.7        Code Base

public interface Identifiable {

int getId();

}

public interface Shape { String getName(); double getPerimeter();

double getArea();

}

public class Rectangle { private double width, height;

public Rectangle(double width, double height) { this.width = width;

this.height = height;

}

public double getPerimeter() {

return 2 * (this.width + this.height);

}

public double getArea() {

return this.width * this.height;

} }

public class Circle { private double radius;

public Circle(double radius) {

this.radius = radius;

}

public double getPerimeter() {

return 2 * Math.PI * this.radius;

}

public double getArea() {

throw new RuntimeException(“Oops, I’ve forgotten my math! :(“);


