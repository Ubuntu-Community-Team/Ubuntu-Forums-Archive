---
title: "2 problems 1)carnt install no permisions@root 2) strange hard drive moutn prob"
date: 2006-05-10
forum: General Help
---

### Post by reidy- on 2006-05-10
Hi i am kinda new to the linux thing but I consider myself pretty computer apt so I don't deem these things to be simple error's (although seen as have never used linux I may be wrong)

my first problem is that:

I cannot access any other partition other than the one with the ubuntu installation on it, I use the system - administration - HAL(system disk) utility to enable all partitions but I  don't know what access path to use, and if i try to go into the /dev/hdb1 it says i canot open the file I think that i am just doing womethign wrong with the access paths but not entirley sure what to do

my secound problem is that i cannot execute a script either clciking the icon or running it from the console I have tried it just as a normal user and root but it still tell's me access denied even though I have checked through the scripts permisions

thanks in advance, Aaron

---

### Post by cgjones on 2006-05-10
1. /dev/??? are references to devices. A device can then be mounted in the filesystem. If you type **mount** in the terminal, you'll see a list of all currently mounted devices. If you are trying to access /dev/hdb1, see where it is mounted and that will be the path.

2. What is the script for and what are the permissions on it?

---

### Post by reidy- on 2006-05-10
yeh I have mounted the devices but no matter what I put as the path i cannot acess this i know it sounds starnge but what program do you use to open the hard drive iconed links because It trys to open it with a text editor and even i know that is not right :p

the script is to install my x300 drivers automatically and i have set the permissions so that any one or anythign can use it (all check boxes ticked)

---

### Post by cgjones on 2006-05-10
I'm not at my Ubuntu machine right now, I'll have to wait until I get home to check it out further.

---

### Post by Omnios on 2006-05-10
This is the wiki page pertaining to mounting and automounting windows drives.
[http://help.ubuntu.com/starterguide/C/ch05.html]("http://help.ubuntu.com/starterguide/C/ch05.html")
 Generaly it will give you a basic idea for mounting any partition. Also there is a fstab link in my signature that does a good job of explaining fstab. 

 To see what partitions are on your sytem in terminal type sudo fdisk -l as in -l (L) for list. Carefull with fdisk as it can format a drive lol. No seriosly if you just use -l you should be ok, You can also type fdisk --help or man fdisk to read more about it. Anyways this will give you a list of the partitions on your computer. 

 Also mounting a partition in Ubuntu you must create a mount to directory in /media/  for example I have Documents for one of my partitions. Now in fstab which automounts partitions on start up  I have
[CODE][/dev/hda2       /media/Documents    vfat    rw,users,gid=users,umask=000,CODE]
Now the /dev/hda2  is the partition the /media/Documents is the mount to file so for eample if you make a directory in /Media called partition1 you would use /media/partition1 in the fstab entry. the rest is for owner and partition which is explained further in fstab link in my signature. Hopefully this gets you started off ok. 
Cheers

---

### Post by reidy- on 2006-05-10
Thanks omnios doing it from the command prompt worked a treat i dont know why HAL wouldnt work it won't unmount either drivers even thoguh they are not in use either but the command prompt does it fine.

now about the file permissions have tried other scripts as well cannot run / compile these either any one ever had this problem before?

p.s. I am running the AMD 64 bit version but i thorght the problems where mroe orientated about the applications / desktop itself rather than drivers but I though I better tell you encase

thanks, Aaron

P.S can any one email me a pre compiled MP3 player as I am stuck here trying to solve the compilation mystery with no music :O i shall be forever in your debt (reidy- at hotmail.co.uk)

---

