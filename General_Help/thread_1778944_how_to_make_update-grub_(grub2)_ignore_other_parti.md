---
title: "how to make update-grub (grub2) ignore other partions/distros ?"
date: 2011-06-09
forum: General Help
---

### Post by interzoneuk on 2011-06-09
Hi.

I generally have at least 4-5 distro's installed at one time - I always install grub to the boot partition of other distros -that was I control grub from the individual distros - I use ubuntu's grub as the default boot loader.

I prefer to use 
---------------------
set root=(hd0,msdosx) 
chainloader +1
---------------------

Rather than the method that ubuntu uses with the update-grub

I normally edit the grub.cnf file to add other distros but when  update-grub launches it also adds links in grub.

How can I prevent the upadte-grub script automatically adding lines for other distros

i.e - I just want it to add ubuntu entries and ignore other partitions.

Is this possible?

Cheers

---

### Post by hhh on 2011-06-09
What happens if you remove the package os-prober (and os-prober-udeb if it's installed), set up your grub configurations and then run sudo update-grub?

---

### Post by drs305 on 2011-06-09
Add this to /etc/default/grub:
```

GRUB_DISABLE_OS_PROBER=true
```
Save the file, then:
```
sudo update-grub
```
The other way to do it is to make /etc/grub.d/30_os-prober unexecutable, but the other method is preferable.
```
sudo chmod -x /etc/grub.d/30_os-prober
```

---

### Post by oldfred on 2011-06-10
Add entries to 40_custom:
gksudo gedit /etc/grub.d/40_custom
Turn off os-prober:
gksudo gedit /etc/default/grub
After any change to grub's files ( I still forget this):
sudo update-grub

Debian based using grub2 have links to the most current kernel in the / (root). Grub2 does not like to be installed to a partition boot sector, but if the install used grub legacy you can still install it to the PBR. Grub2 format is somewhat different than grub legacy was.

from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

I chain to other MBRs or partitions with grub2 entries like this , boot drive is always hd0 which adds some confusion on drive numbers as sda is always sda:
menuentry "9.04 on sdb (from sdc) Chainboot" {
set root=(hd2)
chainloader +1
}

menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

---

### Post by idoitprone on 2011-06-10
Note: screw up and you will not get an bootable system and you wll have to chroot and etc

patch grub2 make an partition skip
[http://www.linuxquestions.org/questions/linux-software-2/grub2-skipping-one-partition-from-os-detection-741100/](http://www.linuxquestions.org/questions/linux-software-2/grub2-skipping-one-partition-from-os-detection-741100/)

might not work with new grub, so i do not know right now

---

### Post by interzoneuk on 2011-06-11
Thank you for all your responses !

I shall try disabling os-prober - I'm pretty accustomed to chroot'ing, etc anyway I used to run Gentoo as my main system..

Cheers

---

### Post by tealio on 2012-04-08
sorry to revive such an old post, but my issue fits with this thread.

Initially i had ubuntu on a USB flash mem stick, and had disabled 30_os-prober, because if the UBS isn't inserted the computer boots windows, if it is, it boots ubuntu from the stick.  Simple.  Now i want to complicate things.

I've added debian to the stick, and i'd like ubuntu's grub to be the master for the stick.  If i enable 30_os-prober, windows will be found on the HD.  If not, i have to make a custom menuentry each time i update the kernel.  Is there a way to make 30_os-prober only probe partitions on the same device on which it resides?

PS- What does it mean if i just tried to end this post by pressing CTRL-X ?

---

### Post by oldfred on 2012-04-08
See post #4.

Ranch Hand's suggestion boots a partition, so it always boot the most current kernel as the link is automatically updated. Leave os-prober turned off and add entry for correct partition to 40_custom.

---

