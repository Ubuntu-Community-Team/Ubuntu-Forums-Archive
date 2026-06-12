---
title: "Auto load insmod modules at boot."
date: 2010-03-18
forum: General Help
---

### Post by Hoso001 on 2010-03-18
I need to run to terminal commands at boot to get my wireless card working, the included drivers with ubuntu dosen't work for my card so I compiled my own broadcom drivers.  I am on 9.10 ubuntu.


I need these commands ran at boot in order for my wireless to work.


#sudo modprobe lib80211 

#sudo insmod wl.ko


I have done these commands as per the readme included with the source files.


# load driver as described above
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless 
# depmod -a


No dice,



Any advice?


Hoso001

---

### Post by l4zy on 2010-03-18
Hey. 

You can edit your /etc/rc.d/rc.local file by adding commands there, so they will get loaded on boot or you can make shell-script which you add in to /etc/rc... so it will run on boot, you can choose run level and so on. 

or you can edit /etc/modules so your modules will get loaded on boot.

---

### Post by Hoso001 on 2010-03-18
Thanks, got it working.. My problem is, I didn't realize I had to recopy my driver over after kernel updates.

---

