---
title: "GRUB recovery"
date: 2010-05-15
forum: General Help
---

### Post by amite on 2010-05-15
i have double boot on my system(windows 7 and ubuntu9.10).

i made a new windows partition in windows7 by dividing an existing partition. but after that when i booted my system GRUB  was not loading and gave some message that system can't locate grub:confused:.So to at least boot my system i install windows7 by replacing previous windows 7.Now i can't access ubuntu .

the grub version which was installed on my system is GRUB 1.97~beta and now i lost my ubuntu9.10 cd but i have ubuntu 9.04 cd.Please tell me how can i recover grub.

---

### Post by rubs93 on 2010-05-15
I have the same problem :( Try to reinstall GRUB than ad ubuntu to the GRUB menu in Windows 7. I hope it works ;)

---

### Post by amite on 2010-05-15
since i haven't ubuntu 9.10 live cd so tried to bind grub with ubuntu9.04 live cd.
so tried with following command lines:
sudo mount /dev/sda5  /mnt 
sudo mount --bind /dev  /mnt/dev      //this gave message /mnt/dev not found
sudo mount --bind /proc  /mnt/proc    //this gave message /mnt/proc not found
grub-install /dev/sda


with above lines i recovered grub with live cd of ubuntu 9.10 but not this time(with ubuntu9.04).Please tell me how can i recover grub and why with 9.04 above lines didn't work..........
Thanks

---

### Post by mgman on 2010-05-16
Since installing Win7 I've tried installing grub on the MBR using several of the recommended methods. 

Win7 boots without giving me the option of booting Ubuntu each time.

I can use the cd to access Ubuntu partition but that's all.

---

