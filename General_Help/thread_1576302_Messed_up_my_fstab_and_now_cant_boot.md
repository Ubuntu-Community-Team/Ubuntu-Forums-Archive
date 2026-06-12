---
title: "Messed up my fstab and now cant boot"
date: 2010-09-17
forum: General Help
---

### Post by dadaas on 2010-09-17
Hi,
First let me tell you what i wanted to do, i wanted to copy and paste some website files into my lampp directory and i was denied, then i tryed to chmod directory which was permitted, then i search forums and see that i need to change umask=007 to umask=oooo i did that and reboot and now i cant boot, it wont mount /

tryed to edit fstab with nano but its read only, how can i edit fstab? 
tryed recovery mode and its not working because its stuck saying filesystem could not be mounted: /

please help

---

### Post by sikander3786 on 2010-09-17
Use sudo while editing fstab to get read/write permissions.

---

### Post by dadaas on 2010-09-17
ok ill write what i try
I type sudo nano /etc/fstab

no permission

I tryed everything with sudo and su, but just cant get write permission

---

### Post by wilee-nilee on 2010-09-17
> **dadaas said:**
> ok ill write what i try
I type sudo nano /etc/fstab

no permission

I tryed everything with sudo and su, but just cant get write permission

Go to net root=terminal in recovery and try that. It is the last line on the bottom.

---

### Post by dadaas on 2010-09-17
i dont see net root=terminal recovery, i only have many 10.04 recoverys and none work

---

### Post by dadaas on 2010-09-17
huh i fix it.

Solved by booting from cd and then using terminal and sudeo command for gedit : gksudo gedit /pathtomyfstabfileonhardisk/fstab

and edit it

I will open new topic for my another problem, thanks for help.

---

### Post by wilee-nilee on 2010-09-17
I just noticed you got it fixed that is great.

---

