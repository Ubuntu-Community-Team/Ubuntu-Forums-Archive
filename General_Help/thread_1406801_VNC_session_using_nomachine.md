---
title: "VNC session using nomachine"
date: 2010-02-14
forum: General Help
---

### Post by waspinator on 2010-02-14
Hi,

I'm trying to run a VNC session through nomachine using Ubuntu 9.10, but I always get connection timeouts. This is all done on a LAN.

I followed this [guide]("http://www.nomachine.com/howto/vnc-session.php") but it doesn't work. I tried using ports 5900, 5901, and 1. And the host name is the same as the ssh hostname.

I also read [here]("http://www.nomachine.com/ar/view.php?ar_id=AR06E00469") that you need to install vncviewer and vncserver on both computers for it to work. I installed vnc viewer, but ubuntu says that vncserver is obsolete and not available. After installing vncviewer, I still get connection timeouts. 

Using Gnome instead of VNC or Shadow in the desktop selection screen in the NX connection wizard works, but spawns a new session, so I cannot share the desktop.

Using Vinagre works for VNC, and SSH/Gnome works in nomachine, but I can't get VNC through nomachine.

Any advice?

Thank you,

Waspinator

---

### Post by 2hot6ft2 on 2010-02-14
> **waspinator said:**
> Hi,

I'm trying to run a VNC session through nomachine using Ubuntu 9.10, but I always get connection timeouts. 

I followed this [guide]("http://www.nomachine.com/howto/vnc-session.php") but it doesn't work. I tried using ports 5900, 5901, and 1. And the host name is the same as the ssh hostname.

I also read [here]("http://www.nomachine.com/ar/view.php?ar_id=AR06E00469") that you need to install vncviewer and vncserver on both computers for it to work. I installed vnc viewer, but ubuntu says that vncserver is obsolete and not available. After installing vncviewer, I still get connection timeouts. 

Using Gnome instead of VNC or Shadow in the desktop selection screen in the NX connection wizard works, but spawns a new session, so I cannot share the desktop.

Using Vinagre works for VNC, and SSH/Gnome works in nomachine, but I can't get VNC through nomachine.

Any advice?

Thank you,

Waspinator
If you already have ssh installed and freenx from nomachine then you can already remote desktop. But as for "sharing the desktop" it makes a new session each time perhaps what you're after is Remote Desktop Sharing which uses vino.
On mine it's under
System > Preferences > Remote Desktop
Not sure what you're after exactly.

---

### Post by waspinator on 2010-02-16
> **2hot6ft2 said:**
> If you already have ssh installed and freenx from nomachine then you can already remote desktop. But as for "sharing the desktop" it makes a new session each time perhaps what you're after is Remote Desktop Sharing which uses vino.
On mine it's under
System > Preferences > Remote Desktop
Not sure what you're after exactly.

Thanks for your reply. I actually already am able to use VNC to do remote desktop sharing, but I wanted to use nomachine's compression protocols to make things faster. Their guide seems to suggest that it is possible, but I always get a connection time out when trying to use the VNC option in nomachine. The Gnome option works, but creates a new session. I already had that check boxed checked, but thanks.

Any other advice?

Thanks,
Waspinator

---

### Post by WicKeDcHilD on 2010-05-06
Reviving a dead thread but when starting new connections, make sure your old connection is closed completely first. NX doesn't always close properly and so the next time you try to load the program, it times out.

---

