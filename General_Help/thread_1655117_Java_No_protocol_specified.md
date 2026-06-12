---
title: "Java: No protocol specified"
date: 2010-12-29
forum: General Help
---

### Post by Frankie Yale on 2010-12-29
I downloaded SEO PowerSuite. 
[http://www.link-assistant.com](http://www.link-assistant.com)

When I run the installer I get:

```
fyale@seo-uni:~/Downloads/seopowersuite$ sudo ./install.sh 
No protocol specified
java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:82)
    at sun.awt.X11.XToolkit.<clinit>(XToolkit.java:112)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:186)
    at java.awt.Toolkit$2.run(Toolkit.java:849)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:841)
    at sun.swing.SwingUtilities2$AATextInfo.getAATextInfo(SwingUtilities2.java:121)
    at javax.swing.plaf.metal.MetalLookAndFeel.initComponentDefaults(MetalLookAndFeel.java:1564)
    at javax.swing.plaf.basic.BasicLookAndFeel.getDefaults(BasicLookAndFeel.java:147)
    at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1599)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:530)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:570)
    at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1320)
    at javax.swing.UIManager.initialize(UIManager.java:1407)
    at javax.swing.UIManager.maybeInitialize(UIManager.java:1395)
    at javax.swing.UIManager.getInstalledLookAndFeels(UIManager.java:410)
    at javax.swing.UIManager.installLookAndFeel(UIManager.java:453)
    at javax.swing.UIManager.installLookAndFeel(UIManager.java:472)
    at com.agilemind.commons.util.UiUtil.setApplicationLookAndFeel(UiUtil.java:73)
    at com.agilemind.commons.util.ApplicationStarter.a(ApplicationStarter.java:13)
    at com.agilemind.commons.util.ApplicationStarter.access$200(ApplicationStarter.java:18)
    at com.agilemind.commons.util.j.run(j.java:1)
    at com.agilemind.commons.gui.errorproof.b.execute(b.java:3)
    at com.agilemind.commons.gui.errorproof.ErrorProofUtil.executeAsErrorProofThreadAndReturn(ErrorProofUtil.java:2)
    at com.agilemind.commons.gui.errorproof.ErrorProofUtil.executeAsErrorProofThreadAndReturn(ErrorProofUtil.java:19)
    at com.agilemind.commons.gui.errorproof.ErrorProofUtil.executeAsErrorProofThread(ErrorProofUtil.java:4)
    at com.agilemind.commons.util.ApplicationStarter.startApplication(ApplicationStarter.java:30)
    at com.agilemind.macosinstaller.InstallerApplicationStarter.main(InstallerApplicationStarter.java:3)

```

Google'd it, but don't understand the fix.

I'm running Ubuntu 10.10 with the Xubuntu desktop.

---

