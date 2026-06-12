---
title: "azureus won't start after update"
date: 2006-04-15
forum: General Help
---

### Post by sgleo87 on 2006-04-15
I update azureus (two different packages I think) and now I get the following error when I try to start it:
```
sandra@ubuntudesktop:~$ azureus
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in    java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:7 5)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThrea d.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.ja va:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

```

Seems to have something to do with java...anybody have any clue how to fix it? :-k

---

### Post by taurus on 2006-04-15
[QUOTE=sgleo87]
Seems to have something to do with java...anybody have any clue how to fix it? :-k[/QUOTE]
And I assume you have installed java on your machine!!!

---

### Post by jazzmuzik on 2006-04-15
Hmm. I install Azureus manually to my home directory, so my experience may be different than how Ubuntu does it. Anyway...

The file 'azureus' needs to be edited at the top to point to your Java binary directory and from your message it looks like it cannot find the necessary Java files. Below is the top of my azureus file, but you may have a different version of java installed. And again, Ubuntu may automate the process for you... but then again something is wrong with yours, so look inside the file 'azureus' and look at these two settings:

```
#!/bin/bash

######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR="/usr/lib/j2re1.5-sun/bin/"    # use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
PROGRAM_DIR="/home/yourlogin/somedirectory/azureus"  # use full path to Azureus bin dir
#######################################
```

---

### Post by sgleo87 on 2006-04-15
[QUOTE=jazzmuzik]Hmm. I install Azureus manually to my home directory, so my experience may be different than how Ubuntu does it. Anyway...

The file 'azureus' needs to be edited at the top to point to your Java binary directory and from your message it looks like it cannot find the necessary Java files. Below is the top of my azureus file, but you may have a different version of java installed. And again, Ubuntu may automate the process for you... but then again something is wrong with yours, so look inside the file 'azureus' and look at these two settings:

```
#!/bin/bash

######## CONFIGURATION OPTIONS ########
JAVA_PROGRAM_DIR="/usr/lib/j2re1.5-sun/bin/"    # use full path to java bin dir, ex. "/usr/java/j2sdk1.4.2/bin/"
PROGRAM_DIR="/home/yourlogin/somedirectory/azureus"  # use full path to Azureus bin dir
#######################################
```[/QUOTE]


thx that helped! after that is upgraded and everything is fine now.

---

