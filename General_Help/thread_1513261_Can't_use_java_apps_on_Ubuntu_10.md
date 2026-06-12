---
title: "Can't use java apps on Ubuntu 10"
date: 2010-06-19
forum: General Help
---

### Post by phaggood on 2010-06-19
After upgrading to Ubuntu 10 on my netbook, no java apps (specifically jedit and freemind) work anymore.  Before the upgrade, all worked fine.  Per searches on google I've uninstalled compiz and used the AWTToolkit/MToolkit fix; neither fix worked, java apps still startup with blank screens and are unusable.  I've got sun-java6-jdk installed with build 1.6.0_20_b02.  

Starting the apps on the commandline I have the following output (truncated)

pbh@FullMetal:~$ jedit
pbh@FullMetal:~$ Warning: Cannot convert string "-dejavu-dejavu sans-medium-r-normal--*-140-*-*-p-*-iso10646-1" to type FontStruct

pbh@FullMetal:~$ 8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0: Exception in thread "AWT-EventQueue-0" 
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0: java.lang.OutOfMemoryError: Java heap space
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at org.gjt.sp.jedit.textarea.ChunkCache.recalculateVisibleLines(ChunkCache.java:155)
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at org.gjt.sp.jedit.textarea.TextArea.recalculateVisibleLines(TextArea.java:4900)
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at org.gjt.sp.jedit.textarea.TextAreaPainter.setBounds(TextAreaPainter.java:166)
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at org.gjt.sp.jedit.textarea.ScrollLayout.layoutContainer(ScrollLayout.java:157)
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at java.awt.Container.layout(Container.java:1421)
8:15:37 AM [AWT-EventQueue-0] [error] AWT-EventQueue-0:  at java.awt.Container.doLayout(Container.java:1410)

pbh@FullMetal:~$ freemind
Checking Java Version...
Warning: Cannot convert string "-dejavu-dejavu sans-medium-r-normal--*-140-*-*-p-*-iso10646-1" to type FontStruct

STDERR: Exception in thread "AWT-EventQueue-0" 
STDERR: java.lang.RuntimeException: Couldn't create pixbuf of size 1276642304x27
STDERR: 	at com.sun.java.swing.plaf.gtk.GTKNativeEngine.nativeStartPainting(Native Method)
STDERR: 	at com.sun.java.swing.plaf.gtk.GTKNativeEngine.startPainting(GTKNativeEngine.java:479)
STDERR: 	at com.sun.java.swing.plaf.gtk.GTKPainter.paintMenuBarBackground(GTKPainter.java:500)
STDERR: 	at javax.swing.plaf.synth.SynthMenuBarUI.update(SynthMenuBarUI.java:102)
STDERR: 	at javax.swing.JComponent.paintComponent(JComponent.java:752)
STDERR: 	at javax.swing.JComponent.paint(JComponent.java:1029)
STDERR: 	at javax.swing.JComponent.paintChildren(JComponent.java:862)
STDERR: 	at javax.swing.JComponent.paint(JComponent.java:1038)
STDERR: 	at javax.swing.JLayeredPane.paint(JLayeredPane.java:567)
STDERR: 	at javax.swing.JComponent.paintChildren(JComponent.java:862)
STDERR: 	at javax.swing.JComponent.paintToOffscreen(JComponent.java:5131)
STDERR: 	at javax.swing.RepaintManager$PaintManager.paintDoubleBuffered(RepaintManager.java:1479)
STDERR: 	at javax.swing.RepaintManager$PaintManager.paint(RepaintManager.java:1410)
STDERR: 	at javax.swing.RepaintManager.paint(RepaintManager.java:1224)
STDERR: 	at javax.swing.JComponent.paint(JComponent.java:1015)
STDERR: 	at java.awt.GraphicsCallback$PaintCallback.run(GraphicsCallback.java:21)
STDERR: 	at sun.awt.SunGraphicsCallback.runOneComponent(SunGraphicsCallback.java:60)
STDERR: 	at sun.awt.SunGraphicsCallback.runComponents(SunGraphicsCallback.java:97)
STDERR: 	at java.awt.Container.paint(Container.java:1780)
STDERR: 	at java.awt.Window.paint(Window.java:3375)
STDERR: 	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:796)
STDERR: 	at javax.swing.RepaintManager.paintDirtyRegions(RepaintManager.java:713)
STDERR: 	at javax.swing.RepaintManager.seqPaintDirtyRegions(RepaintManager.java:693)
STDERR: 	at javax.swing.SystemEventQueueUtilities$ComponentWorkRequest.run(SystemEventQueueUtilities.java:125)
STDERR: 	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
STDERR: 	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
STDERR: 	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
STDERR: 	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
STDERR: 	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
STDERR: 	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
STDERR: 	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
STDERR: 	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

---

### Post by Barafu Albino Cheetah on 2010-06-19
purge both java and apllications, as well as thier settings. Compiz have nothing to dio with it, unless you set up something very weird. 
Have the same combination, works smoothly. Purge configs.

---

