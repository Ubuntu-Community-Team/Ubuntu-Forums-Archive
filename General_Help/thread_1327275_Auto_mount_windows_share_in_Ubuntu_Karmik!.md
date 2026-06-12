---
title: "Auto mount windows share in Ubuntu Karmik!"
date: 2009-11-15
forum: General Help
---

### Post by Irwin J. Finster on 2009-11-15
Hi,

I am running Ubuntu Karmik Koala, and can successfully mount a Windows share via places/network by entering the correct passwords. Is there an easy way to have this automatically done everytime I reboot the system?

TIA

---

### Post by sisco311 on 2009-11-15
[http://psychocats.net/ubuntu/mountwindows#ntfsconfig]("http://psychocats.net/ubuntu/mountwindows#ntfsconfig")

---

### Post by Irwin J. Finster on 2009-11-15
Thanks for the fast reply. And sorry if I have been not entirely clear, the share I want to mount is not on my PC, but on a NAS.

---

### Post by sisco311 on 2009-11-15
Sorry I missread your first post.

You have to edit the fstab file. [thread=288534]Mount samba shares with utf8 encoding using cifs[/thread] #Permanent mount

---

### Post by Irwin J. Finster on 2009-11-15
Thanks, that worked great!

---

