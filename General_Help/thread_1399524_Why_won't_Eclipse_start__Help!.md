---
title: "Why won't Eclipse start?  Help!"
date: 2010-02-05
forum: General Help
---

### Post by josephellengar on 2010-02-05
I am talking about the java IDE.  For some reason it just won't start.  I am using 64-bit, so that might have something to do with it.  There is no terminal output when I try to start it from a terminal.  It just moves on to another command prompt.  Any help would be great.  I am really desperate for this.

---

### Post by GregBrannon on 2010-02-05
Describe how you acquired and installed Eclipse, where it is installed, the command line you're using to start it (Why not run it from the GUI?), and the details of your Java (JDK/JRE, Sun or Open) installation.

---

### Post by josephellengar on 2010-02-05
> **GregBrannon said:**
> Describe how you acquired and installed Eclipse, where it is installed, the command line you're using to start it (Why not run it from the GUI?), and the details of your Java (JDK/JRE, Sun or Open) installation.

I installed the latest version from synaptic (version from 3.5.1).  I wasn't running it from the gui just because I wanted to see if there were errors when I ran it (the command was simply "eclipse").  It doesn't work when I run it with alt-f2 or from the Applications menu either.  My java is sun-java-6-15-1bin and the java jre (and JDK).  I'm not sure where it is installed, as I installed it from synaptic- just in the default location.

---

### Post by josephellengar on 2010-02-06
Do you have any ideas?  I'm really kind of desperate here.  Could it have something to do with my OS being 64 bit?

---

### Post by GregBrannon on 2010-02-06
Have you tried running it from the GUI to see if it will run that way?  I run Eclipse in 64- and 32-bit Linux/KDE and MacOS environments, and it runs fine, so that your running it in 64-bit is not the root cause of your problems.  There's just not a lot to go on.  Try reinstalling?

---

### Post by josephellengar on 2010-02-06
> **GregBrannon said:**
> Have you tried running it from the GUI to see if it will run that way?  I run Eclipse in 64- and 32-bit Linux/KDE and MacOS environments, and it runs fine, so that your running it in 64-bit is not the root cause of your problems.  There's just not a lot to go on.  Try reinstalling?

Thank you so much for your response.  I have tried running it in the GUI from both the applications menu and the alt-f2.  I have also tried reinstalling.  What version of Java do you have on your machine?  Oh, and I am running in Gnome, if that makes any difference.

---

### Post by josephellengar on 2010-02-06
I've reinstalled again and installed some of the optional libraries.  Now the splash screen appears, but after that the program still doesn't start.  Have you had this problem before?

---

### Post by josephellengar on 2010-02-06
I found a log file with some error messages from my last failed launch:

```

!ENTRY org.eclipse.osgi 4 0 2010-02-06 11:16:39.137
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:179)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:516)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:143)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:88)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
	at org.eclipse.equinox.launcher.Main.main(Main.java:1287)

```

---

### Post by GregBrannon on 2010-02-07
I apologize for the time between posts, but I'm distracted and sleep deprived by the shuttle launch this weekend.  I fled the mid-Atlantic snowstorm in time to make it to Kennedy for Sunday morning's launch, and it was scrubbed for weather. We're trying again Monday morning, but if it doesn't go this time, we're headed home.

Good job on what you've done so far and posting the resulting error message from your log.  It appears from the first long line in your log that you only have the 32-bit Java libraries installed and you're trying to run a Java program (Eclipse) that requires the 64-bit libraries.  Review your JDK install and ensure that you've installed the 64-bit libraries.

I don't have an Ubuntu machine with me in Florida, so can't give specific directions. If after reviewing your install it is not obvious, then Google something like "JDK 64-bit install," adding Ubuntu and/or synaptic as necessary to get the helpful results.

Hang in there; you'll get it to work.

---

### Post by josephellengar on 2010-02-07
> **GregBrannon said:**
> I apologize for the time between posts, but I'm distracted and sleep deprived by the shuttle launch this weekend.  I fled the mid-Atlantic snowstorm in time to make it to Kennedy for Sunday morning's launch, and it was scrubbed for weather. We're trying again Monday morning, but if it doesn't go this time, we're headed home.

Good job on what you've done so far and posting the resulting error message from your log.  It appears from the first long line in your log that you only have the 32-bit Java libraries installed and you're trying to run a Java program (Eclipse) that requires the 64-bit libraries.  Review your JDK install and ensure that you've installed the 64-bit libraries.

I don't have an Ubuntu machine with me in Florida, so can't give specific directions. If after reviewing your install it is not obvious, then Google something like "JDK 64-bit install," adding Ubuntu and/or synaptic as necessary to get the helpful results.

Hang in there; you'll get it to work.
I figured it out.  Thanks for your help though!  For some reason, just installing openjava got it to work.

---

### Post by GregBrannon on 2010-02-07
Good job!  Glad you got it working.  You fixed it by adding the 64-bit libraries you were missing.

Now, if you see Eclipse not responding to mouse clicks on dialogue buttons, start it from a script file that includes the line:

GDK_NATIVE_WINDOWS=true

before starting Eclipse.

Happy programming!

---

