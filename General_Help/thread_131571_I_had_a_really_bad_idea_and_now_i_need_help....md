---
title: "I had a really bad idea and now i need help..."
date: 2006-02-16
forum: General Help
---

### Post by kgee on 2006-02-16
O.K. so. I have a really funny story about how much of a noob I really am.

I was trying to install DSL onto my flash drive. Since I have little experience with linux, I decided a tutorial would be helpful. The tutorial I found seemed very thorough, and I was in the middle of the part where I partition the flash drive when the instructions went something along the line of: 

sudo sfdisk /dev/sda

Against all my knowledge of how sda was my SATA drive with Ubuntu loaded on it, I decided to trust the tutorial. For some reason, no matter what I did to the usb drive, this command always threw an error, saying the disk was still mounted. I eventually gave up.

Now I was having a program conflict with my sound, and I decided I would reboot my computer, and figure out what the problem was through process of elimination.

Needless to say, bootloader threw an error (17) and wouldnt boot to any menus. So now my SATA drive is unplugged, and I'm on the dirty looking windows side of my computer.

Do I have to format my Ubuntu hard drive, or is there still hope?

Any help would be appreciated

---

### Post by az on 2006-02-16
It would seem that your partition table has been messed up.  Your data is still all there, but the hard drive does not think there is a partition there.

You can boot the installer cd (or any live cd you like - just remember to unmount your swap if you use a a live cd other than the installer - they pretty much find your swap and mount it;  type swapoff -a)

From the installer Use the second command-line terminal (CTRL-ALT-F2) and run parted

parted /dev/sda

make use of the rescue option.  I think you just have to tell it where you though a partition was and it will look there and try to add it to the partition table.  It should work.  Do this for all the partitions that were on that drive...

In parted, "print"shows you the current partition table.

Good luck.

Maybe read the parted manual (print it out) so that you can have it next to you while you do this....

---

### Post by kgee on 2006-02-16
ok, i tried the command line from the installer (ash) and there was no parted command. It didnt recognise parted as a command, it wasnt in the command list, or anything else that looked related to partitioning.

am i doing something wrong, or just not seeing something?

I booted the cd, ran the installer (both with just booting the installer and typing in "rescue" before booting) and then i used both ctrl+alt+f2 and the shell command to get into the ash command prompt. from there it seemed a dead end.

I am very much certain that all the data is still on my disk somewhere, and it is just the partition table that is screwed up.

The only solution I can think of off the top of my head is to get a live cd and use that to edit the /dev/sda. Unfortunately I dont have a live cd here. I'm pretty sure there was just one partition and a swap file. I even think i remember the size and order they go in. so if i can get to the partition table I think i can recover my system.

---

### Post by az on 2006-02-16
[QUOTE=kgee]ok, i tried the command line from the installer (ash) and there was no parted command. It didnt recognise parted as a command, it wasnt in the command list, or anything else that looked related to partitioning.

am i doing something wrong, or just not seeing something?

I booted the cd, ran the installer (both with just booting the installer and typing in "rescue" before booting) and then i used both ctrl+alt+f2 and the shell command to get into the ash command prompt. from there it seemed a dead end.

I am very much certain that all the data is still on my disk somewhere, and it is just the partition table that is screwed up.

The only solution I can think of off the top of my head is to get a live cd and use that to edit the /dev/sda. Unfortunately I dont have a live cd here. I'm pretty sure there was just one partition and a swap file. I even think i remember the size and order they go in. so if i can get to the partition table I think i can recover my system.[/QUOTE]


Sorry.  You need to go through the first steps of the installer.  After you configure your keyboard and it locates the cdrom hardware, it loads the components into memory - parted is one of thoese components.  

Just go through the installer until it gets to the partitoining.  Then, skip to CTRL-ALT-F2.

Sorry for my imprecision.

---

### Post by kgee on 2006-02-17
thanks, I'll give it a shot.

the good people at efnet #linux and #linux2 are pretty stumped too, so no dice from them.

so, I guess this is my last resort before formatting.

---

### Post by az on 2006-02-19
Okay, I booted the Dapper live cd and tried out the espresso live-cd-installer.

I forgot a file on a partition on my hard drive.

I stopped the install, rebooted and found an empty partition table.

So I used the recovery function - I did this:

ubuntu@ubuntu:~$ sudo parted /dev/hdb
GNU Parted 1.6.25.1
Copyright (C) 1998 - 2005 Free Software Foundation, Inc.
This program is free software, covered by the GNU General Public License.

This program is distributed in the hope that it will be useful, but WITHOUT ANY
WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.  See the GNU General Public License for more details.

Using /dev/hdb
(parted) print
Disk geometry for /dev/hdb: 0kB - 10GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
(parted) ?
  check NUMBER                  do a simple check on the file system
  cp [FROM-DEVICE] FROM-NUMBER TO-NUMBER   copy file system to another partition  help [COMMAND]                prints general help, or help on COMMAND
  mklabel LABEL-TYPE            create a new disklabel (partition table)
  mkfs NUMBER FS-TYPE           make a FS-TYPE file system on partititon NUMBER
  mkpart PART-TYPE [FS-TYPE] START END     make a partition
  mkpartfs PART-TYPE FS-TYPE START END     make a partition with a file system
  move NUMBER START END         move partition NUMBER
  name NUMBER NAME              name partition NUMBER as NAME
  print [NUMBER]                display the partition table, or a partition
  quit                          exit program
  rescue START END              rescue a lost partition near START and END
  resize NUMBER START END       resize partition NUMBER and its file system
  rm NUMBER                     delete partition NUMBER
  select DEVICE                 choose the device to edit
  set NUMBER FLAG STATE         change a flag on partition NUMBER
  unit UNIT                     set the default unit to UNIT

(parted) rescue
Start? 4999
End? 10000
Information: A ext3 primary partition was found at 5001MB -> 9550MB.  Do you
want to add it to the partition table?
Yes/No/Cancel? yes
(parted) print
Disk geometry for /dev/hdb: 0kB - 10GB
Disk label type: msdos
Number  Start   End     Size    Type      File system  Flags
1       5001MB  9550MB  4549MB  primary   ext3
(parted) quit
Information: Don't forget to update /etc/fstab, if necessary.

ubuntu@ubuntu:~$ sudo mkdir /hdb1
ubuntu@ubuntu:~$ sudo mount /dev/hdb1 /hdb1
ubuntu@ubuntu:~$ nautilus /hdb1
ubuntu@ubuntu:~$




And I saved my file to usb drive.


It works.

---

