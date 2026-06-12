---
title: "Need Help with installing Java"
date: 2010-01-29
forum: General Help
---

### Post by Horomancer on 2010-01-29
I want to view the files for RepRap, but do not know which java files to install. Here is the error readout from running the reprap shell script.


```
keeper@keeper-netbook:~/Desktop/reprap-mendel-20100105$ ./reprap
Exception in thread "Main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   at java.awt.EventQueue.invokeLater(libgcj.so.81)
   at javax.swing.SwingUtilities.invokeLater(libgcj.so.81)
   at org.reprap.Main.main(Unknown Source)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.81)
   at java.lang.Runtime.loadLibrary(libgcj.so.81)
   at java.lang.System.loadLibrary(libgcj.so.81)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.81)
   ...3 more
keeper@keeper-netbook:~/Desktop/reprap-mendel-20100105$ ./reprap
Experimental:  JNI_OnLoad called.
Experimental:  JNI_OnLoad called.
Stable Library
=========================================
Native lib Version = RXTX-2.1-7
Java lib Version   = RXTX-2.1-7
Experimental:  JNI_OnLoad called.
Error opening port: /dev/ttyUSB0
Exception during event dispatch:
java.lang.NoClassDefFoundError: javax.media.j3d.X11NativeConfigTemplate3D
   at java.lang.Class.initializeClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at javax.media.j3d.NativeConfigTemplate3D$1.run(NativeConfigTemplate3D.java:79)
   at java.security.AccessController.doPrivileged(libgcj.so.81)
   at javax.media.j3d.NativeConfigTemplate3D.createNativeConfigTemplate3D(NativeConfigTemplate3D.java:74)
   at javax.media.j3d.NativePipeline.initialize(NativePipeline.java:127)
   at javax.media.j3d.Pipeline.createPipeline(Pipeline.java:170)
   at javax.media.j3d.MasterControl.loadLibraries(MasterControl.java:965)
   at javax.media.j3d.VirtualUniverse.<clinit>(VirtualUniverse.java:299)
   at java.lang.Class.initializeClass(libgcj.so.81)
   at javax.media.j3d.GroupRetained.<init>(GroupRetained.java:161)
   at javax.media.j3d.BranchGroupRetained.<init>(BranchGroupRetained.java:55)
   at javax.media.j3d.BranchGroup.createRetained(BranchGroup.java:76)
   at javax.media.j3d.SceneGraphObject.<init>(SceneGraphObject.java:119)
   at javax.media.j3d.Node.<init>(Node.java:178)
   at javax.media.j3d.Group.<init>(Group.java:556)
   at javax.media.j3d.BranchGroup.<init>(BranchGroup.java:68)
   at org.reprap.gui.Panel3D.<init>(Unknown Source)
   at org.reprap.gui.RepRapBuild.<init>(Unknown Source)
   at org.reprap.Main.createAndShowGUI(Unknown Source)
   at org.reprap.Main.access$1500(Unknown Source)
   at org.reprap.Main$9.run(Unknown Source)
   at java.awt.event.InvocationEvent.dispatch(libgcj.so.81)
   at java.awt.EventQueue.dispatchEvent(libgcj.so.81)
   at java.awt.EventDispatchThread.run(libgcj.so.81)
Caused by: java.lang.ClassNotFoundException: sun.awt.X11GraphicsDevice not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./reprap.jar,file:./j3dcore.jar,file:./j3d-org-java3d-all.jar,file:./j3dutils.jar,file:./vecmath.jar,file:./RXTXcomm.jar,file:./swing-layout-1.0.3.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.81)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.ClassLoader.loadClass(libgcj.so.81)
   at java.lang.Class.forName(libgcj.so.81)
   at java.lang.Class.initializeClass(libgcj.so.81)
   ...25 more

```

---

### Post by doas777 on 2010-01-29
check this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

and if you are developing:
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-install-configure-jdk-jre/)

be sure to run the update alternatives command, so that your system will acytually use the java you have jsut installed.

---

### Post by Horomancer on 2010-02-02
thank you!

---

