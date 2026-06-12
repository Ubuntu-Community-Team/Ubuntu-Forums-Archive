---
title: "Computer won't boot"
date: 2010-01-09
forum: General Help
---

### Post by kman269 on 2010-01-09
Today I was messing with my partitions (probably a really bad idea for me) and I messed something up. I took a screen shot of my GParted to show my partition set up.
[IMG]http://i759.photobucket.com/albums/xx237/kman269/Screenshot--dev-sda-GParted.png?t=1263094650[/IMG]
basically I shrunk the sda1 down to about 50GiB. I then deleted the partition at the very end (there is now unallocated space there.) It was called HP SETUP and was FAT32 I believe. My understanding of it was it included some information about my hardware (I think it  only matters to windows.) I then rebooted my computer to see if the windows partition still worked and it wouldn't boot. I used plop boot manager and was able to select the windows partition to boot from and it worked fine. However, when I selected my ubuntu partition my computer wouldn't boot from it. I pulled out my live CD to see if I could figure anything out and saw that the extended partition had expanded to include the new free space created by resizing my windows partition. I then resized that back to include just the sda5 and linux-swap partitions and resized the windows partition back to its original size. That is how I got to the state I am at right now and it obviously still will not boot. I can however still mount the partitions and view all of my old data so I now there wasn't any damage to that. I am thinking that it will be fairly easy to fix this and I could probably do this on my own if I new what to search for but "computer won't boot" is a bit big of a category.

So if there is a simple way to make my hard drive bootable again, you don't need to go into too much detail, but if it is intermediate to advanced, step by step would be appreciated. 

Also I have an external hard drive so I can use that to store all of my data if I need to do some reinstall thing.

---

### Post by Jackzor on 2010-01-10
Easiest thing that I can think of is backing up and reinstalling.... 

Thats just what I would do though. I'm sure there is a better fix.

But if you want to get it running right now.. I'd back it up and format it.

---

### Post by blueridgedog on 2010-01-10
You can try and reinstall grub.  What version of Ubuntu to you have?  The process is different based on pre-9.10 or 9.10 users.

---

### Post by oldfred on 2010-01-10
Windows does not like to be resized partituarly Vista & 7. XP is usually ok with gparted.

Generally you need to boot the windows cd/dvd and run the repairs. Instructions are slightly different for XP and vista/7.


How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently)

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.htm)

Hi there, dont worry, boot from Windows 7 dvd and select repair your computer at the Install Now screen.
Run Startup repair thrice and reboot.

---

### Post by kman269 on 2010-01-11
I'm going to try reinstalling grub. I'm hoping I can get it without too much help but if you guys want to post something else about it that requires the versions I have, I have ubuntu 9.10 and windows xp

---

### Post by Leppie on 2010-01-11
booting with the karmic livecd, you should be able to re-install grub2 easily:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```
that should do the trick.

---

### Post by kman269 on 2010-01-11
just tried the instructions at [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708) and got nothing. I will try the suggestion from Leppie which adds the --recheck but I can't help but thinking it is trying to boot from the extended sda2 partition instead of sda5.

---

### Post by Leppie on 2010-01-11
if that doesn't work, please [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt

---

### Post by kman269 on 2010-01-11
sorry it took so long but here are the results from boot_info_script047.sh

---

### Post by Leppie on 2010-01-11
ok, you are one of the few who get a mixed grub/grub2 environment.
try the following:
```
sudo bash
mkdir -p /mnt/temp/boot
mount /dev/sda6 /mnt/temp/
mount -o bind /proc /mnt/temp/proc
mount -o bind /dev /mnt/temp/dev
mount -o bind /dev/pts /mnt/temp/dev/pts
mount -o bind /sys /mnt/temp/sys
chroot /mnt/temp
apt-get purge grub grub-pc grub-common
apt-get install grub-pc grub-common
exit
```
this should completely remove both grub legacy and grub2 from your system and then install grub2.

---

### Post by kman269 on 2010-01-11
I got this error...

```
ubuntu@ubuntu:~$ sudo bash
root@ubuntu:~# mkdir -p /mnt/temp/boot
root@ubuntu:~# mount /dev/sda6 /mnt/temp/
/dev/sda6 looks like swapspace - not mounted
```when I looked into it, it looked as if you can't mount the swap and it said the best thing I could do is use swapon. what should I do that or is there something else I need to do?

---

### Post by Leppie on 2010-01-11
if you don't have anything important on your ubuntu system, re-install it.
or try testdisk to see if you can recover your sda5:
```
sudo apt-get install testdisk
sudo testdisk
```
more information on testdisk here: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by kman269 on 2010-01-11
okay. I think I will do that.

---

### Post by kman269 on 2010-01-12
test disk didn't help but as I was reinstalling, I had the idea of just installing ubuntu over my windows partition which I honestly didn't care about and then when I booted that up it listed my old ubuntu stuff under other operating systems were I was able to load it and retrieve all of those files that I didn't have permission to view earlier.

---

### Post by MoRoBoShi on 2010-01-12
Hi all,
I very briefly take a look to this thread....it seems you miss a boot flag to the partition you need to boot.

---

