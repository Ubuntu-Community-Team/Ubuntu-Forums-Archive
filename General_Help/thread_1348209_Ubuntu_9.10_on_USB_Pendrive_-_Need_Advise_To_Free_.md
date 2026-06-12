---
title: "Ubuntu 9.10 on USB Pendrive - Need Advise To Free Diskspace"
date: 2009-12-07
forum: General Help
---

### Post by chrisqck on 2009-12-07
Hi, 

Recently a friend introduced me to the idea of installing Ubuntu to a pendrive and using it to boot to Ubuntu. Using the guide provided by PendriveLinux.com [here]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/"), I've managed to create a bootable Ubuntu 9.10 pendrive. 

This method has a limitation however on the maximum diskspace available, which is 4GB (due to FAT32 limitation). (The pendrive, however, has 8GB of diskspace so i'm 'wasting' 4GB of diskspace using this method). 

The problem arise when upon 1st logon, i ran the updates and the files took up most of the 4GB allocated to this installation. Now it only have 4.6 MB of free diskspace. 

I would appreciate if anyone can guide me on these tasks below: 

1. Disk cleanup. I am only using this for entertainment purposes like watching movies, listening to music & chatting with friend on Pidgin. Are there any file that i can remove from the system since i won't be needing them ? (or when i DO need them later, i can reinstall them). 


2. I read from another post that there is a way to make use of the remaining 4GB that was not used in the installation process. I've tried searching but since i'm not yet familiar with the syntax of specific search keyword, the results i gets are not what i wanted. Is there a guide somewhere that i can refer to for this type of scenario ? 

The whole purpose of this exercise is to se if I can replace Windows in my PERSONAL day to day computing needs. So far I have been very happy with it. If i can find answers to the 2 questions above, it would be even better. 

Thank you in advance to everyone that helps. :)

---

### Post by Sin@Sin-Sacrifice on 2009-12-07
I have a 250 GB fat32 partition so I don't see why you couldn't just resize that to use the entire pen drive.

---

### Post by chrisqck on 2009-12-07
Sorry if i didn't mention it clearer in my firt post but the guide at pendrivelinux would create a 4GB loop file (HDD). it is not able to create anything larger than 4GB. so any idea what files i can remove to free up more diskspace? thanks.

---

### Post by snowpine on 2009-12-07
I am not familiar with the "Pendrivelinux" method. Maybe it is awesome. :) But their suggestion to use fat32 for Linux (and waste half the drive) makes me skeptical.

Personally, with 8gb, I would simply use the Ubuntu installer (using a single 8gb / partition with the default ext4 filesystem, and being sure to click the Advanced button on the last step to install Grub to the pen drive instead of your internal hard drive). 

There is also an usb-creator application included in Ubuntu (System, Administration, USB Startup Creator), have you given that a try?

My philosophy is to use the built-in Ubuntu tools whenever possible (instead of some random tutorial from a 3rd party website) but that is just my opinion. ;)

ps This command will clear some space by removing your archived packages:

```
sudo apt-get clean
```

---

### Post by chrisqck on 2009-12-08
hi snowpine, thanks for the suggestion. i will try it out soon. (i'll need to burn the iso to cd first though) will update again after i try this out. many thanks! :D

---

### Post by chrisqck on 2009-12-12
hi all, 

i just want to update that the solution is working fine for me so far. i've also done some read up on other ways to keep this installation lean and clean. thanks to all that replied, esp. snowpine :)

---

### Post by efflandt on 2009-12-12
Use tmpfs for your /tmp, so small files used to keep track of things that are deleted next boot use RAM instead of flash.  Example used by bootable USB live/install iso for /etc/fstab:

tmpfs /tmp tmpfs nosuid,nodev 0 0

---

### Post by chrisqck on 2009-12-12
hi efflandt, 

thanks for the suggestion. googling "tmpfs howto" i came across this instruction below: 

```
sudo gedit /etc/fstab and add the line:

   tmpfs <dir> tmpfs rw 0 0

 where dir is the directory you made for the tmpfs
```


here's the content of my fstab file : 

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=cc041d1b-4a7c-48b4-8152-235ae716052e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ca5df55a-f652-4d98-b6f4-e3d6bd802705 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

note: /dev/sdb is the 8GB pendrive. 

so what i need to do now is add the line that you have given at the bottom most line,rite? ```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=cc041d1b-4a7c-48b4-8152-235ae716052e /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=ca5df55a-f652-4d98-b6f4-e3d6bd802705 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
[COLOR="Red"]tmpfs /tmp tmpfs nosuid,nodev 0 0[/COLOR]
```

is this correct or do i have to amend anything?  

i'm new to the linux environment but i am familiar with editing config files in the Windows environment so if you could guide me, it would be much valuable experience. thank you in advance :)

---

