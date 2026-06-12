---
title: "how to run java programs"
date: 2010-01-13
forum: General Help
---

### Post by malikge on 2010-01-13
Hello.
I want to know that how to run java programs in ubuntu.
Which is the best compiler for java, and how to compile the program file...
Thanks.

---

### Post by khelben1979 on 2010-01-13
Java is provided by Sun Microsystems and you should find it if you search in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager").

Otherwise you have different java packages [here]("http://java.com/en/download/manual.jsp") directly from Sun Microsystems homepage.

Once java is installed in the system you just start them like ordinary programs a.f.a.i.k.

---

### Post by lykeion on 2010-01-13
You can compile Java source code from the command line.
This example is the most basic of all Java programs, the famous HelloWorld example.

Source code: HelloWorld.java
```
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello world");
    }
}
```

Compile it like this using javac in Sun's JDK:
```
javac HelloWorld.java
```

And run the program with
```
java HelloWorld
```

As for the question about the best compiler for java, I leave that unanswered because it all depends on the type of application and what you need. You can google for other compilers like jikes, kaffe, gcj and find out the differences yourself. For me Sun's javac compiler suits 99% of all my needs.

---

### Post by cavh on 2010-01-13
See also [http://java.sun.com/new2java/]("http://java.sun.com/new2java/")

---

### Post by philcamlin on 2010-01-13
> **cavh said:**
> See also [http://java.sun.com/new2java/](http://java.sun.com/new2java/)
thats a good place so start

---

### Post by Kungalm on 2010-01-13
My tip of the day is: as soon as you have java up and running. go to [www.eclipse.org]("http://www.eclipse.org") and install their developer gui(IDE). It takes care of comiling and running the program for you, and you get a lot of other features as well. They have tons of "how-to's" available as well. 

Cheers,

---

