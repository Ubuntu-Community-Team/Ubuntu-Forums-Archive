---
title: "Freemind install java woes"
date: 2006-04-15
forum: General Help
---

### Post by jlhughes on 2006-04-15
I managed to get the java runtime installed (I think) and all of the dependencies the freemind ( [http://sourceforge.net/projects/freemind/](http://sourceforge.net/projects/freemind/) ) needs.

BUT when I attempt to launch freemind, I get this output:

Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.g
tk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0
)
   at javax.swing.RepaintManager.addInvalidComponent(javax.swing.JComponent) (/usr/lib/lib
gcj.so.6.0.0)
   at javax.swing.JComponent.revalidate() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.setOpaque(boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel(java.awt.LayoutManager, boolean) (/usr/lib/libgcj.so.6.0.0
)
   at javax.swing.JPanel.JPanel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.createGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.getGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.JRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.createRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.getRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.frameInit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.JFrame(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at freemind.main.FreeMind.FreeMind() (Unknown Source)
   at freemind.main.FreeMind.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in                gnu.gcj.runtime.SystemClassLoader{urls=[file:./,file:/usr/share/freemind/lib/freemind.jar               ,file:./,file:/usr/share/freemind/lib/ant/lib/jaxb-api.jar,file:/usr/share/freemind/lib/an               t/lib/jaxb-impl.jar,file:./,file:/usr/share/freemind/lib/ant/lib/jaxb-libs.jar,file:/usr/s               hare/freemind/lib/ant/lib/namespace.jar,file:./,file:/usr/share/freemind/lib/ant/lib/xsdli               b.jar,file:/usr/share/freemind/lib/ant/lib/jax-qname.jar,file:./,file:/usr/share/java/form               s-1.0.5.jar,file:/usr/share/java/commons-lang.jar,file:./,file:/usr/share/java/jaxp-1.2.ja               r,file:/usr/share/java/relaxngDatatype.jar,file:./,file:/usr/share/freemind/], parent=gnu.               gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0               )
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/               libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more


Any ideas what I'm missing? 

 In another thread on a different java app, they listed a number of libs and other possible necessary files. All of those where installed.

---

### Post by MartinG on 2006-04-15
I think what's happening is that the program is trying to use the free Java from the basic Ubuntu installation.  But Freemind needs Sun Java to run.

When you say you think you installed Java I presume you mean the Sun version, but if so the system is not using it.  Try the following:```
sudo update-alternatives --set java /usr/lib/j2re1.5-sun/bin/java
```Before you run it, check that /usr/lib/j2re1.5-sun/bin/java is a valid path!

---

### Post by jlhughes on 2006-04-15
That did the trick. But the people at freemind suggested that will affect all applications. 

Instead, they recommend following the instructions found here:

[http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux](http://freemind.sourceforge.net/wiki/index.php/FreeMind_on_Linux)
#How_can_I_make_FreeMind_use_a_specific_Java_Virtual_Machine.3F


 How can I make FreeMind use a specific Java Virtual Machine?

If you've installed FreeMind from a package, you can make it use a different Java virtual machines than other programs by adding lines similar to the 2 following ones to /etc/freemind/freemindrc, for all users, or to $HOME/.freemind/freemindrc, for you, so that only FreeMind is impacted (and no other program):

   export PATH=$PATH:/usr/java/j2re1.4.2_04/bin
   export JAVA_HOME=/usr/java/j2re1.4.2_04

---

### Post by gritsul on 2007-04-21
Hello!

I have added page for Freemind in documentation part.
May be it will help you.

So check it.

[URL="https://help.ubuntu.com/community/Freemind"][SIZE="3"][COLOR="Black"]_**Freemind fiesty install**_[/COLOR][/SIZE]
[/URL]

---

