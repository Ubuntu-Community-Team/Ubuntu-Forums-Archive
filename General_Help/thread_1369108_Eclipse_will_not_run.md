---
title: "Eclipse will not run"
date: 2009-12-31
forum: General Help
---

### Post by eewoz on 2009-12-31
I am trying to install Eclipse on an Ubuntu 9.10 machine. I installed Eclipse with the Synaptic Package Manager. When I run Eclipse I get an error window saying that an error has occurred and that I should see the log file. The contents of the log file that the error message refers to are ```
!SESSION Thu Dec 31 09:07:32 EST 2009 ------------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2009-12-31 09:07:32.088
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.ClassNotFoundException: org.eclipse.core.runtime.adaptor.EclipseStarter
    at java.net.URLClassLoader$1.run(URLClassLoader.java:200)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:556)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

```Does anyone have any suggestions how to correct this problem?

Thanks.

---

### Post by pavel989 on 2009-12-31
definitely dont use synaptic for eclipse, i am ye to hear good results. just download the tar.gz of their website and untar it somewhere, then u can make a link in the apps-programming menu

---

### Post by eewoz on 2010-01-01
Boy that was pretty easy!  Thanks for the help.  Eclipse now seems to be running.  How do I make a link in the apps-programming menu?

---

### Post by eewoz on 2010-01-01
I take that back.  It is not completely running correctly.  I am trying to go through a tutorial that shows how to make a C++ program.  In going through the process I get to a window where none of the buttons (NEXT, CANCEL, etc) will not work.  The only way to cancel the window is to use the close button in the upper right hand corner of the window.  What can be going on now?

---

### Post by eewoz on 2010-01-01
I did one other thing that may give a clue as to what is going on.  I installed Eclipse using the Ubuntu Software Center.  With this version I had to manually load the CDT plugin.  In order to do that I had to open Eclipse as root.  I can open this version of Eclipse as a normal user but it does not allow me to save any of the files that I generate.  I have to run eclipse as root in order to make Eclipse fully functional.  i guess that is OK but something is not right.

---

### Post by eewoz on 2010-01-01
I did some work with Eclipse as root and then tried once again as a normal user and all seems well.  go figure...

---

### Post by airbag on 2010-01-02
nice

---

### Post by LumbeeNDN on 2010-01-11
...I'm having some of the same problems with Eclipse...specifically my finish button is not working. I know this is a stupid question, but how do I run eclipse as root? Sudo <then some command>???

---

