---
title: "Installed Ubuntu along side Windows... Unable to Mount C drive or see C drive"
date: 2010-11-25
forum: General Help
---

### Post by ve2 on 2010-11-25
I installed Ubuntu on my machine. I'm unable to mount or see or even browse the windows portion of the drive. Any suggestions??;)

---

### Post by pawhtiobo on 2010-11-25
Hi :)

The easyest way is to install ntfs-config from Synaptic and enable R/W support for NTFS and choose the mount points.

[IMG]http://avi.alkalay.net/articlefiles/2007/11/ntfs-config.png[/IMG]

See ya...

---

### Post by WorMzy on 2010-11-25
What does fdisk report?

Open a terminal and run
```
sudo fdisk -l
```
(That's a lowercase L, not a one.)

---

### Post by ve2 on 2010-11-25
I installed Ubuntu within Windows... Now I feel DUMB!!! I dont think I can see the windows files... I tried the NTFS tool and it does not start up... I don't see anything relating to a partiton...

---

### Post by pawhtiobo on 2010-11-25
Ahh ok... you used Wubi to do the instalation whitin Winodws...I never tryed it that way, so i can't assist you in much :confused: to help you solved your problem, sorry...


See ya...

---

### Post by ve2 on 2010-11-25
Not a problem. I should of installed it the proper way....:(

---

### Post by linux-hack on 2010-11-25
Why not dualboot it with windows ... you don't need so much space tu run ubuntu ...

---

### Post by pawhtiobo on 2010-11-25
You can always go to add/remove programs and remove the Ubuntu install and start over :). Any help you need the community is here ;).

See ya...

---

### Post by WorMzy on 2010-11-25
The partition on which you installed the root.disk for Wubi is mounted under /root

But I'd recommend installing Ubuntu properly anyway, if that option is available to you. :)

---

