---
title: "Installing Zend Studio"
date: 2006-02-21
forum: General Help
---

### Post by niclas on 2006-02-21
Hi 

I'm trying to install Zend Studio on Ubuntu 5.10, but I have some problems...

First the installer complained about a missing X11 DISPLAY-variable, so I run

 DISPLAY=localhost:0.0 export DISPLAY 

That error seems to be solved, but now I get this instead:

Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at java.awt.Window.init(Unknown Source)
        at java.awt.Window.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at com.zerog.ia.installer.LifeCycleManager.g(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.h(DashoA8113)
        at com.zerog.ia.installer.LifeCycleManager.a(DashoA8113)
        at com.zerog.ia.installer.Main.main(DashoA8113)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
        at java.lang.reflect.Method.invoke(Unknown Source)
        at com.zerog.lax.LAX.launch(DashoA8113)
        at com.zerog.lax.LAX.main(DashoA8113)
This Application has Unexpectedly Quit: Invocation of this Java Application has caused an InvocationTargetException. This application will now exit. (LAX)

I'm running the installer as root, and have installed the Sun JRE-1.5

Could anyone tell me whats wrong, beacuse I can't solve it even though I have tried the Google-way for hours...

Regards

/Niclas

---

### Post by weissed on 2006-02-24
Hi,

You could try running the app by executing the **runStudio_unix.sh** script inside the bin folder of your Zend Studio install. (Make sure your pwd is the bin folder) If it works this way, then your problem is the classpath set in the script. Everywhere it's using relative paths, and this is a problem when you execute the script by it's full path, from a folder different from the bin in the Zend install folder.

Hope this helps.

---

### Post by emanaton on 2008-06-19
Oddly enough, I was getting this same error while in "sudo -i", but as soon as I dropped down to a 'normal' user, it installed just fine!

For the record, I'm in the 64 bit Heron with sun 64 bit java installed.

Sean P. O. MacCath-Moran
[www.emanaton.com](www.emanaton.com)

---

