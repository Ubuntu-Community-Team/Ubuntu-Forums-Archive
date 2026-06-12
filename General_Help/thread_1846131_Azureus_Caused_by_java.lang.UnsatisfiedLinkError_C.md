---
title: "Azureus: Caused by: java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries"
date: 2011-09-18
forum: General Help
---

### Post by Dáire Fagan on 2011-09-18
Hello

From the Ubuntu repos I use the following version fine on Xubuntu 11.04:

Java 1.6.0_22
 Sun Microsystems Inc.
SWT v3659, gtk
Linux v2.6.38-11-generic, i386
V4.3.0.6/4 az2

On my 32 bit system I today downloaded [http://cf1.vuze.com/files/Vuze_Installer.tar.bz2](http://cf1.vuze.com/files/Vuze_Installer.tar.bz2) but when I try to run the script I receive the following error:

    > dusf@banshee:/opt/vuze$ ./vuze
    Starting Azureus...
    Suitable java version found [http://java = 1.6.0_22]("http://java%20=%201.6.0_22/")
    Configuring environment...
    Java exec found in PATH. Verifying...
    Browser check failed with: Cannot load 64-bit SWT libraries on 32-bit JVM
    Auto-scanning for GRE/XULRunner.  You can skip this by appending the  GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
      checking /usr/lib/firefox-6.0.2 for GRE
    GRE found at /usr/lib/firefox-6.0.2.
    Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
    Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better luck.
    setting LD_LIBRARY_PATH to: /usr/lib/firefox-6.0.2
    setting MOZILLA_FIVE_HOME to: /usr/lib/firefox-6.0.2
    Loading Azureus:
    java -Xmx128m -cp "./Azureus2.jar:./swt.jar"  -Djava.library.path="/opt/vuze" -Dazureus.install.path="/opt/vuze"  -Dazureus.script="./vuze" -Dazureus.script.version=2  org.gudy.azureus2.ui.swt.Main
    file:/opt/vuze/Azureus2.jar ; file:/opt/vuze/swt.jar ; file:/opt/vuze/
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
            at java.lang.Thread.run(Thread.java:679)
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
    Azureus TERMINATED.If I were to take a guess I would say the problem appears to be I am  trying to use 64bit Azureus on my 32bit system? I did not see any option  for a 32 bit tarball on the website. Either way, how can I remedy this  problem?

---

