---
title: "Installing Eclipse/Java on Ubuntu"
date: 2012-01-04
forum: General Help
---

### Post by Attempt#2 on 2012-01-04
I have installed Eclipse but I can't run Java code. I get lots of different errors including:

Unsupported major.minor version 51.0

OR 

in the IDE itself I get errors like:

"Implicit super constructor Object() is undefined for default constructor. Must define an explicit constructor."

I have Eclispe, IcedTea Java 6 Web Start (whatever that is) and OpenJDK Java 6 Runtime installed.

This code runs on multiple Windows machines correctly.

I have tried to run the code via the terminal but I don't know how to edit .bashrc correctly so I can use javac. I don't know what path I am meant to set.

---

### Post by Catharsis on 2012-01-04
I'm not super familiar with Eclipse -- I know it does some weird things, like it has its own compiler, etc.

First, make sure you have everything installed:
```
sudo apt-get install openjdk-6-jre icedtea6-plugin openjdk-6-jdk
```

And check that it's set up correctly:
```
java -version
```
```
javac -version
```

It should look something like
```
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
```
and
```
javac 1.6.0_23
```
respectively.

You can also find the official Ubuntu java documentation at
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Attempt#2 on 2012-01-05
> **Catharsis said:**
> I'm not super familiar with Eclipse -- I know it does some weird things, like it has its own compiler, etc.

First, make sure you have everything installed:
```
sudo apt-get install openjdk-6-jre icedtea6-plugin openjdk-6-jdk
```

And check that it's set up correctly:
```
java -version
```
```
javac -version
```

It should look something like
```
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
```
and
```
javac 1.6.0_23
```
respectively.

You can also find the official Ubuntu java documentation at
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Thanks for the response - appreciate it. :)

```
sudo apt-get install openjdk-6-jre icedtea6-plugin openjdk-6-jdk
```

Result:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-6-jdk is already the newest version.
openjdk-6-jre is already the newest version.
openjdk-6-jre set to manually installed.
icedtea6-plugin is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```
java -version
```

Result:

```
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10)
OpenJDK Server VM (build 20.0-b11, mixed mode)

```

```
javac -version
```

Result:

```
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.6-jdk
 * gcj-4.5-jdk
 * openjdk-7-jdk
Try: sudo apt-get install <selected package>

```

I assumed javac isn't working because I haven't edited .bashrc correctly. I have googled but am not exactly sure what to put in .bashrc.

I tried following this: [http://introcs.cs.princeton.edu/java/15inout/linux-cmd.html](http://introcs.cs.princeton.edu/java/15inout/linux-cmd.html)

but couldn't seem to make it work as I wasn't sure of the location of my javac and java executables.

---

### Post by Catharsis on 2012-01-05
I'm pretty sure you can just run
```
sudo update-alternatives --config javac
```
and choose the number with 'openjdk-6-jdk'.

If that doesn't work you might try reinstalling it
```
sudo apt-get install --reinstall openjdk-6-jdk
```

You might also want to remove openjdk-7-jdk, since it might be conflicting with things
```
sudo apt-get remove openjdk-7-jdk
```
(If you think you have other openjdk-7 stuff, you can remove all of them with ```
sudo apt-get remove openjdk-7-*
```)

---

### Post by Attempt#2 on 2012-01-05
> **Catharsis said:**
> I'm pretty sure you can just run
```
sudo update-alternatives --config javac
```
and choose the number with 'openjdk-6-jdk'.

If that doesn't work you might try reinstalling it
```
sudo apt-get install --reinstall openjdk-6-jdk
```

You might also want to remove openjdk-7-jdk, since it might be conflicting with things
```
sudo apt-get remove openjdk-7-jdk
```
(If you think you have other openjdk-7 stuff, you can remove all of them with ```
sudo apt-get remove openjdk-7-*
```)

The
```
sudo update-alternatives --config javac
```
didn't work. I reinstalled openjdk-6-jdk and removed all openjdk-7 related stuff.

I tried creating a new project and running code and it worked!

Importing old projects didn't work - still produced the major minor version error. I deleted the created .class files in my bin folder and changed under the project settings under Java Build Path -> libraries to JAVASE-1.7 to JAVASE-1.6 (java-6-openjdk) and everything works!

Thank you!

---

### Post by Catharsis on 2012-01-05
Awesome. Sounds like you might have made the old files with version 7, in which case you'd have to install openjdk-7-{jdk,jre} and remove the 6 to run those compiled with version 7.

The major minor error is just building with version 6 and running with version 7 or vice versa and the resulting incompatibilities.

---

