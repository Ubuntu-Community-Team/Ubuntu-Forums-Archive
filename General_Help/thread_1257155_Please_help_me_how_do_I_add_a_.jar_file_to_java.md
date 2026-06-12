---
title: "Please help me: how do I add a .jar file to java????"
date: 2009-09-03
forum: General Help
---

### Post by smokyink on 2009-09-03
OK here is my problem:
I study in the University of Oslo (Informatics-1st semester)
We use Java...but I have to add a .jar package(easyio.jar :() to the Java 6,
so I can compile the programs I write and all the exercises and stuff...


In the instructions for windows it says that I have to paste the file in:

C:\Program Files\Java\jdk1.6.0_11\jre\lib\ext\
 
I have tried to simply add the package to:

/usr/lib/jvm/java-6-sun-1.6.0.14/ext

but when I compile a program which uses it ( import easyio.*)
the complier says that the file does not exist:confused:?????

ex241.java:1: package easyIO does not exist
import easyIO.*;
^
Please please help I'm struggling to find a solution since about 3 hours ](*,)
:(  #-o

If you need any info just ask I'm still here...](*,)

---

### Post by smokyink on 2009-09-03
By the way I use the console to compile and gedit to write the program...

---

### Post by Penguin Guy on 2009-09-03
For me it is at [COLOR="Green"]/usr/lib/jvm/java-6-openjdk/jre/lib/ext[/COLOR]. Open nautilus, start at /, and look step-by-step for the most likely folder.

---

### Post by smokyink on 2009-09-03
I dont have 
 [COLOR=Green]/usr/lib/jvm/java-6-openjdk

in   [/COLOR][COLOR=Green]/usr/lib/jvm/ there is only :
java-1.5.0-gcj-4.3-1.5.0.0
  java-6-sun 
 java-6-sun-1.6.0.14 
 java-gcj


[/COLOR]

---

### Post by Chronon on 2009-09-03
It seems you should try either **/usr/lib/jvm/java-6-sun/jre/lib/ext** or **/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext**.

---

### Post by Penguin Guy on 2009-09-03
> **smokyink said:**
> I dont have 
 [COLOR=Green]/usr/lib/jvm/java-6-openjdk

in   [/COLOR][COLOR=Green]/usr/lib/jvm/ there is only :
java-1.5.0-gcj-4.3-1.5.0.0
  java-6-sun 
 java-6-sun-1.6.0.14 
 java-gcj

[/COLOR]


Check in all of them, I would probably do it in this order:
```
java-6-sun 
java-gcj
[S]java-6-sun-1.6.0.14[/S]
java-1.5.0-gcj-4.3-1.5.0.0
```

---

### Post by smokyink on 2009-09-03
/usr/lib/jvm/java-1.5.0-gcj-4.3-1.5.0.0/jre/lib ---pasted easyio.jar in anyway....doesn't change things

/usr/lib/jvm/java-6-sun/lib  ---there isn't a ext folder...pasted easyin.jar there ....no effect

/usr/lib/jvm/java-gcj/jre/lib ---there isn't a ext folder..pasted easyin.jar there...no effect

/usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext ---pasted file ....no effect

Any Ideas???

---

### Post by smokyink on 2009-09-03
Sorry there is a /usr/lib/jvm/java-6-sun/jre/lib/ext 
just pasted the file and no effect

---

### Post by Penguin Guy on 2009-09-03
Can you post your code here?
What error did the compiler give you?

---

### Post by smokyink on 2009-09-03
Jupp:

ex241.java:1: package easyIO does not exist
import easyIO.*;
^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
     ^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
                      ^
3 errors

---

### Post by smokyink on 2009-09-03
And the code is:

import easyIO.*;

 class ex241
  {
   public static void main(String[] args)
    {
     Out skjerm = new Out();
     skjerm.outln('A');
     skjerm.outln("Canis familiaris betyr hund");
     skjerm.outln(15);
     skjerm.outln(3.1415, 2);  //Bruk to desimaler
    }
  }

Error
ex241.java:1: package easyIO does not exist
import easyIO.*;
^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
     ^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
                      ^
3 errors

---

### Post by smokyink on 2009-09-03
installed javacc still no go

If it would help I have:
sun-java6-jre
sun-java6-jdk
eclipse
emacs
and other java related packages installed with synaptic

---

### Post by Penguin Guy on 2009-09-03
> import easyIO.*;
Make sure that you have a link/copy of easyIO.jar in all the folders mentioned before. Make sure you are using the **exact** name of the file, it must be the correct case and it's probably best to miss out the wildcard (*) and use the extension (.jar) instead. So your command would be something like [COLOR="Green"]import easyio.jar;[/COLOR]

---

### Post by Penguin Guy on 2009-09-03
> **smokyink said:**
> And the code is:

import easyIO.*;

 class ex241
  {
   public static void main(String[] args)
    {
     Out skjerm = new Out();
     skjerm.outln('A');
     skjerm.outln("Canis familiaris betyr hund");
     skjerm.outln(15);
     skjerm.outln(3.1415, 2);  //Bruk to desimaler
    }
  }

Error
ex241.java:1: package easyIO does not exist
import easyIO.*;
^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
     ^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
                      ^
3 errors

Looking at that code doesn't look very nice, using the [PHP] tag for code and the ```
 tag for compiler output makes things look nicer. :)

> **smokyink said:**
> And the code is:

**[Java]**
[PHP]
import easyIO.*;

 class ex241
  {
   public static void main(String[] args)
    {
     Out skjerm = new Out();
     skjerm.outln('A');
     skjerm.outln("Canis familiaris betyr hund");
     skjerm.outln(15);
     skjerm.outln(3.1415, 2);  //Bruk to desimaler
    }
  }
[/PHP]

**[Compiler Output]**
[CODE]
Error
ex241.java:1: package easyIO does not exist
import easyIO.*;
^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
     ^
ex241.java:7: cannot find symbol
symbol  : class Out
location: class ex241
     Out skjerm = new Out();
                      ^
3 errors

```


---

### Post by smokyink on 2009-09-03
I just tried it with:
import easyio.*;
import easyIO.*;
import easyio.jar;
import easyIO.jar;
import Easyio.*;
import EasyIO.*;

the compiler gave me the same error just different name of package...

Any ideas??

---

### Post by smokyink on 2009-09-03
OK thanks will do :)

---

### Post by smokyink on 2009-09-03
So maybe this way it wont work...
Does anybody know any other way??
So I can include the jar into my programs....or to Java itself???

---

### Post by falconindy on 2009-09-03
Java defines a variable "classpath" for specifying user created libraries and jar files. You'll need to do something like:
```
java -classpath /path/to/jar package.class
```[source]("http://en.wikipedia.org/wiki/Classpath_%28Java%29#Setting_the_path_of_a_Jar_file")

---

### Post by Chronon on 2009-09-03
Are you able to import other packages in those directories?  Maybe something about your classpath is messed up?

---

### Post by Penguin Guy on 2009-09-03
**[Java]**
[PHP]
import package-path.*;             // Makes all classes in package visible.
import package-path.class;         // Makes only class visible.
import static package-path.*;      // Makes all static variables in all classes in package visible.
import static package-path.class;  // Makes all static variables in class visible.
[/PHP]

If I understand this correctly, the command you should be using is: [COLOR="Green"]import easyio.jar.*;[/COLOR]

---

### Post by smokyink on 2009-09-04
I just tried it and it doesn't work..
But the program is shown in my book so I'm pretty sure that there shouldn't be a syntax error in it.

---

### Post by smokyink on 2009-09-04
[falconindy]("http://ubuntuforums.org/member.php?u=863375")


I tried with this command:
code:

```
java -classpath /home/username/Desktop/class.easyio.jar

```But when I press enter the terminal just shows me the usage
and syntax of the java command with all options.
So I'm probably doing something wrong.

Maybe I misunderstood the way of use of
the command?And I'm using it wrong?:confused:


Chronon
How do I find out weather my classpath is messed up??

I have also tried to issue the classpath command as a super(with sudo) stil no go. :(

Any ideas?? Anyone

Could someone give me an example of how he/she would write it?

---

### Post by smokyink on 2009-09-04
YEEESSS finaly I got it!!!!!\\:D/

I compile with

```
......@......:~/Desktop/i1000$ javac ex1.java -cp /home/user/Desktop/i1000/lib/easyio.jar
```Source:[http://ubuntuforums.org/showthread.php?p=7895527#post7895527](http://ubuntuforums.org/showthread.php?p=7895527#post7895527)


Here is how I solved my problem:

on my desktop I have:
```
Desktop/i1000

```I created
```
Desktop/i1000/lib
```containing package easyIO.jar

my program is in Desktop/i1000

Also I extracted easyIO.jar 
and copied the easyIO folder with its contens as such:
```
Desktop/i1000/easyIO
```So when I run the program it finds the easyIO folder with the custom classes that It needs.

:biggrin::popcorn::KS

Thanks for all the help
:D8-)=D>

---

