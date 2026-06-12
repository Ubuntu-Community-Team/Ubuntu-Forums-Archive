---
title: "java help......"
date: 2010-06-09
forum: General Help
---

### Post by meomike2000 on 2010-06-09
not sure this is in the right place but here we go....

i have downloaded and installed java-6-sun on my machine, version 9.10 and had it working. i could create and compile java classes, using javac. Then i could call the class via java classname and it would run. but for some reason now i can not get none of my classes to run not even a simple little HELLO World, i get this error message.

> 
Exception in thread "main" java.lang.NoClassDefFoundError: FirstProgram
Caused by: java.lang.ClassNotFoundException: FirstProgram
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: FirstProgram.  Program will exit.

i also have the same setup on my laptop, version 8.04 and all still works fine there.

i have installed tomcat on both machines and i can serve simple servlets from either machine

here is the output of java -version
same on both machines....
> 
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Client VM (build 16.3-b01, mixed mode, sharing)


any help would be great, thanks in advance mike.....

---

### Post by Queue29 on 2010-06-09
Are you sure you compiled the program first?
Are you sure you are in the correct directory (the one with the .class files) when you run java [...] ?

---

### Post by meomike2000 on 2010-06-09
i was using these classes before.....

then i set up tomcat via this how-to 
[http://ubuntuforums.org/showthread.php?p=226828]("http://ubuntuforums.org/showthread.php?p=226828")

got tomcat serving some simple servlets....

trying to learn serialization, typed this from the book i am learning from
```

import java.io.*;
import java.util.*;

public class StudentList implements Serializable {	
	
	//Vector holding out students
	Vector list = new Vector(6);
	
	//default constructor
	public StudentList() {
	}
	
	public void addStudent(String value) {
		//add a string representing a student name
		if ( value != null ) {
			list.addElement(value);
		}
	}
	
	public void listStudents() {
		//iterate over list vector, printint all Strings
		for ( int x = 0; x < list.size(); x++ ) {
			System.out.println("Student " + x + " : " + (String)list.elementAt(x));
		}
	}
}

``` 
and
```

import java.io.*;

public class StudentListApplication {
	//Default Constructor
	public StudentListApplication() {
	
	}
	
	//adds student names to list
	public void buildStudentList(StudentList value) {
		value.addStudent("Bob Robinson");
		value.addStudent("Steve Bobinson");
		value.addStudent("Rob Stevinson");
		value.addStudent("Todd Thompson");
		value.addStudent("Tom Toddson");
		value.addStudent("Rob Bobinson");
	}
	
	// Stores the Serializable StudentList to the file "file.dat"
	public void putStudentList(StudentList value) {
		try {
			//create the ObjectOutputStream passing it the FileOutputStream 
			//object that points to our persistent storage.
			ObjectOutputStream os = new ObjectOutputStream( new FileOutputStream("file.dat"));
			//write the StudentList to the ObjectOutputStream
			os.writeObject(value);
			os.flush();
			os.close();
		}
		catch (IOException e) {
			System.err.println(e.getMessage());
		}
	}
	
	public StudentList getStudentList() {
		StudentList list = null;
		try {
			//create the ObjectInputStream passing it the FileInputStream object that points
			//to out persistent storage.
			ObjectInputStream is = new ObjectInputStream( new FileInputStream("file.dat"));
			//Read the stored object and downcast it back to a StudentList
			list = (StudentList)is.readObject();
			is.close();
		}
		catch (IOException e) {
			System.err.println(e.getMessage());
		}
		catch (ClassNotFoundException ce) {
			System.err.println(ce.getMessage());
		}
		return list;
	}
	
	public void invoke() {
	
		StudentList list = new StudentList();
		
		buildStudentList(list);
		
		System.out.println("Before being serialized.");
		list.listStudents();
		putStudentList(list);
		
		System.out.println("After being read back in.");
		//get the StudentList and print it out
		StudentList inList = getStudentList();
		if ( inList != null ) {
			inList.listStudents();
		}
		else {
			System.err.println("readObject failed.");
		}
		try {
			System.out.println("\n Press enter to quit.");
			System.in.read();
		}
		catch (Exception e) {
			System.err.println(e.getMessage());
		}
	}
	
	public static void main(String[] args) {
		StudentListApplication studentListApplication = new StudentListApplication();
		studentListApplication.invoke();
	}
}

```

compiled them but they would only give me the same errors as i posted above, moved them to my laptop and runs just fine....
so i know something happened on this machine but can not figure it out....

thanks mike....

i also set tomcat up on the laptop via the same how to.....

---

### Post by meomike2000 on 2010-06-09
ok, i found my problem, when setting up tomcat via the above mentioned how-to i made a change to my .bashrc file, and did not omit the changes

thanks to any that tried to help and hope this may help others....

ps i thought that i had omited the changes but when u use su and make a change to .bashrc it dont change the same file as when u use sudo, lesson learned......
su changes the user to root where sudo only give the current user superuser privileges......

---

