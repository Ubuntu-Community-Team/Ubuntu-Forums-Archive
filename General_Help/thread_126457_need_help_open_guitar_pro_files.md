---
title: "need help: open guitar pro files"
date: 2006-02-06
forum: General Help
---

### Post by dage on 2006-02-06
Hi all,
Someone can help me to find a program that open gp3, gp4, gp5 files please, they're tab's file for guitar :), in windows, i use guitar pro 5 but in linux .... :(
 Thank you

---

### Post by lha on 2006-02-06
See [DGuitar]("http://dguitar.sourceforge.net/").

---

### Post by PuNGS on 2006-02-07
I'm going nuts trying to install DGuitar... Can anyone help me? When I run ./DGuitar.sh, it gives this error:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.RepaintManager.addInvalidComponent(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.revalidate() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.setOpaque(boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel(java.awt.LayoutManager, boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.createGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.getGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.JRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.createRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.getRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.frameInit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.JFrame() (/usr/lib/libgcj.so.6.0.0)
   at dguitar.gui.DGuitar.DGuitar() (Unknown Source)
   at dguitar.gui.DGuitar.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:dist/DGuitar.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more
```

Anyone can help me? Thanks in advance.

---

### Post by Protex on 2006-02-07
Given all the JAVA errors, I'm going to assume that a Java reinstall might not hurt.

---

### Post by PuNGS on 2006-02-07
But I use Java applications like Frostwire with no problems... And I can see Java stuff on Firefox perfectly... I think the error is in this line:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
```

---

### Post by gsmith on 2006-06-27
[QUOTE=PuNGS]But I use Java applications like Frostwire with no problems... And I can see Java stuff on Firefox perfectly... I think the error is in this line:

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
```[/QUOTE]

I am using the sun-java5-jre package from multiverse repository for my Java runtime and had this problem with another application.  Installing the libgcj7-awt package solved it.  Hope this works for you too.

---

### Post by lijno on 2006-07-18
Hi, I had the same problem with another application (JBidWatcher), and installing libgcj7-awt worked fine! Thanks for the tip.

---

