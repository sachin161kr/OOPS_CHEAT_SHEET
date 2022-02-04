# OOPS_CHEAT_SHEET

OOPS CONCEPT CHEAT SHEET

-------------------------------

Classes and Objects :-

1. There can be only one PUBLIC class in any .java file whose name must match with the name of that .java file.

2. We can create multiple number of classes in a single .java file.

3. A class is just a blue print of an object i.e. it is not an actual object but we can create multiple objects with the help of this class.

4. Class does not take up space in the memory, Objects made from them do.

5. We use NEW keyword to create objects.

6. We can use DOT(.) operator to access the properties of the created object.

---------------------------------

Methods/Functions (Compiled Time Polymorphism):-

*Polymorphism signifies many forms.

1. Every objects has some PROPERTIES as well as BEHAVIOUR defined in the class.

class Person {
    String name;
    int age;

    void walk()
    {
        System.out.println(name+" is walking.");
    }

    void eat()
    {
        System.out.println(name+" is eating.");
    }
}

Here, Person is the Class in which name and age are the properties and walk , eat are the behaviours.

2. Method/Funtion Overloading - name of the method/function remains same but differs in arguments.

 void walk(int steps)
    {
        System.out.println(name + " has walked "+steps+" steps");
    }

--------------------------------------------

Constructors And Static Keyword :-

1. There's always a default constructor which need not to be defined by the user. Also one can create a constructor of your own.

class Person {
    String name;
    int age;

    public Person()
    {
        System.out.println("Constructor is called");
    }
}

Here, Person() is the default constructor which is not necessory to be called. It is called automatically.

2. STATIC keyword is used in java so that there is no need to make an object of the class first to use it's functions/Methods.

class Person {
    String name;
    int age;

    static int count = 0;

    public Person()
    {
        count++;
        System.out.println("Constructor is called");
    }
}

public class Solution {
    public static void main(String[] args)
    {
        
        System.out.println(Person.count);

    }
}

In the above code Person.count is used without creating any object of the Person class as we have used static keyword while defining int count.

STATIC is used to define properties of a CLASS and not the properties of an OBJECT.

3. Contructor Overloading - Same as Method/Function Overloading

class Person {
    String name;
    int age;

    public Person()
    {
        System.out.println("Default constructor is called");
    }

    public Person(int myAge,String myName)
    {
        name = myName;
        age = myAge;

        System.out.println("Overloaded constructor is called");
    }
}

In the above code Person() is default Constructor and 
Person(int myAge ,String myName) is user defined.


3. THIS keyword - THIS keyword can be used to call one constructor from another constructor.

class Person {
    String name;
    int age;

    public Person()
    {
        System.out.println("Default constructor is called");
    }

    public Person(int myAge,String myName)
    {
        this();
        name = myName;
        age = myAge;

        System.out.println("Overloaded constructor is called");
    }
}

In the above code, Person() will be called twice and 
Person(int myAge, String myName) will be called once same as before.


THIS keyword can also be used to access the variables of the class shown below -

class Person {
    String name;
    int age;

    public Person(int age,String name)
    {
        this.age = age;
        this.name = name;
    }
}

-----------------------------------------------------

Inheritance :-

When a class(child class) inherits the properties as well as behaviour of other class(parent class) is termed as inheritance.

*In JAVA extends keyword is used to support inhertance.
*In JAVA every class has an universal parent which is called OBJECT class.

class Dev extends Person{

    public Dev(int age, String name) {
        super(age, name);
    }
}

class Person {
    String name;
    int age;

    public Person(int age , String name)
    {
        this.name = name;
        this.age = age;
    }

    public void walk()
    {
        System.out.println(name+" is walking");
    }
}

In the above code Dev Class inheits the properties and methods of the Person Class.

Super keyword is used to call the constructor of the Parent Class from the Child Class.

* THIS is used to access the properties and methods of the current class where as SUPER is used to access the properties and methods of the Parent class.

** Below is an example of RUN-TIME Polymorphism

class Dev extends Person{

    public Dev(int age, String name) {
        super(age, name);
    }

    public void walk()
    {
        System.out.println(name + " is walking");
    }
}

class Person {
    String name;
    int age;

    public Person(int age , String name)
    {
        this.name = name;
        this.age = age;
    }

    public void walk()
    {
        System.out.println(name+" is walking");
    }
    
}

*In the above code there are two walk() methods/function which is determined in run time which walk() is called and then it's linked. Previously in Compiled time polymorphism we are explicitly defining which walk() is to be called.

Firstly the compiler will find the walk() inside the class from which it is called then if not found will proceed to the super class.

------------------------------------------------------

Encapsulation :-

1. Used mainly for data hiding and data protection.
2. Encapsulation can be achieved with the help of Packages and Access Modifiers.

* Packages -> Packages are like folders inside which we can create multiple java classes.

*Access Modifiers -> There are 3 access Modifiers used in JAVA. Note - Default access is not explicitly written.

Default - Any Property or Behaviour marked as default can be accessed only by the class and it's childeren and not by the super classes also not visible from any other package. 

PUBLIC - Any Property or Behaviour marked as public can be accessed by any class from anywhere even if the class is present in another PACKAGE.

PRIVATE -  Any Property or Behaviour marked as private can be accessed only by the class in which it is defined and not else where.

PROTECTED - Any Property or Behaviour marked as protected is a public Property or Behaviour only for it's children classes i.e. behaves exactly like public access but only for childen classes.

*Concept Of getter and setter functions.
-> If a property is private it cannot be accessed outside of the class so we can create a public getter and setter functions to access it outside of the class and can define who can access then inside these getter setter methods/functions.

public class Solution {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
        Laptop lp = new Laptop();

        lp.setPrice(500);

        lp.getPrice();
    }
}

class Laptop {
    private int price;

    public void setPrice(int price)
    {
        this.price = price;
    }

    public void getPrice()
    {
        System.out.println(price);
    }
} 

Above code implements getter and setter functions for private field price.

-----------------------------------------------------

Abstraction :-

When a user is only interested in the work done and not in the working and internal complexities of the code.

Abstraction can be achieved by abstract keyword and interfaces.

Abstraction concept is used to reduce the complexities in the system.

-> Abstract keyboard when added before any class signifies that now object can be created from that class and
Abstract keyboard when added before any method/function signifies that you dont have to define the method/function body at that particular instance as shown in the code below.

class Audi extends Car{ 
    @Override
    void start() {
        System.out.println("Audi is starting.");
    }
}

class BMW extends Car{
    @Override
    void start() {
        System.out.println("BMW is starting");
    }
}

abstract class Car{
    abstract void start();
}

*An abstract function/method must be contained inside a abstract class.


-> Abstraction using interfaces

Interfaces are special abstract classes.

Functions/Methods declared inside interfaces are by default public and abstract where as in an abstract class we can create a non-abstract method/function inside it.

Interfaces provide true abstraction.

public class Solution implements Car {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
    }

    @Override
    public void start() {
        System.out.println("Car is starting");
    }
}

interface Car{
    void start();
}

*JAVA does not allow one class to have multiple parents. There can be multi-level parents but not multiple therefore we can use multiple interfaces which is shown in below code.

public class Solution implements Car,Person {
    public static void main(String[] args)
    {
        Scanner sc = new Scanner(System.in);
    }

    @Override
    public void start() {
        System.out.println("Car is starting");
    }

    @Override
    public void walk() {
        System.out.println("Car is Walking");
    }
}

interface Car{
    void start();
}

interface Person{
    void walk();
}

----------------------------------------------------------

video reference -> https://youtu.be/a199KZGMNxk

