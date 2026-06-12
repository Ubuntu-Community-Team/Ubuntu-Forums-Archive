---
title: "Jogl not working with Ubuntu 11.04"
date: 2011-06-10
forum: General Help
---

### Post by lads on 2011-06-10
Hello everyone,

I need to use jogl in some Eclipse stuff I'm working with. I've installed libjogl-java package with synaptic but am getting like these at Eclipse:

```
Exception in thread "AWT-EventQueue-0" java.lang.NoClassDefFoundError: com/sun/gluegen/runtime/DynamicLookupHelper

```

Hence I tried to install jogl manually, by copying the .jar and .so files into /jre/lib/ext. Even doing that I can't use jogl. For instance a simple program compiled at the command line is giving an exception like this:

```
Exception in thread "main" java.lang.UnsatisfiedLinkError: no jogl in java.library.path
```

Can anyone help? Thank you,

Luís

---

### Post by lads on 2011-06-13
Reading a suggestion at another forum I tried to run the jogl test program explicitly providing a path to the jars:

```
java Hello -Djava.library.path="/usr/lib/jvm/java-6-sun/jre/lib/ext"
```

The result is exactly the same, with the "UnsatisfiedLinkError" exception.

---

### Post by lads on 2011-06-13
Another thing I tried in the meanwhile: Ubuntu ships with OpenJDK, but it has several issues with some of the applications I use, hence installing Oracle's Java is one of the first things I do on a Ubuntu system. 

In the event of this problem being caused by a wrong reference to OpenJDK I manually installed jogl in that jre by copying the .jar and .so files into the jre/lib/ext directory. Unfortunately this hasn't solved the issue.

---

### Post by lads on 2011-06-23
Hello everyone,

I returned to this issue today. I created a new Java project in Eclipse with a very simple sample program that goes below. Eclipse is showing this error on the import line:

> Access restriction: The type GLCapabilities is not accessible due to restriction on required library /usr/lib/jvm/java-6-openjdk/jre/lib/ext/jogl-1.1.1+dak1.jar

I have no idea why Eclipse can't access this jar; it originally had reading permissions for everyone, and even after changing it to full permissions to everyone Eclipse keeps complaining. Stranger still is the fact that if I ask Eclispe to run the program it executes without any exception.

Any help apreciated. Thanks,

Luís

---------

```
import javax.media.opengl.GLCapabilities;

public class Hello{
	
	public static void main (String args[]) {
		try {
			System.loadLibrary("jogl");
			System.out.println(
					"Hello World! (The native libraries are installed.)"
			);
			GLCapabilities caps = new GLCapabilities();
			System.out.println(
					"Hello JOGL! (The jar appears to be available.)"
			);
		} catch (Exception e) {
			System.out.println(e);
		}
	}
}
```

---

