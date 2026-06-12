---
title: "Eclipse Galileo (3.5) on Ubuntu Jaunty (9.04)"
date: 2009-08-30
forum: General Help
---

### Post by LzBy1 on 2009-08-30
I followed the following instructions (link below) for installing Eclipse 3.5 on Jaunty. Everything went well, however on launching eclipse, all I got was the eclipse splash screen. The application never opened, suggestions?

[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/](http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/)

Note: Eclipse 3.2 is available in the repositories, however, at least 3.3 is needed for Google's Web Toolkit.

---

### Post by uylug on 2009-08-30
What happens if you run it from the console?

This command should work

```
eclipse
```

---

### Post by LzBy1 on 2009-08-30
lol, same results. I get the splash screen then nothing else. I tried downloading the archive from the Eclipse website, extracted and ran from the desktop, I also got the same results.

---

### Post by uylug on 2009-08-30
Yeah but... no console output? Any errors or something?

---

### Post by LzBy1 on 2009-08-30
I reinstalling following the instruction once again, I actually installed everything to /bin/... instead of ~/bin/... that may have something to do with it.

Thank for the help, I'll let you know how it goes.

---

### Post by LzBy1 on 2009-08-30
I reinstalled, copied and pasted the code exactly, this time installing to the appropriate directory, however, when I try to start Eclipse via the terminal, I get an error that says it's not installed (this didn't happen with the other directory).

Also, when I manually start the application from it's directory I get an error message that points me to a log file. (This occurs a good 5 minutes after I close the frozen slash screen.) 

The log file from /home/user/workspace/.metadata/.log is listed below.

```
!SESSION 2009-08-30 18:23:20.798 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.3
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2009-08-30 18:23:23.452
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-30 18:23:23.452
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-30 18:23:23.452
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-08-30 18:23:23.452
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2009-08-30 18:26:34.650
```

A quick summery of what happened when I ran Eclipse.

1)Splash Screen Opens (nothing else happens).
2)I close the Splash Screen.
3)Receive error message pointing towards log file.

---

### Post by LzBy1 on 2009-08-30
No luck yet, any suggestions? Has anyone else been able to use Eclipse 3.5 on Ubuntu?

---

### Post by LzBy1 on 2009-08-30
Figured it out, Application launcher doesn't like ~/bin/eclipse use /home/user/bin/eclipse instead.

Also used chmod u+x ~/bin/eclipse again... although the permission were previously set correctly, the file didn't run until I reset the permissions.

Lastly, configure to use the latest java jdk (install jave 6 jdk first) by using

```
sudo update-alternatives --config java
```

as selecting the java 6 jdk option (#1 for me)

Thanks again.
:)

---

### Post by sgenoves on 2009-12-03
I had the exact problem and solved it by:

1. Making the Sun JVM my default JVM.
2. In the startup script (/usr/bin/eclipse) it adds a path to LD_LIBRARY_PATH, but never exports it, so I added the export.

---

