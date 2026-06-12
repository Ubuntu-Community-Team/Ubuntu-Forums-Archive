---
title: "Recovering files from ubuntu! Please!!"
date: 2012-03-22
forum: General Help
---

### Post by fanny87 on 2012-03-22
Hello, I have a huge problem. First I'll tell you I have ubuntu 11.04 (80%)and windows(20%) on dual boots. I installed ubuntu with wubi through windows {a mistake I'll never do again}.Some time ago I had overheating problems with my laptop and ubuntu stopped working. Now I've made some hardware adjustments but ubuntu still is not working. I need at least to retrive my files.. they're too important.:(

Here's the message I get everytime I try to enter with ubuntu:

GNU GRUB VERSION 1.99- rcl -13ubuntu3
Minimal BASH-like line editing  is supported. For the first word, TAB list possible command  completation. Anywhere else TAB list possible device or fill  completation.
grub> 

Please help me!!!
(sorry for my bad english)

Oh I forgot to say I cancelled the ISO file of ubuntu from windows T_T I am so stupid.

---

### Post by alphaamanitin on 2012-03-22
Easy fix.  Download .iso of any linux.  Burn to disk or make bootable USB drive.  Boot into usb drive or disk, open the drive with your files and copy to a usb drive.

It looks like you need to rebuild your grub.conf though.  There are a bunch of instructions on how do to that.  If I wasn't super lazy I would find you a link.  Sorry.

AlphaA

---

### Post by The Cog on 2012-03-22
You should be able to get at your files using a Linux live CD, and copy them to an external hard drive (or to the C drive if there's enough space). But you have to be able to identify the file that wubi uses for its virtual disk. I have no idea what it might be called or where it might be on the windows drive. 

Once you have found it, you should be able to use a command like
```
sudo mount -o loop path-to-file /mnt
```
and then find the disk contents in /mnt.

Hopefully, someone can tell you where to find the virtual disk file.

---

### Post by Mark Phelps on 2012-03-22
I believe the virtual file is named root.disk.

---

### Post by fanny87 on 2012-03-22
I found root.disk with 'search for files' but it's a file text that can't be open..anyway I copied the path, opened the terminal and writed down the code but..

```
mount: invalid option -- '0'
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
```

the thing is.. where do I find the files?? T_T there's this folder called found.000 I open it and there's another one called 'dir0000.chk' then 2 text files 'root.disk' and 'swap.disk' another folder called boot that contains a folder called grub .. that is empty!!! T_T

---

### Post by bcbc on 2012-03-22
Move dir0000.chk to \ubuntu\disks and wubi will boot.

[http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

From link (assuming ubuntu is on C: ):
```
C:\found.000>move dir0000.chk \ubuntu\disks
```

---

### Post by imachavel on 2012-03-22
now wait a minute, if he pops the live cd in, before 'trying' ubuntu, isn't there a way to run boot repair? This might fix grub. If not then yes, I also recommend reformatting the partitions with g parted(hard to download and install to a cd since it's an .iso and you will be using the cd drive to boot the ubuntu live cd)

BUT if you can reformat, then you can install Linux on one partition, then windows on the other, provided your activation key works twice. Also, which one should the boot flag be set to in /dev/sda? I don't really know. I think gparted will set all that for you though. Now if you can get all of that done, you still need the files? I thought wubi created a virtual drive, not another partition? Weird. If you pop your live cd in there, there should be a folder for the hard drive containing all the files, it will be listed as 'something or another gb file system'

Am I wrong? Well, last resort, buy a usb to sata transfer device, or IDE I'm not sure which hard drive it is, disconnect that bad boy, pop into another computer, and the computer(once it's booted up and OS loaded) will see the drive as a letter considering it's windows, or as a device in the home folder if you are using linux. here is an image of your drive connected the main board interface with a sata cable(if your drive is sata)

[http://www.thg.ru/howto/20051125/images/hdd_sata_connected2.jpg](http://www.thg.ru/howto/20051125/images/hdd_sata_connected2.jpg)

[http://www.officialwindowsmagazine.com/files/old/2008/09/drive3.jpg](http://www.officialwindowsmagazine.com/files/old/2008/09/drive3.jpg)

---

### Post by alphaamanitin on 2012-03-22
Ah, just noticed wubi install.  My advice seems mostly wrong now.

AlphaA

---

### Post by fanny87 on 2012-03-22
So I have to return to windows..?
I don't need to fix ubuntu, I just need to retrieve my files then I think I'll install ubuntu 10.04 without wubi and without windows..
from the link:
```

]So now you look for your root.disk (or other .disk files) and copy them  back to the \ubuntu\disks folder. If the entire \ubuntu\disks folder is  missing, you'll likely find a dir0000.chk directory and within  that the root.disk, swap.disk and empty \boot\grub folders. Copy this  back to \ubuntu renaming the directory to disk
```

so..just to be clear (lol) I need to rename the folder 'dir0000.chk' \ubuntu\disks or do I need to rename the other folder 'ubuntu' which has only 'unistall wubi' and install' ?

---

### Post by bcbc on 2012-03-22
If you just want to loop mount it, use the -o option instead of the -0 (zero) that you supplied (based on the error output you posted).

```
sudo mount -o loop /<mountpoint>/found.000/dir0000.chk/root.disk /mnt
nautilus /mnt/home/

```

That will show you your files which you can then copy.

---

### Post by fanny87 on 2012-03-22
```
ubuntu@ubuntu:~$ sudo mount -o loop /<mountpoint>/found.000/dir0000.chk/root.disk /mnt nautilus /mnt/home/
bash: mountpoint: No such file or directory

```

T_T[FONT=monospace][/FONT]

---

### Post by bcbc on 2012-03-22
<mountpoint> is supposed to be replaced by whatever mountpoint your host partition (the one containing the root.disk) is mounted on. The nautilus command is a separate command once the root.disk is successfully mounted.

e.g. let's say your root.disk is on /dev/sda1
then you would run:
```
sudo mkdir /media/win  # create a mountpoint
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/found.000/dir0000.chk/root.disk /mnt
nautilus /mnt

```

Each line is a separate command that depends on the success of the prior line. Don't continue if you have errors.

---

### Post by fanny87 on 2012-03-22
Thank youu!! I did it.. I mean a new folder opened called mnt..what shall I do now?

---

### Post by bcbc on 2012-03-22
If you successfully mounted the root.disk, under the /mnt directory you should see directories such as boot, etc, home ...
Your home directory will be within /mnt/home/ and you can backup data from there.

When you're done, just unmount the root.disk, then the partition:
```
sudo umount /mnt
sudo umount /media/win
```

---

### Post by fanny87 on 2012-03-22
Thank you so much!:KS
I'm actually moved.. you saved me!! :guitar:

just one last question: there are some folders with an X on it, that I can't open.. how can I ?

---

### Post by bcbc on 2012-03-22
I'm not sure about the X... can you give me an example of the folder name please? Or maybe a screen shot. Is this a data folder you're trying to access in order to back up the contents?

---

### Post by sudodus on 2012-03-23
> **fanny87 said:**
> Thank you so much!:KS
I'm actually moved.. you saved me!! :guitar:

just one last question: there are some folders with an X on it, that I can't open.. how can I ?
I think it can be 
- a folder that you have no permission to open
or
- a link to a folder (and the link is broken)

If you have no permission, try with superuser privileges
```
gksudo nautilus
```

If it is a broken link, the actual folder (or file) could be somewhere else or deleted. The broken link itself does not mean that any file content is destroyed. It is only the link (alias short-cut) that is not working, when you log in from another environment or system.

---

