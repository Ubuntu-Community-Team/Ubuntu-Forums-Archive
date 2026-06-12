---
title: "Problem mounting shared folder-Ubuntu in vBox"
date: 2010-12-11
forum: General Help
---

### Post by whs37 on 2010-12-11
I am running Ubuntu in a Virtual Box under Windows 7. I have defined a shared folder but cannot mount it in Ubuntu. I am not sure whether it is a Ubuntu or a vBox problem. See picture for details:
 
 
 
[IMG]http://i260.photobucket.com/albums/ii36/whs37/HTG25/HTG%2026/2010-12-11_2237.png[/IMG]

---

### Post by karthick87 on 2010-12-11
Have you installed Guest Additions??

Follow this [link for step by step instructions]("http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/").

---

### Post by whs37 on 2010-12-11
> **karthick87 said:**
> Have you installed Guest Additions??
 
Follow this [link for step by step instructions]("http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/").
 Yes, I have the guest additions.

---

### Post by whs37 on 2010-12-14
**The problem is solved**. I applied those commands that worked:

sudo mkdir /mnt/A1Temp
sudo mount -t vboxsf A1Temp /mnt/A1Temp
nautilus /mnt/A1Temp

Thanks to everybody for their assistance.

---

### Post by karthick87 on 2010-12-14
Mark this thread as [COLOR=Red][SOLVED][/COLOR]

---

