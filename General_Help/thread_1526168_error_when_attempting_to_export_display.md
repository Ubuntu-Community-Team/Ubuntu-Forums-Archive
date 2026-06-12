---
title: "error when attempting to export display"
date: 2010-07-07
forum: General Help
---

### Post by mkeyes001 on 2010-07-07
I'm attempting to export netbackup gui from a solaris netbackup server to my ubuntu 10.04 desktop.

I set my display from the unix host to my system & then execute the command to bring up the GUI on my ubuntu system.  I get this error message.  Any idea's?

java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnvironment
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(Unknown Source)
        at java.awt.Window.init(Unknown Source)
        at java.awt.Window.<init>(Unknown Source)
        at java.awt.Frame.<init>(Unknown Source)
        at javax.swing.JFrame.<init>(Unknown Source)
        at vrts.common.utilities.CommonFrame.<init>(CommonFrame.java:75)
        at vrts.common.utilities.CommonFrame.<init>(CommonFrame.java:70)
        at vrts.nbe.BaseNBEFrame.<init>(BaseNBEFrame.java:59)
        at vrts.nbe.LoginFrame.<init>(LoginFrame.java:228)
        at vrts.nbe.JavaPresentationLayer.initiateLogin(JavaPresentationLayer.java:154)
        at vrts.nbe.AdminConsole.main(AdminConsole.java:57)

What other info might you need to diagnose the issue?

---

### Post by mkeyes001 on 2010-07-08
Well, I got this fixed.  It was my error, I was using the command "ssh -X host" and then setting my display back to my linux machine.  I didn't need to set my display on the remote host, just run the netbackup gui and it pop up on my linux desktop.  Not sure why I didn't try that yesterday, wasn't thinking I guess.

---

