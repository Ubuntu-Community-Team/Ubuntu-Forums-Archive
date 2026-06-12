---
title: "how do I enable XTEST 2.2 extension"
date: 2006-03-15
forum: General Help
---

### Post by Generic1234 on 2006-03-15
hi

im learning to program in java, and i tried to use the java class awt.Robot.  when i run my compiled program i get this error message:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Robot.Robot() (/usr/lib/libgcj.so.6.0.0)
   at KeyRobot.main(java.lang.String[]) (Unknown Source)
   at .main (/usr/lib/libgij.so.6.0.0)
   at .__libc_start_main (/lib/libc-2.3.5.so)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...4 more

according to the java api page for the Robot class (at [here]("http://java.sun.com/j2se/1.3/docs/api/java/awt/Robot.html") ), it could be because the "XTEST 2.2 standard extension is not supported (or not enabled)".

if this is indeed the problem, how do i enable XTEST?  i did a quick search but could find any instructions on the interweb about it.

---

### Post by Generic1234 on 2006-03-17
no replies?  yes, well, i spose it was rather a specialised question.  or did i post this in the wrong category?

anyway, i now have more serious concerns (ubuntu hanging on startup), so nevermind.

---

