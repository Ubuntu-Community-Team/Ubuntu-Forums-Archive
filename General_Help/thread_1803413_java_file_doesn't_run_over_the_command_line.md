---
title: "java file doesn't run over the command line"
date: 2011-07-13
forum: General Help
---

### Post by Bortecin on 2011-07-13
Hello I'm newbie to Linux,

I have bound over the command line all for my work related jar files to my CLASSPATH 
and can now execute the command  ***javac HelloRDFWorld.java*** and there comes no
error messages. I assume javac command can be executed without any problems:
[B]/workspace/JenaTutorial/src/main/java/tutorial$ javac HelloRDFWorld.java
/workspace/JenaTutorial/src/main/java/tutorial$ [/B]


But there are still one problem; although my java file can run in Eclipse environment without any problems it does not run over the command line:  
  

**//workspace/JenaTutorial/src/main/java/tutorial$ java HelloRDFWorld.java **
Exception in thread "main" java.lang.NoClassDefFoundError: HelloRDFWorld/java
Caused by: java.lang.ClassNotFoundException: HelloRDFWorld.java
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
**Could not find the main class: HelloRDFWorld.java. Program will exit.**



What is here wrong? Thanks in advance!

---

### Post by anieruddha on 2011-07-13
Its a Java Issue not ubuntu 

Do following checks :
1. HelloRDFWorld.java file contain class HelloRDFWorld 
(check exact case match)

2. check main method is in class HelloRDFWorld and its signature is correct.

you can post code, if problem doesnt solve.

---

### Post by Bortecin on 2011-07-13
Thanks.

By the way, my Java version:

$ java -version
java version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.8) (6b20-1.9.8-0ubuntu1~10.04.1)
OpenJDK 64-Bit Server VM (build 19.0-b09, mixed mode)

**And my code: It runs in Eclipse enviroment but not over the command line with the command **java HelloRDFWorld
(the class produced by javac HelloRDFWorld.class is already in the current directory) 

package tutorial;

import com.hp.hpl.jena.datatypes.xsd.XSDDatatype;
import com.hp.hpl.jena.rdf.model.Model;
import com.hp.hpl.jena.rdf.model.ModelFactory;
import com.hp.hpl.jena.rdf.model.Resource;
import com.hp.hpl.jena.rdf.model.Property;


public class HelloRDFWorld {

    /**
     * @param args
     */
    public static void main(String[] args) {
        // TODO Auto-generated method stub
        Model m = ModelFactory.createDefaultModel();
        String NS = "http://example.com/test/";
        
        Resource r = m.createResource( NS + "r" );
        Property p = m.createProperty( NS + "p");
        
        r.addProperty(p, "hello world", XSDDatatype.XSDstring);
        
        m.write(System.out, "Turtle");
        

    }

}

---

### Post by adit on 2011-07-13
To compile:
I assume you have already compiled HelloRDFWorld.java.  If not type
```
javac HelloRDFWorld.java
```
The above code will produce HelloRDFWorld.class in the same directory.  

To run:
```
java HelloRDFWorld
```
Note: I have NOT typed any extension like HelloRDFWorld.class or HelloRDFWorld.java.
The javac command requires extension.  The java command does not need extension.

---

