---
title: "share external usb drive with ubuntu"
date: 2010-07-05
forum: General Help
---

### Post by kristo5747 on 2010-07-05
Greetings!

I hope I am the right forum. I would like to know if it is possible to mount remotely and external usb drive with ubuntu.

I finished installing Lucid (Ubuntu 10.04) on two desktop PCs formerly running Windows XP. Both installs went like a charm.

Machine A has an external USB drive connected to it that I previously used for MS Windows backups. I can see the contents of the external drive from A's "file explorer" and navigate its directories.  

I would like to have machine B auto-mount A's external USB drive.

A while back, I did something similar with a RedHat host that would automount a connection to  an external USB drive shared by a MS Windows machine. My "/etc/fstab" was updated to mount a CIFS  share. 

I used CIFS since RedHat does not support NTFS, which is the format of USB drive. It worked perfectly.

Can I do the same thing or is there a simple way? I am thinking that I may need to setup NFS server and client but I am not sure. 

Is there a how-to on NFS and Ubuntu?

I welcome any pointers or suggestions. Thanks.

Al.

---

### Post by gordintoronto on 2010-07-06
The simple way would be to put everything on the external drive into one folder, and share the folder.

---

