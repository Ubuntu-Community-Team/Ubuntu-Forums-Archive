---
title: "Help compiling files for install and ./configure command"
date: 2011-12-28
forum: General Help
---

### Post by Rtedmonston on 2011-12-28
I've recently switched over to Linux/Ubuntu, using version 11.10 (Oneiric Ocelot), I cannot figure out how for the life of me to compile source code from the command terminal to install anything. I've been trying it with the latest version of Tor, start-tor-browser Shell Script, I can run it by double clicking and it seems to work fine, though it opens no program icon in the task bar. I search for it in dash but it's not there. I want to actually install it so I can keep it in my launcher. 

Some of the instructions say to compile the source code file, tried to, only the ./configure command is never found/doesn't work, I cd into the directory the file is in via terminal, it always gives me "not a valid command" response. I've already added the repositories to etc/sources.list through Synaptic manager and have the keys. 

Am I missing something to use it?

---

### Post by azmyth on 2011-12-28
chmod +x configure
./configure

---

### Post by Rtedmonston on 2011-12-28
chmod: cannot access `configure': No such file or directory
bash: ./configure: No such file or directory

---

### Post by bruno9779 on 2011-12-28
Are you in the right folder?
```
ls
```
and check that configure has a green font (it means executable in the deafult ubuntu shell)
then after configure
```
make
```
and most of the times
```
sudo make install
```

This is the autotools way of compiling and it is the most common by far. Be aware that there are several other compiling tools (cmake etc..)
You will surely need some dependencies to compile. build-essentials is the most obvious, but you will need to check the ./configure stage for missing dependencies.

It is much easier than it sounds. Kind of fun as well once you get the hang of it

---

### Post by oldos2er on 2011-12-29
[S]What program are you trying to compile?[/S] Have you checked the repositories for it?

Edit: To install tor, see [https://help.ubuntu.com/community/Tor](https://help.ubuntu.com/community/Tor)
There is a repository for Oneiric even though it's not mentioned on that page.

---

### Post by Rtedmonston on 2011-12-29
Which folder am I supposed to cd into to see configure? I think I have  Tor installed properly, since terminal tells me Tor-geoipdb is the  newest version, but I can only run it from the shell script I DLed? I  can't find it or vidalia in my programs directory.

I'm trying to follow these instructions: [https://www.torproject.org/docs/debian.html.en#ubuntu](https://www.torproject.org/docs/debian.html.en#ubuntu)
I can't find the /etc/apt/sources.list file anywhere either.

---

### Post by oldos2er on 2011-12-30
If you already have tor installed why are you trying to compile it? The start-tor-browser script should do everything you need.

---

### Post by Rtedmonston on 2011-12-30
Because I'd like to get ./configure working for future use. which folder am I supposed to cd into before I make ./configure?

---

### Post by chipbuster on 2011-12-30
First off, make sure you actually have source code. Firefox 9 and ioUrbanTerror both download as a set of executable binaries (pre-compiled), so trying to compile that will leave you going nowhere. To use the configure script, you need to be in the folder where the configure script is (if you have the code downloaded into /home/user/Desktop/sourcecode, you need to be in /home/user/Desktop/sourcecode to use configure)

You say you go to the directory that the "file" is in. Source code is usually "files" plural. Was that a typo or are you looking at a tarball? if its a tar.gz or tar.bz2, you need to extract it first.

---

### Post by oldos2er on 2011-12-30
> **Rtedmonston said:**
> Because I'd like to get ./configure working for future use. which folder am I supposed to cd into before I make ./configure?

Wherever you extracted the source code to. Since I can't see files and folders on your system, I can't be any more specific than that.

Edit: Maybe this info will help:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by Rtedmonston on 2011-12-31
Oh, well I don't see any ./config files anywhere in the package, guess there aren't any. Really confusing to me, I thought it was a universal command.

---

### Post by Rtedmonston on 2011-12-31
Ok so now Im trying Vuze (Azureus), again can't find any config files in  the dir. The shell script does nothing when I run it, I followed those  instructions, ./configure not a valid command, etc. etc. 

Am I just not seeing something? Here's my files: [http://imageshack.us/photo/my-images/196/screenshotat20111231152.png/](http://imageshack.us/photo/my-images/196/screenshotat20111231152.png/)

---

### Post by Rtedmonston on 2011-12-31
I'm trying to get Vuze running but it won't start, I run it in terminal and get this: 

> :~$ vuze
Starting Azureus...
Suitable java version found [java = 1.6.0_23]
Configuring environment...
Java exec found in PATH. Verifying...
Browser check failed with: Cannot load 64-bit SWT libraries on 32-bit JVM
Auto-scanning for GRE/XULRunner.  You can skip this by appending the GRE path to LD_LIBRARY_PATH and setting MOZILLA_FIVE_HOME.
  checking /usr/lib/xulrunner-addons for GRE
    Can not use GRE from /usr/lib/xulrunner-addons because it's missing libxpcom.so.
  checking /usr/lib/mozilla for GRE
    Can not use GRE from /usr/lib/mozilla because it's missing libxpcom.so.
  checking /usr/lib/firefox-addons for GRE
    Can not use GRE from /usr/lib/firefox-addons because it's missing libxpcom.so.
  checking /usr/lib/firefox-8.0 for GRE
GRE found at /usr/lib/firefox-8.0.
Browser check failed with: Could not initialize class org.eclipse.swt.widgets.Display
Can't create browser.  Will try to set LD_LIBRARY_PATH and hope Vuze has better luck.
setting LD_LIBRARY_PATH to: /usr/lib/firefox-8.0
setting MOZILLA_FIVE_HOME to: /usr/lib/firefox-8.0
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/opt/vuze" -Dazureus.install.path="/opt/vuze" -Dazureus.script="/opt/vuze/vuze" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/opt/vuze/Azureus2.jar ; file:/opt/vuze/swt.jar ; file:/opt/vuze/
[alert] Alert:3:Failed to access torrent file ''. Ensure sufficient temporary file space available (check browser cache usage).
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
    at java.lang.Thread.run(Thread.java:679)
Caused by: java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:214)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:84)
    at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:63)
    at com.aelitis.azureus.ui.swt.Initializer.<init>(Initializer.java:162)
    ... 12 more
Exit from Azureus complete
No shutdown tasks to do
Azureus TERMINATED.

Can anyone tell me what's wrong?

---

### Post by oldos2er on 2012-01-01
> **Rtedmonston said:**
> Ok so now Im trying Vuze (Azureus), again can't find any config files in  the dir. The shell script does nothing when I run it, I followed those  instructions, ./configure not a valid command, etc. etc. 

There's no configure script there, so....

> Am I just not seeing something? Here's my files: [http://imageshack.us/photo/my-images/196/screenshotat20111231152.png/](http://imageshack.us/photo/my-images/196/screenshotat20111231152.png/)

Looks like Azureus is a Java program, so you would run the .jar file there, or possibly vuze or azureus. What does the README.txt file tell you?

---

### Post by Paqman on 2012-01-01
Rtedmonston, it's actually very, very rare that you'll need to compile a program. I haven't done it for years. The first place to go for software is Ubuntu Software Centre. You'll find Azureus in there, along with thousands of other packages that can be installed with a couple of clicks.

---

### Post by Rtedmonston on 2012-01-01
> **oldos2er said:**
> There's no configure script there, so....



Looks like Azureus is a Java program, so you would run the .jar file there, or possibly vuze or azureus. What does the README.txt file tell you?


It says Java is needed and to extract the package and run the script from terminal, I've done all that and posted the error it gives me above.

---

### Post by oldos2er on 2012-01-01
I don't use Azureus, so I don't think I can help you any further except to suggest you try their forum, [http://forum.vuze.com/index.jspa](http://forum.vuze.com/index.jspa)

---

