---
title: "my laptop cant boot from ubuntu disc"
date: 2010-09-26
forum: General Help
---

### Post by meteors on 2010-09-26
Package: installation-reports  Boot method: CD
Image version: ubuntu-10.04.1-desktop-i386
Date: 1 oct 1600h

Machine: Lenovo T5500
Processor: intel core 2 cpu 1.66ghz 
Memory: 0.99gb ram
Partitions: no

Output of lspci and lspci -n: unsure  Base System Installation Checklist: [O] = OK, [E] = Error (please elaborate below), [ ] = didn't try it  Initial boot worked:    [O] Configure network HW:   [ ] Config network:         [ ] Detect CD:              [E] Load installer modules: [ ] Detect hard drives:     [ ] Partition hard drives:  [ ] Create file systems:    [ ] Mount partitions:       [ ] Install base system:    [ ] Install boot loader:    [ ] Reboot:                 [ ]  Comments/Problems: Left my CD in the cd-drive and proceed to boot computer. Everything works fine till I entered this screen which says:
"BusyBox v1.13.3 (Ubuntu 1:1.13.3-|ubuntu11) built in shell (ash)

Enter 'help' for a list of built in commands.

(initramfs) can not mount /dev/loop0 (/cdrom/casper/filesystem-squaslfs) on //filesystem.squaslifs"


I have retried many times, using different disc, different boot method from the CD menu but consistantly get to this screen.
What can I do?

---

### Post by 0N3 on 2010-09-26
Could be a bad image try burning the image again on the slowest possible speed you can its good practice to do this for all ISO images
Heres a link to 2 ways of installing Ubuntu either by USB Pen drive or CD
[http://www.youtube.com/user/LinuxForDummies?feature=mhum](http://www.youtube.com/user/LinuxForDummies?feature=mhum)

---

### Post by philinux on 2010-09-26
> **meteors said:**
> i have downloaded the iso, burn the image onto a cdr but when my laptop tried to boot from the disc, it ran smoothly only for awhile before consistently going to this black screen which says :

 

what shld i do? my computer not suitable to use ubuntu?

Boot the cd and at the first graphic press any key. A menu appears. Choose Check CD for Defects.

---

### Post by meteors on 2010-10-01
> **0N3 said:**
> Could be a bad image try burning the image again on the slowest possible speed you can its good practice to do this for all ISO images
Heres a link to 2 ways of installing Ubuntu either by USB Pen drive or CD
[http://www.youtube.com/user/LinuxForDummies?feature=mhum](http://www.youtube.com/user/LinuxForDummies?feature=mhum)

did that, same prob even with diff disc

---

### Post by meteors on 2010-10-01
> **philinux said:**
> Boot the cd and at the first graphic press any key. A menu appears. Choose Check CD for Defects.

it leads me to the same screen when i choose check cd for defects

---

### Post by meteors on 2010-10-03
[IMG]http://i52.tinypic.com/2el819g.jpg[/IMG]


no matter wat i do...i alays end up with this screen:(

---

### Post by Quackers on 2010-10-03
I think that may mean that the file system is bad on the disc. Check the MD5 checksum on the download and if correct maybe you could burn the image again. Try a slower setting.

---

### Post by poodoopealeoaph on 2010-10-03
I actually have had this issue with certain computers. This usually happens to me when the cd/dvd drive doesn't have drivers to run in dos. Try using some different external cd drives to see if that may be your issue.

If you do not have any externals and you have a desktop, then try to see if you have some sort of a conversion box. I have one where I plug in a laptop hd and it can be used as a usb drive. This way, you can plug it into your desktop, insert the disk and start install, then install to the laptop drive. After that is installed you should be able to put it back in your laptop and it will boot to your os.

---

### Post by zaphod777 on 2010-10-03
> **poodoopealeoaph said:**
> I actually have had this issue with certain computers. This usually happens to me when the cd/dvd drive doesn't have drivers to run in dos. Try using some different external cd drives to see if that may be your issue.

If you do not have any externals and you have a desktop, then try to see if you have some sort of a conversion box. I have one where I plug in a laptop hd and it can be used as a usb drive. This way, you can plug it into your desktop, insert the disk and start install, then install to the laptop drive. After that is installed you should be able to put it back in your laptop and it will boot to your os.

This shouldn't be the problem there is no DOS here. 

I would probably make a bootable USB stick as it will give you less problems and you probably have a few 1GB flash drives lying around. 

Otherwise try re-downloading the ISO file and burn it at a slow speed some older CDROM drives have trouble reading a disk that has been burned at a higher speed.

---

### Post by meteors on 2010-10-04
> **Quackers said:**
> I think that may mean that the file system is bad on the disc. Check the MD5 checksum on the download and if correct maybe you could burn the image again. Try a slower setting.
[IMG]http://i52.tinypic.com/120rqk6.jpg[/IMG]

tried using other software to burn and got this

is my prob with the iso?

---

### Post by gcbzzzz on 2010-10-21
i'm getting the same error

asus eeepc 1000, all original.

using ubuntu 10.10 netbook iso.

MD5 checks. (btw, i cursed for half an hour while trying to find the hashes. you guys went great lengths to make it as far away from  ubuntu.com as you could)

what else. i downloaded the torrent version. copied to a USB stick using a desktop with ubuntu 10.10 (network upgrade from 10.04)

i used usb disk creator application. erased the disk with it before copying.

will try again running the application as root now and will check for write errors on the log.

---

### Post by gcbzzzz on 2010-10-21
Ha! running the application via console `sudo /usr/bin/python /usr/bin/usb-creator-gtk` it writes the data, start the "writting the bootloader" step, and then close. With a Segmentation Fault.


i would never know that launching the application via the menu. as it stupidly hides every >0 exit code from me....

---

### Post by zaphod777 on 2010-10-21
Hmm it looks like there is a bug report on this you should add your details. 
[https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/547114](https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/547114)

But I would try and purge the application and install it again
```

sudo apt-get purge usb-creator-gtk
sudo apt-get install usb-creator-gtk

```

---

### Post by gcbzzzz on 2010-10-21
solved.

copied the image to a windows box and used universal-usb-installer-1.8

was able to boot the 10.10 installer without a problem.

So the problem for everyone having this error is on the "Start up disk creator" in the existing ubuntu install

---

### Post by zaphod777 on 2010-10-21
Good job as long as you get the job done in the end :-)

---

