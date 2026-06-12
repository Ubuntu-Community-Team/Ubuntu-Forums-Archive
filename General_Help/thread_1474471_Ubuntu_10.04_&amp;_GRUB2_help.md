---
title: "Ubuntu 10.04 &amp; GRUB2 help?"
date: 2010-05-06
forum: General Help
---

### Post by edekba on 2010-05-06
So i was running 9.04/GRUB before and decided to install 10.04LTS cleanly. Everything was fine and dandy and ubuntu/grub2 worked w/o a hitch. When I tried to select my WinXp Partition however is when I started to run into issues. When I select the winXp partition, grub just goes blank and returns me back to the grub menu w/o booting or anything. I've tried a few things ([https://wiki.ubuntu.com/Grub2#Dual-booting](https://wiki.ubuntu.com/Grub2#Dual-booting)) / reruning update-grub / ([https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)) but all seem to not affect anything.

When I run 'sudo update-grub' this is what i get. [ [http://pastebin.com/xVQf791B](http://pastebin.com/xVQf791B) ]

My /boot/grub/grub.cfg is [ [http://pastebin.com/C1aqTqwi](http://pastebin.com/C1aqTqwi) ]

---

### Post by marcusjames on 2010-05-06
try to do 
[COLOR=Red]sudo install-grub /dev/sda[/COLOR]

---

### Post by dino99 on 2010-05-06
when you install grub2, it might be installed into the ubuntu mbr partition, not over the windows bootloader.

see info below in signature

run: sudo grub-mkconfig && update-grub

---

### Post by edekba on 2010-05-06
Hmm okay i tried both and read through the link and tried to restore the winxp bootloader as i thought that was the problem ....

Instead of looping back to the grub menu i get this

error: unknown filesystem.
grub rescue>

---

### Post by dino99 on 2010-05-06
so you have to reinstall grub2 on ubuntu partition ( have to know its name: /dev/sd?, "?" is a letter followed by 1), if you dont know it exactly run gparted or partedmagic from cd or usb stick.

If you think that is too complex, you have choice to reinstall ubuntu again (with the "alternate" which let you choose how to install), or try to repair that one.

To repair you need to boot and follow this thread: [http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)  with your real path. When done, run:

sudo grub-install --root-directory=your-ubuntu-partition-path (ie /dev/sd?)

sudo grub-mkconfig && update-grub

---

### Post by edekba on 2010-05-06
tried to reinstall the winxp w/o the cd as it wouldnt give me the repair option and that just didnt let me boot anything, so i had to reinstall the ubuntu bootloader using this ( [http://ubuntuforums.org/showpost.php?p=6391959&postcount=1](http://ubuntuforums.org/showpost.php?p=6391959&postcount=1) ). Got my 10.04 working again.

I tried to reinstall previously but w/o doing alternate. Not sure i even saw that option, but I will look again in the morning, as this is a fresh install i see no harm in wipe.clean again. + looking @ the link you posted looks a lot harder than reinstalling. 

thanks Dino, will try in the morning.

---

### Post by Jerubaal on 2010-05-06
> **edekba said:**
> Instead of looping back to the grub menu i get this

error: unknown filesystem.
grub rescue>

I got this after trying to clean up my excess partitions. 

I also had messages about the partition not existing. This appears to be because the partitions were renumbered when I deleted some unused partitions. :oops: I then did a clean install on a new drive but still had to change the bios disk boot order around to find which drive had the correct grub... My pc's BIOS often resets itself as to which drive should boot first :mad:

---

### Post by edekba on 2010-05-06
Hmm shoot something serioussly is wrong. I tried to reinstall and now ubuntu's installer cant find my windows partition when im specifying where to install. It thinks that sda doesnt have any partitions on it whatsoever.

---

