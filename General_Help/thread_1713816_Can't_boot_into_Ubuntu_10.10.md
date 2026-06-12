---
title: "Can't boot into Ubuntu 10.10"
date: 2011-03-24
forum: General Help
---

### Post by artemeas on 2011-03-24
couple of days ago after I tied some new plymouth theme and did:
update-initramfs -u -k all
update-grub2

I saw this:
Generating grub.cfg..............
Found Windows 7 (loader) on /dev/sda
done

than I restarted to see the new theme...
but in grub I saw only Win 7................

the whole day (today) I tried to boot ubuntu, to reinstall grub via live-usb.
I can boot into ubuntu by:
grub> insmod part_msdos
grub> insmod ext2
grub> set root=(hd1,msdos6) ; /dev/sdb6 = /boot (pressing tab gives me uuid's...)
grub> linux /vmzlinuz-2.6.35-28-generic root=UUID=<uuid of /dev/sdb8 = / > single
grub> initrd /initrd.img-2.6.36-28-generic
grub> boot

then I go into root prompt. because "ro quiet splash" hangs my laptop right after THE NEW PLYMOUTH THEME I INSTALLED COUPLE OF DAYS AGO...
so from root console.. I log into my account login: artem
then I do: startx 
and laptop hangs

from the console I can do sudo update-initramfs -u -k all
it regenerates 3 images in /boot/ - initrd.img-2.6.35-22, initrd.img-2.6.35-27 and initrd.img-2.6.35-28
then I do update-grub2
and it founds ONLY windows 7

I wanted to reinstall grub but I can't connect to the wi-fi (wpa2) from the root prompt..

Please help me

---

### Post by Hedgehog1 on 2011-03-25
artemeas,

This is an interesting pickle you have found yourself in.

Please boot off your LiveCD/LiveUSB, select TRY

Determine what partition holds your Ubuntu root.  In the examples below, they assume that /dev/sd**a5** is your Ubuntu partition.  Yours may be /dev/sd**b5** or /dev/sd**a3** or /dev/sd**b3** or whatever...  Use that.  Also note that your drive MAY be /dev/sd**b**.

In the Terminal (Menu to: Applications >> Accessories >> Terminal):

```
sudo mount /dev/sd**a5** /mnt
```
```
sudo grub-install --root-directory=/mnt /dev/sd**a**
```

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-25
There is an alternate method to do this as well:

To reinstall Grub on Hard Drive from LiveCD/LiveUSB:

Please boot off your LiveCD/LiveUSB, select TRY
In the Terminal (Menu to: Applications >> Accessories >> Terminal), copy and paste these one at a time:
  
 ```
sudo mount /dev/sd**a5** /mnt && sudo mount -o bind /dev /mnt/dev && sudo mount -o bind /dev/pts /mnt/dev/pts && sudo mount -o bind /proc /mnt/proc && sudo mount -o bind /sys /mnt/sys && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
``` ```
grub-install /dev/sd**a**
``````
update-grub
``````
exit
```                                  ```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt
``````
sudo shutdown -r now
```

***The Hedge***

:KS

---

### Post by artemeas on 2011-03-25
I tried everything you posted above before I created that thread :))

I did also:

sudo mkdir /mnt/boot
sudo mount /dev/sdb8 /mnt
sudo mount /dev/sdb6 /mnt/boot
sudo mount /dev/sdb7 /mnt/home
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /
sudo chroot /mnt

root@ubuntu: I did (as well as in the root console of the real system (after booting via grub> boot) ):
update-initramfs -u -k all
it recreated images in /boot
than I did update-grub2 and it found only win 7 right as it did in ubuntu single (repair) mode.

I was tired of that grub errors and did so:
chroot /mnt from live-usb
sudo cp -r /etc/apt /home/artem/Documents/apt_back — to backup all the ppa's I used
sudo dpkg --get-selections > /home/artem/Documents/apps.txt — to backup all the apps I installed via ppa's
then I reinstalled ubuntu and formated (sdb6 = /boot and sdb8 = / )
20 mins later I booted into old-new kernel 2.6.35-22 and started update-manager and then did:

sudo dpkg --set-selections < /home/artem/Documents/apps.txt
sudo apt-get -y update
sudo apt-get dselect-upgrade

— to restore/reinstall apps I had before :)

---

### Post by Hedgehog1 on 2011-03-25
I find myself wondering if you should really be giving the help rather than asking for it.  **Your solution is very nice!**

I am glad you are operational again.

***The Hedge***

:KS

---

