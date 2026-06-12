---
title: "Vuze 4.3.1.4 64bit installation issues."
date: 2010-02-20
forum: General Help
---

### Post by Carlo1973 on 2010-02-20
Hi there, I've been trying (unsuccessfully) to install Vuze 4.3.1.4 x86_64 onto my system (Ubuntu 9.10 64bit)

I followed the following guides: [http://ubuntuforums.org/showthread.php?t=1339488&highlight=vuze+4.3]("http://ubuntuforums.org/showthread.php?t=1339488&highlight=vuze+4.3") and [http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu]("http://forlong.blogage.de/en/entries/2008/12/2/How-to-install-and-update-Vuze-formerly-Azureus-4-on-Ubuntu") and although I have a menu item for it, I can't get it to launch.  In the first guide, there is a section that states > 
6) Copy the "swt.jar" file from this folder "/etc/alternatives/swt.jar" and replace the one found in the vuze folder. (if you can't fine it just search the file system for "swt.jar" to find it).

NOTE: If you do not perform step #6 you will probably get an error that says something like this when you try to do the install using the instructions:

Browser check failed with: Cannot load 32-bit SWT libraries on 64-bit JVM Auto-scanning for GRE/XULRunner. You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME

I didn't replace the original swt.jar file. Instead I renamed the file to swt-old.jar and copied the proper one to the folder as stated. I'm not sure if not removing the original swt.jar file is causing the problems I'm experiencing. 

When I run vuze from the command line I get the following:

> carlo@desktop:~$ vuze
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: no swt-gtk-3452 or swt-gtk in swt.library.path, java.library.path or the jar file
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /etc/gre.d/libxul0d.conf for GRE_PATH
GRE found at /usr/lib/xulrunner.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/xulrunner
setting MOZILLA_FIVE_HOME to: /usr/lib/xulrunner
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar:./swt-old.jar" -Djava.library.path="/opt/vuze" -Dazureus.install.path="/opt/vuze" -Dazureus.script="/opt/vuze/azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/opt/vuze/Azureus2.jar ; file:/opt/vuze/swt.jar ; file:/opt/vuze/swt-old.jar ; file:/opt/vuze/
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Invoking main failed
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.UnsatisfiedLinkError: no swt-gtk-3452 or swt-gtk in swt.library.path, java.library.path or the jar file
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:233)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:151)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:130)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:79)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:59)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:110)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 6 more
Exception in thread "MainRunner" java.lang.SecurityException: VM exit operation prohibited
	at org.gudy.azureus2.core3.security.impl.SESecurityManagerImpl$2.checkExit(SESecurityManagerImpl.java:274)
	at java.lang.Runtime.exit(Runtime.java:105)
	at java.lang.System.exit(System.java:923)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:42)
	at java.lang.Thread.run(Thread.java:636)
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.


I've double checked in the Package Manager, and Gecko, xpcom, and XULrunner 1.9 appear to be installed. 

Any help on solving this issue would be great. I've checked around but couldnt find one that quite matched up to the error I'm getting.

Carlo

---

### Post by Carlo1973 on 2010-02-20
Okay I think I fixed this. On a whim I decided to remove the copied swt.jar and re-instate the swt-old.jar file back as swt.jar. 

> carlo@desktop:/opt/vuze$ rm swt.jar
carlo@desktop:/opt/vuze$ mv swt-old.jar swt.jar
carlo@desktop:/opt/vuze$ gksu gedit vuze.desktop


I edited the menu item script

gksu gedit /usr/local/share/applications/vuze.desktop

> [Desktop Entry]

Encoding=UTF-8

Categories=Java;Network;FileTransfer;P2P

Comment=Multimedia Bittorrent Client 

Exec=/opt/vuze/vuze %f
Terminal=false
StartupNotify=true
Type=Application
Icon=/opt/vuze/vuze.png

GenericName=Multimedia Bittorrent Client

MimeType=application/x-bittorrent

Name=Vuze (Azureus 4)



After this program launches just fine. It looks like Azureus/Vuze has updated the swt.jar file properly this time and the instructions to copy over the existing swt.jar file are no longer necessary - At least this is the way it appears. I haven't done any extensive testing to see if stability is an issue.

I hope this helps someone :)

Carlo

---

### Post by Camaguey on 2010-02-24
glad you got it working but the (hidden?) 64 bit version is right here:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)

---

### Post by byte777 on 2010-03-02
> **Camaguey said:**
> glad you got it working but the [COLOR="Red"]**(hidden?)**[/COLOR] 64 bit version is right here:

[http://azureus.sourceforge.net/download.php](http://azureus.sourceforge.net/download.php)
[SIZE="4"][COLOR="DarkGreen"]Thank you so much!!! That was **THE ONLY** solution that worked for me![/COLOR][/SIZE]

---

