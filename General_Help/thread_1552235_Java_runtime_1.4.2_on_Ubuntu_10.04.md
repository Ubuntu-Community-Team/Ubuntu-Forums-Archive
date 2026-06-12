---
title: "Java runtime 1.4.2 on Ubuntu 10.04"
date: 2010-08-13
forum: General Help
---

### Post by cprofitt on 2010-08-13
I am looking for a good guide for installing and using Java 1.4.2 on Ubuntu 10.04 64bit including the browser plugin...

Anyone have a good reference?

Thanks

Or forcing the JDK to 32bit might work as well.

I am having issues with using the Virtual Media function of HP iLO2.

---

### Post by Queue29 on 2010-08-13
Java 1.4.2 reached EOL in 2008. 

However, if you really think it's going to help: 
[http://java.sun.com/j2se/1.4.2/jre/install.html](http://java.sun.com/j2se/1.4.2/jre/install.html)

Install Guide:
[http://java.sun.com/j2se/1.4.2/jre/install-linux.html](http://java.sun.com/j2se/1.4.2/jre/install-linux.html)

---

### Post by cprofitt on 2010-08-13
I have read and attempted those instructions... I could not get the plug-in to show in Firefox... perhaps I did not follow them properly...

As far as EOL goes -- when a vendor say's "use this version" -- you use that version or get no help. So it does not matter what I think.

---

### Post by cprofitt on 2010-08-13
Here is the error I am getting

```

Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/cprofitt

----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------

Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/cdstart.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/cdstop.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/active.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/inactive.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/fdstart.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/fdstop.gif
Loaded image: jar:https://10.120.254.13/vtd150p02.jar!/com/hp/ilo2/virtdevs/fistart.gif
Exception: java.io.FileNotFoundException: /home/cprofitt/.java/hp.properties (No such file or directory)
Checking for /tmp/cpqma-b09dc35
DLL not present
Loading /tmp/cpqma-b09dc35
Exception in thread "thread applet-com.hp.ilo2.virtdevs.virtdevs.class-1" java.lang.UnsatisfiedLinkError: /tmp/cpqma-b09dc35: /tmp/cpqma-b09dc35: wrong ELF class: ELFCLASS32 (Possible cause: architecture word width mismatch)
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1803)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1699)
    at java.lang.Runtime.load0(Runtime.java:770)
    at java.lang.System.load(System.java:1003)
    at com.hp.ilo2.virtdevs.DirectIO.<clinit>(DirectIO.java:87)
    at com.hp.ilo2.virtdevs.MediaAccess.devices(MediaAccess.java:183)
    at com.hp.ilo2.virtdevs.virtdevs.ui_init(virtdevs.java:363)
    at com.hp.ilo2.virtdevs.virtdevs.start(virtdevs.java:142)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1639)
    at java.lang.Thread.run(Thread.java:619)

```

---

### Post by cprofitt on 2010-08-13
Three more troubleshooting steps.

1.  OS X 10.6 -- JRE 1.6 64bit -- works
2.  Windows 7 -- JRE 1.6 32bit -- works
3.  Live CD Ubuntu 64bit -- JRE 1.6 -- fails

---

