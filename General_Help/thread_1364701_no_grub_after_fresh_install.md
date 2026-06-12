---
title: "no grub after fresh install"
date: 2009-12-26
forum: General Help
---

### Post by gisler87 on 2009-12-26
hi, i just recently did a fresh install of 9.10 on my laptop. There is no other OS on the laptop either. When it boots up though it says no operating system found. I can boot up the linux install if i have the live cd in and select boot from hard disk. I can't figure out why grub is not loading. Also i am not sure if this is any help but there is only one hard drive. 

thanks

---

### Post by john newbuntu on 2009-12-26
Perhaps you set up grub on a different partition and not the MBR.  Boot from the liveCD and follow step 13 from this link:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by gisler87 on 2009-12-26
I will have a look at the url. 
 
Quick question, when i installed ubuntu i simply selected use entire disk drive. Shouldn't grub by default install in the mbr?

thanks.

---

### Post by john newbuntu on 2009-12-26
The choice of where GRUB needs to be installed is available towards the end of the install via a button called advanced.  I think MBR is the default but I am not a 100% sure.

---

