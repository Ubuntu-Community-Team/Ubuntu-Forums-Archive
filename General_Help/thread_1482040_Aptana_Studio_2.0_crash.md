---
title: "Aptana Studio 2.0 crash"
date: 2010-05-13
forum: General Help
---

### Post by samuel.faith on 2010-05-13
Hi folks,

Being a front-end web designer, I mainly used SciTE on Windows. But since a few years back, I switched to Ubuntu and now mainly using Aptana Studio.

I upgraded to Lucid Lynx a week ago, everything worked just fine. But now, when I tried working on Aptana Studio, it crashed.

It doesn't crash on all occasions, but especially when I create new project and click on "Finish" button. It is annoying the hell out of me. The process did a directory for that project in the set workspace. 

When I close My Studio window, it also crashed Aptana. By crash I mean it closes down itself!

And I once got this error message:

```

/usr/bin/java
-Xms40m
-Xmx512m
-Djava.awt.headless=true
-XX:MaxPermSize=256m
-jar
/home/samuelfaith/Aptana Studio 2.0//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
-data
/home/samuelfaith/workspace
-os
linux
-ws
gtk
-arch
x86_64
-showsplash
-launcher
/home/samuelfaith/Aptana Studio 2.0/AptanaStudio
-name
AptanaStudio
--launcher.library
/home/samuelfaith/Aptana Studio 2.0//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.200.v20090519/eclipse_1206.so
-startup
/home/samuelfaith/Aptana Studio 2.0//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
-exitdata
3718016
-application
com.aptana.ide.desktop.integration.Application
-vm
/usr/bin/java
-vmargs
-Xms40m
-Xmx512m
-Djava.awt.headless=true
-XX:MaxPermSize=256m
-jar
/home/samuelfaith/Aptana Studio 2.0//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar

```

Any ideas why it's happening?

Samuel Faith

---

### Post by Ensnared on 2010-05-14
The same thing happens to me when I close the My Studio tab, but so far I haven't had it happen elsewhere.
I don't know if this is a Lucid exclusive issue since I've only just discovered Apatana after having used jEdit as my code-editor-of-choice for the last decade or so.

I get the following in the terminal when it crashes:
```
The program 'Aptana Studio' received an X Window System error.
This probably reflects a bug in the program.
The error was 'RenderBadPicture (invalid Picture parameter)'.
  (Details: serial 11570 error_code 172 request_code 152 minor_code 7)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

---

### Post by Bronto on 2010-05-14
I've solved my crashing problems by launching Aptana with a custom script:

```
#!/bin/bash
export GDK_NATIVE_WINDOWS=true
/path/to/Aptana/AptanaStudio
```

---

### Post by Ensnared on 2010-05-14
> **Bronto said:**
> I've solved my crashing problems by launching Aptana with a custom script:

```
#!/bin/bash
export GDK_NATIVE_WINDOWS=true
/path/to/Aptana/AptanaStudio
```

I've already tried this, as it was one of the ways of solving certain issues with Zend Studio (not crashes though, but unresponsive buttons and other GUI hickups). Since both Zend and Aptana are based on Eclipse I figured it might help some, but alas, no such luck.

---

