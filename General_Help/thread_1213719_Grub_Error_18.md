---
title: "Grub Error 18"
date: 2009-07-15
forum: General Help
---

### Post by mganesh30 on 2009-07-15
I have Ubuntu 9.04 installed alongwith WIN XP. For about 2 weeks, both were working fine. But yesterday when starting I got an error "GRUB loading ......waiting. Error 18" I cannot even boot into Windows.
 
Today when I started, I got the Bootloader screen and I could start Windows & Ubuntu. But again after shutting down, same error.
 
Is there any problem with my HDD? will it be a good idea if I switch to Ubuntu completely and not have Windows at all?
 
Please help.

Regards
Ganesh

---

### Post by Screwdriver0815 on 2009-07-15
> **mganesh30 said:**
> I have Ubuntu 9.04 installed alongwith WIN XP. For about 2 weeks, both were working fine. But yesterday when starting I got an error "GRUB loading ......waiting. Error 18" I cannot even boot into Windows.
 
Today when I started, I got the Bootloader screen and I could start Windows & Ubuntu. But again after shutting down, same error.
 
Is there any problem with my HDD? will it be a good idea if I switch to Ubuntu completely and not have Windows at all?
 
Please help.

Regards
Ganesh

normally from my experience, the Error 18 comes up when the Bios is old and can not read harddisks which are bigger than 40 gigabytes and the Ubuntu partitions are located "behind" these 40 gigabytes.

But when it worked before in your setup and it still randomly works, the harddisk has most likely a damage. 

You could try to only install one operating system. Then it should work because all the data which are required for booting this system are located in the first tracks on the harddisk.

maybe this [http://ubuntuforums.org/showthread.php?t=11764](http://ubuntuforums.org/showthread.php?t=11764) helps too.

---

