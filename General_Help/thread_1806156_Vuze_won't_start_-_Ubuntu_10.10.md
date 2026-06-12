---
title: "Vuze won't start - Ubuntu 10.10"
date: 2011-07-17
forum: General Help
---

### Post by pingu1 on 2011-07-17
I downloaded it from vuze.com and used this tutorial:
[http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu](http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu)

I get this output when trying /opt/vuze/vuze:

jarkro@jarkro-Presario-CQ61-Notebook-PC:~$ /opt/vuze/vuze
Starting Azureus...
Suitable java version found [java = 1.6.0_20]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 64-bit SWT libraries on 32-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner-addons for GRE
	Can not use GRE from /usr/lib/xulrunner-addons because it's missing libxpcom.so.
  checking /usr/lib/firefox-3.6.10 for GRE
GRE found at /usr/lib/firefox-3.6.10.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox-3.6.10
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox-3.6.10
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/vuze" -Dazureus.install.path="/opt/vuze" -Dazureus.script="/opt/vuze/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/opt/vuze/Azureus2.jar ; file:/opt/vuze/swt.jar ; file:/opt/vuze/
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
jarkro@jarkro-Presario-CQ61-Notebook-PC:~$

---

### Post by pingu1 on 2011-07-17
anybody know what's wrong?

---

### Post by pingu1 on 2011-07-17
If i go into the folder /opt/vuze/ and click the vuze-file -> nothing happends.

---

### Post by Cpierce on 2011-07-17
I have Getdeb added as other sources and just went to Synaptic and searched vuze. There is only one and it installed fine.

---

### Post by pingu1 on 2011-07-17
what did you specifically write to get the getdeb under other sources?
What adress, etc? I only have Getdeb games...

---

### Post by pingu1 on 2011-07-17
I've downloaded Amule... and this seems to work, although you get less information about the state of the files you download... :-(
Vuze is clearly better...

Are there any other clients that I can use if I don't get vuze up and running...

---

