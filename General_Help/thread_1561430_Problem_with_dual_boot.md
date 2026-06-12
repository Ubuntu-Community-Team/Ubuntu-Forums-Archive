---
title: "Problem with dual boot"
date: 2010-08-26
forum: General Help
---

### Post by jakewoble on 2010-08-26
Hi,
I'm running ubuntu for a while, and I decided to dual boot it with windows XP.
After creating a new partition with the GParted boot cd, I've inserted the XP installation disk. When rebooting, I get an error message that says:

a problem has been detected and windows has been shut down to prevent damage to your computer.
... run CHDISK, check for virusses, ....
STOP: 0x0000007B

I think a total format is necessary? 
Thanks in advance.

---

### Post by Mark Phelps on 2010-08-26
You should first do what it says -- boot into your XP CD, in command mode, and run CHKDSK.  If that doesn't fix it, more drastic measures may be needed.

---

### Post by brr872002 on 2010-08-26
> **jakewoble said:**
> Hi,
I'm running ubuntu for a while, and I decided to dual boot it with windows XP.
After creating a new partition with the GParted boot cd, I've inserted the XP installation disk. When rebooting, I get an error message that says:

a problem has been detected and windows has been shut down to prevent damage to your computer.
... run CHDISK, check for virusses, ....
STOP: 0x0000007B

I think a total format is necessary? 
Thanks in advance.

pl. post out put
code 
sudo fdisk -l  /dev/sda

---

