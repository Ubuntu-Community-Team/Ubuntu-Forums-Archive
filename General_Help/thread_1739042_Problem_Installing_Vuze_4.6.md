---
title: "Problem Installing Vuze 4.6"
date: 2011-04-25
forum: General Help
---

### Post by JDog2pt0 on 2011-04-25
I'm on Ubuntu 10.10. When following the directions for installing Vuze, all I'm granted with is this in the terminal. 

Starting Azureus...
Suitable java version found [java = 1.6.0_20]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 64-bit SWT libraries on 32-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/firefox for GRE
    Can not use GRE from /usr/lib/firefox because it's missing libxpcom.so.
  checking /usr/lib/mozilla for GRE
    Can not use GRE from /usr/lib/mozilla because it's missing libxpcom.so.
  checking /usr/lib/firefox-4.0 for GRE
GRE found at /usr/lib/firefox-4.0.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox-4.0
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox-4.0
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/justin/vuze" -Dazureus.install.path="/home/justin/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/justin/vuze/Azureus2.jar ; file:/home/justin/vuze/swt.jar ; file:/home/justin/vuze/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
    at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
    at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
    at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
    at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:114)
    at org.gudy.azureus2.ui.swt.Main.main(Main.java:292)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
    at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:174)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:84)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:63)
    at com.aelitis.azureus.ui.swt.Initializer.<init>(Initializer.java:163)
    ... 12 more
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

I can see the various errors, but I've no clue what the specific cause is.

---

### Post by JDog2pt0 on 2011-04-25
From another forum, I guess I'm mixing 32bit and 64 bit libraries. Vuze apparently thinks everyone is running 64bit linux so that's the SWT it downloads. Now I've been directed to the proper SWT link, but I've no clue how to install the file/s.

---

### Post by jonnyzat on 2011-04-27
> **JDog2pt0 said:**
> From another forum, I guess I'm mixing 32bit and 64 bit libraries. Vuze apparently thinks everyone is running 64bit linux so that's the SWT it downloads. Now I've been directed to the proper SWT link, but I've no clue how to install the file/s.

simply copy the swt.jar file into the vuze directory, replacing the existing swt.jar. the download link i used is : [http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.6.2-201102101200/swt-3.6.2-gtk-linux-x86.zip](http://www.eclipse.org/downloads/download.php?file=/eclipse/downloads/drops/R-3.6.2-201102101200/swt-3.6.2-gtk-linux-x86.zip)

---

### Post by JDog2pt0 on 2011-04-27
That was too easy...lol

Thanks man

---

### Post by sku_dave on 2011-05-31
ok, that swt.jar caused me some serious headache. Thankfully I know how to use the search function ! I'm sure I'll be back here next install...

---

