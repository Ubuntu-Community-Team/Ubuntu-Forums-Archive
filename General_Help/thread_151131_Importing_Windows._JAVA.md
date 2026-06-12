---
title: "Importing Windows. JAVA"
date: 2006-03-27
forum: General Help
---

### Post by dev-h on 2006-03-27
Hello. I have a big trouble on my Ubuntu system and my boss is thinking about dont let me use it at my work cause of this problem.


I cannot import the window of some aplications. When i try it i get this error message:


Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using '192.168.100.20:0.0' as the value of the DISPLAY variable.
at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
at sun.awt.X11GraphicsEnvironment.access$000(X11GraphicsEnvironment.java:53)
at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:142)
at java.security.AccessController.doPrivileged(Native Method)
at sun.awt.X11GraphicsEnvironment.(X11GraphicsEnvironment.java:131)
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:164)
at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
at sun.awt.motif.MToolkit.(MToolkit.java:93)
at java.lang.Class.forName0(Native Method)
at java.lang.Class.forName(Class.java:164)
at java.awt.Toolkit$2.run(Toolkit.java:821)
at java.security.AccessController.doPrivileged(Native Method)
at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:804)
at javax.swing.UIManager.initialize(UIManager.java:1262)
at javax.swing.UIManager.maybeInitialize(UIManager.java:1245)
at javax.swing.UIManager.getUI(UIManager.java:851)
at javax.swing.JPanel.updateUI(JPanel.java:104)
at javax.swing.JPanel.(JPanel.java:64)
at javax.swing.JPanel.(JPanel.java:87)
at javax.swing.JPanel.(JPanel.java:95)
at SC_IP.graph.MenuSC.(Unknown Source)
at SC_IP.graph.MenuSC.main(Unknown Source)





Annoying... I have found on java forums some ppl with the same problem but i cannot find the solution.

Ubuntu breezy, xhost +, when i ssh -X myself it works correctly....
And the worst thing!!!! With Exceed over Windows XP it works perfect :(

---

