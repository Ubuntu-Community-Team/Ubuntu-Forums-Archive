---
title: "Personal File Sharing"
date: 2012-08-15
forum: General Help
---

### Post by dln9 on 2012-08-15
Machine A:  Ubuntu Lucid 10.04 32 bit

Machine B:  Ubuntu 12.04 32 bit


Using "Personal File Sharing" (gnome-user-share), I wish to access the public folder on machine B while working on machine A.  On machine A I can see the icon for the public folder on machine B, but whenever I double click on that icon, I get this error message:  


"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"


I don't know what this is telling me, nor what I ought to do.  

I appreciate any help people can provide.

---

### Post by Perfect Storm on 2012-08-15
Thread bump.

---

### Post by Bucky Ball on 2012-08-15
Are the permissions correct for the folder on B and set up to share?

---

### Post by dln9 on 2012-08-16
> **Bucky Ball said:**
> Are the permissions correct for the folder on B and set up to share?

Yes, they are set up for "create and write", which is what I want.

---

### Post by Bucky Ball on 2012-08-16
Does Nautilus share by FTP or Samba? I don't use it, use FTP and Filezilla for all file sharing on the LAN, so don't know. I'm wondering, if it needs Samba, whether you have Samba installed on both machines correctly or at all (seems like it is installed on one so you can see the public folder). 

Plug this into a search engine:

ubuntu DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

... and:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

... and you will get some leads. I did. ;)

This one might be of help:

[http://forums.cnet.com/7723-6617_102-534423/can-t-open-network-shares-in-linux/](http://forums.cnet.com/7723-6617_102-534423/can-t-open-network-shares-in-linux/)

Some ideas further down this page also:

[http://ubuntuforums.org/showthread.php?t=1036024&page=5](http://ubuntuforums.org/showthread.php?t=1036024&page=5)

---

