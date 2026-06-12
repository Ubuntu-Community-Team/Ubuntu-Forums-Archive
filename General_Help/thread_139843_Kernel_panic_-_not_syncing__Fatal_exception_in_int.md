---
title: "Kernel panic - not syncing : Fatal exception in interrupt"
date: 2006-03-04
forum: General Help
---

### Post by scythe72 on 2006-03-04
Hi, I am not sure who can help me out with this since this is the first time I am encountering this error on Linux.

I have recently installed Kubuntu 5.10 and performed the following:
1. Updated all the packages
2. Installed the openssh package
3. Installed the latest Bittorrent packages
4. Installed the Samba package
5. Recompiled and installed an updated DSDT.aml into /etc/initramfs to repair
errors in the default DSDT.

However, I notice that during periods of high disk activities (Bittorrent and Samba), the system would crash with the error in the jpg file attached.

Do hope that someone would help me out to id/solve this problem. Hope its not a hardware error :(

---

### Post by m4v1s on 2006-11-14
I have been getting that same error, I am running 6.06 LAMP. I have not concluded that it is due to disk activity since this happens to me, seamingly, at random. Any suggestions are apreciated, Thanks.
Aaron.

---

### Post by AgenT on 2006-11-15
Assuming that the kernel giving you problems is 2.6.17-10-generic (x86). Assuming your root partition / is on /dev/hda1.

NOTICE: Instructions below say to use su, if this fails, use sudo with the next line below the su command instead like so: sudo mkdir....

Boot your favorite Debian (based) LiveCD and start a terminal then (Knoppix is always reliable):
```
su -
mkdir -p /media/ubuntu
mount /dev/hda1 /media/ubuntu
chroot /media/ubuntu
```Now do a test:
```
echo "bbb" < /dev/null
```If you do not receive an error, continue. If you do receive an error, something is wrong with your permissions. Make sure you were root before you executed chroot!
```
apt-get update
apt-get install --reinstall linux-image-2.6.17-10-generic
exit
cd /
umount /media/ubuntu
shutdown -r now
```Reinstalling the linux-image package not only reinstalls all the files, but also updates a lot of programs that may be causing the kernel panic.

---

### Post by Xaviar on 2006-12-06
I am getting exactly the same error trying to install Kubuntu 6.06 LTS from the Live CDs I got through the mail.  My hardware is all new and has no problems with XP but all 5 Kubuntu CDs produce the same error and I cannot install it at all.

---

### Post by ghat on 2006-12-15
HI

The chroot stuff would work if the /boot is on the same partition as /

I have the following partitions
/dev/hda1 => 250MB /boot
/dev/hda2 => 64GB windowsXP
/dev/hda3 => extended
/dev/hda5 => 8GB /
/dev/hda6 => 2GB swap

I can mount / as specified above but my /boot does not get mapped correctly how do 
I fix the same  problem 


Ghat

PS: I am using Edgy-Xubuntu...

---

### Post by unimatrix on 2008-02-21
Bump!

Same problem here, though I think I've figured out what's wrong.
Apparently one of my RAM cards is broken.. At least memtest86+ says so.
But I'd like to see this confirmed.

---

