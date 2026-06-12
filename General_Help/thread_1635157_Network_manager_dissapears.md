---
title: "Network manager dissapears"
date: 2010-12-01
forum: General Help
---

### Post by joelstitch on 2010-12-01
For some reason my Network Manager keeps disappearing after 30-60 minutes sometimes even less than that. I read a few topics of people having this problem but when they restart their computer, with me the icon appears and it connects to the internet fine but after a while the internet goes out and the icon disappears and I have to open it again. I also tried using wicd but for some reason it doesn't want to connect to some connections. How can I make it not disappear?

---

### Post by joelstitch on 2010-12-06
I am also trying Wicd with no luck. A while ago I uninstall network-manager and installed wicd instead and it worked fine but now wicd doesn't want to connect, every time I try to connect to my house internet it says that it was unable to get an IP address.

---

### Post by joelstitch on 2010-12-07
I could really use some help here...

---

### Post by joelstitch on 2010-12-15
When i open Network manager on the terminal this is what I get:

> pag@pag-laptop:~$ nm-applet
** (nm-applet:5476): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:5476): DEBUG: foo_client_state_changed_cb
** (nm-applet:5476): DEBUG: foo_client_state_changed_cb
** (nm-applet:5476): DEBUG: old state indicates that this was not a disconnect 2
** (nm-applet:5476): DEBUG: going for offline with icon: notification-network-wireless-disconnected
** Message: Caught signal 15, shutting down...
When the icon disappears from the Panel this is what comes up on the terminal "**** Message: Caught signal 15, shutting down...**"

---

### Post by JeanVW14 on 2011-01-18
+1

Any takers?

BTW, if you want to get the network icon back in the gnome panel, hit Alt-F2 and run 'nm-applet'.

---

### Post by xscd on 2011-01-24
The following solved the nm-applet not appearing issue for me--

[http://georgia.ubuntuforums.org/showthread.php?t=1588455]("http://georgia.ubuntuforums.org/showthread.php?t=1588455")

Good luck! :)

---

