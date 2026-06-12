---
title: "Help installing Windows 95 in Qemu"
date: 2006-05-05
forum: General Help
---

### Post by egghead3 on 2006-05-05
I'm trying to install windows 95 in qemu so I can play an old game.  I followed this guide to get qemu installed and everything seems to be working.

[http://ubuntuforums.org/showthread.php?t=154265&highlight=qemu]("http://ubuntuforums.org/showthread.php?t=154265&highlight=qemu")

I was successfully able to install windows 98 (which turned out not to be old enough to play my game), so I am fairly confident qemu is installed properly.

Trying to install Windows 95 is giving me difficulties however. These seem to stem from the fact that the cd is not bootable, you instead need a boot floppy. I acquired a floppy image from [www.bootdisk.com](www.bootdisk.com), and have successfully gotten qemu to boot from the floppy image. I then cd to the Windows 95 installation disc and attempt to run "setup.exe." When I do so, I get the following error.

```
Cannot create a temporary directoy.
If you have HPFS or NTFS installed on your hard drive, you will need to create an MS-DOS boot partition to set up windows
```

I had used the instructions given in the above tutorial to create the disk image for windows.

```
qemu-img create hd1.img 1000M
```

Prior to linux, I have always been a mac user, and never dealt with boot floppies or any problems of this sort. I am not sure if the problem lies with how I am creating the hard drive image in qemu (or how qemu formats it), or if it is just my lack of knowledge at how to install windows (MS-DOS boot partition?).

Has anyone successfully installed windows 95 in qemu? Looking around the internet for help, it is claimed to be possible, but everyone in practice seems to go with 98, win2k, or xp.

---

### Post by yabbadabbadont on 2006-05-05
Once you have booted the floppy image, you will need to run fdisk and partition the hard drive.  (the virtual disk)  You will need to restart the virtual machine again after that so that the boot disk will see the newly partitioned drive.  Now that you have booted the floppy image again, you need to use the format command on the newly created C: drive.  You should then be able to run the win95 setup program.

EDIT: also, you needed to tell qemu-img to use the vmdk format when created your image...

Take a read through this:  [http://ubuntuforums.org/showthread.php?t=84275&highlight=howto+vmware+player](http://ubuntuforums.org/showthread.php?t=84275&highlight=howto+vmware+player)

---

### Post by egghead3 on 2006-05-05
I seem to be getting closer. Linux qemu is not capable of producing an image in the vmdk format, hence they are using win qemu under wine. I am not entirely clear as to why the raw format wont work; certainly it was fine with win 98.

Running fdisk in the bootdisk DOS environment allows me to format the image to a primary DOS filesystem. However, when I then run setup off the cd, I get an error about the size of the partition.

```
Setup requires 7340032 bytes available on your c: drive
```

I had allocated a gig for the partition, so this should be fine. I tried formatting the entire partition as primary DOS, as well as just a small part to leave free space. Neither worked...

---

### Post by yabbadabbadont on 2006-05-05
I don't know about older versions, but the current qemu-img under linux has no problem creating a vmdk image.  I don't have any suggestions about the other problems.  I never installed Win95 in vmware, just Win98 and above.  I did have to use a boot floppy for Win98, but I didn't run into your problems.

By the way, this all started because you said that you wanted to install a game.  The last time I checked, vmware doesn't support DirectX inside the virtual machine.  (I think there are some experimental settings, but that's it)  If your game worked with Win95, it might be a good candidate for running under WINE in Linux.  WINE does at least have *some* DirectX support.  For DOS games, there are DosBox and DOSEmu you can try.

---

### Post by egghead3 on 2006-05-06
I was able to format the drive to vmdk, but am still getting that memory error. However, I have been trying to install and run in qemu, without using vmware player (there doesn't seem to be anything wrong with this approach theoretically). I guess I will have to try setting up vmware. 

I attempted to use wine to play my game, but it doesn't seem to want to work. I'm not concerned about Direct X support; the game is warlords II and certainly doesn't need anything like that. I am going to try running it in one the DOS emulators you suggested.

---

