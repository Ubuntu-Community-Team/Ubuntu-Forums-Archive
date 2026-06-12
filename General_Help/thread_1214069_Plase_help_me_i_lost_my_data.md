---
title: "Plase help me i lost my data"
date: 2009-07-15
forum: General Help
---

### Post by GBLinux on 2009-07-15
Hello,

I was installing ubuntu operating system on my computer.
At the installing procedure in the step i guess 3 & 4 where we have to select partition for installation i done something wrong.

I choosed "manually" check box button then preceeded forward, in the next step i choose one of my drive which was kept empty for ubuntu.

I then edited the drive setting to file system JFS File system.

When i clicked next there was some warning on swap & physical memory thing.It told me to choose one swap drive.I though it wouldn't do any wrong with the drive.

When the installation procedure was completed i couldn't find the swap drive in the Home.

I then logged into the windows xp it was also not showing there.

The previous file system of swap drive was ntfs.


The drive isn't showing and i want to extract data from it how do i do it ????


Please help me Linux expert's, can the data be recovered.

While in the step i didn't choosed to format the swap choosen drive because as you know there was precious data.

Due to the misconception this problem occurred.

I thought that the data will be safe there and it will be visible.

What should i do now, please give any suggestion that can enable me extracting the data.

Thank You!

---

### Post by ramnarayan on 2009-07-15
Ok First Step - be very very cool and don't do anything till you know all the implications

Second - i hope you have access to another machine which has internet access or there is internet access on your existing machine using the Live CD

Third and importantly - there are many recovery tools available under Linux so in many / most cases it should be possible to get your data back.

Check google for how to recover data + preferably stick to Ubuntu / Linux tools because they are your best bet

Boot you live CD and it should have testdisk that runs from the terminal

run this and see what all options it has and how to use it.

Make sure you read up on testdisk 
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

am quite sure if you follow all the parameters and instructions you will get your data back.

---

### Post by ramnarayan on 2009-07-15
it would also be good if you had an additional external drive on which to copy your data.

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> it would also be good if you had an additional external drive on which to copy your data.


Yes i have a drive to copy that data.

Really can we copy the data from swap drive which is not visible to me.

---

### Post by Kraut~salat on 2009-07-15
I get the impression you don't really know what swap space is. It is like a RAM extension. When your RAM is full Linux will ofload some memory into swap to free RAM. You as a user don't explicitly store data (i.e. files and folders) in swap space. It doesn't even make sense to read what's on swap space, since it is all cryptic RAM extracts.

You don't "see" swap space in your file system. There is no "/media/swap" or anything like that. Type 'cat /proc/meminfo|grep Swap'. The line with SwaTotal should tell you if you have swap activated, it should read more than 0kB.

And you will certainly not see swap space unter Windows. Your don't even see regular partitions since Windows can't read any of the linux filesystems

---

### Post by GBLinux on 2009-07-15
> **Kraut~salat said:**
> I get the impression you don't really know what swap space is. It is like a RAM extension. When your RAM is full Linux will ofload some memory into swap to free RAM. You as a user don't explicitly store data (i.e. files and folders) in swap space. It doesn't even make sense to read what's on swap space, since it is all cryptic RAM extracts.

You don't "see" swap space in your file system. There is no "/media/swap" or anything like that. Type 'cat /proc/meminfo|grep Swap'. The line with SwaTotal should tell you if you have swap activated, it should read more than 0kB.

And you will certainly not see swap space unter Windows. Your don't even see regular partitions since Windows can't read any of the linux filesystems


Yeap i thought it would work same as paging in windows and wouldn't do any thing wrong to data meaning lost ?


Can the data be recovered ????

---

### Post by m4tic on 2009-07-15
swap is usless from my my xperienc

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> Yeap i thought it would work same as paging in windows and wouldn't do any thing wrong to data meaning lost ?


Can the data be recovered ????

Yes as long as you don't make use of the swap space 
the first thing (i think ) would be to un mark the swap as swap and make it anything else 
am not sure if a live system also uses on board swap (i think it does) - anyone can confirm this

---

### Post by GBLinux on 2009-07-15
> **m4tic said:**
> swap is usless from my my xperienc


I was installing ubuntu for first time, actaully i wasn't going to choose swap as im having 4GB of RAM.

Can the data of 49GB within the drive which was converted to swap during installation be recovered ????

I have downloaded the tool "testdisk-6.11.tar.bz2"

But don't how to start it ?

Please help me............................................

---

### Post by t4thfavor on 2009-07-15
> **m4tic said:**
> swap is usless from my my xperienc

With more than 1GB or ram I rarely use my swap, for future reference If you have 1-2GB of RAM, just forgo the swap partition. It will save you from accidentally deleting all your data.


Good luck recovering your data, I +1 the tutorial mentioned above.

---

### Post by GBLinux on 2009-07-15
Guys i think you didn't get me.

Actaully i was having a drive in windows of file system NTFS having a important data in it.

While i decided to take surf on Linux architecture i choosed to install it.

During the installation i choosed this as swap drive.

After installation i was dead for a while had a glass of water gone through many thing ultimately came here.

Is the data still there ? Can it be recovered ? How do it recover it ?

Sorry guys for troubling you linux experts but please i request you to spend some time on this problem.

---

### Post by Kraut~salat on 2009-07-15
well, in principle data can be recovered as long as it has not been overwritten. 
Once I had the problem that my partition table got damaged. After I repartitioned my harddrive to the exact same simensions I had before and setting the filesystem types like they were before, I could completely recover my data.

For you that means,, that you would have to know the exact size and location (i.e. start and end block) and the filesystem type of the partition you want to recover. Then you would have to use fdisk to create a partition that has exactly those parameters. Partitioning a hard drive does not destroy data, but formating does! 

UNFORTUNATLY if linux formatted the partition as swap space, which USUALLY IS THE CASE when you install Linux and tell it to use swap space, your data WILL BE LOST. So I don't think there is much help in your case. No tool can recover data that has been overwritten.

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> I was installing ubuntu for first time, actaully i wasn't going to choose swap as im having 4GB of RAM.

Can the data of 49GB within the drive which was converted to swap during installation be recovered ????

I have downloaded the tool "testdisk-6.11.tar.bz2"

But don't how to start it ?

Please help me............................................

Ok where did you download testdisk

am assuming you have a Live Ubuntu CD

Pop that in to your computer and restart it

once it starts up 
open a terminal
Applications ->Accessories ->Terminal

type 
```
sudo testdisk 
```

and follow the instructions

**
make sure you read about testdisk and how it works before you use it

Second there are windows based versions of testdisk - maybe you can try and run that
[http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

am not too familiar with testdisk under windows but can tell you from personal experience that testdisk under a Live Ubuntu session saved my data (most of it atleast)

---

### Post by GBLinux on 2009-07-15
I haven't formatted the drive as stated earlier.

I had extracted that package to the root system and got into the dir through terminal.

I typed ../configure but some error is been stated at last saying - > cannot create executable....

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> Yes i have a drive to copy that data.

Really can we copy the data from swap drive which is not visible to me.

Hey try test disk it will show you the entire disk and try and recover what ever is possible 

first do that and see

---

### Post by ramnarayan on 2009-07-15
testdisk is available on the ubuntu boot cd 
[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

so just go for it

---

### Post by Kraut~salat on 2009-07-15
well, the point is YOU didn't format it yourself, but you told the installer to use swap, so the installer (most likely) did it FOR YOU.

well, once you have the liveCD running run
fdisk -l /dev/<what ever harddisk your partition is on>

and post the output. This will tell you if your partition is now a swap partiion. In that case your data whould be lost.

---

### Post by ramnarayan on 2009-07-15
> **Kraut~salat said:**
>  Partitioning a hard drive does not destroy data, but formating does! 


Not really , even after formatting the data is still there - its only when it gets overwritten by new data that the problems appear
> 
UNFORTUNATLY if linux formatted the partition as swap space, which USUALLY IS THE CASE when you install Linux and tell it to use swap space, your data WILL BE LOST. So I don't think there is much help in your case. No tool can recover data that has been overwritten.

Testdisk can and will help provided you run it off a live cd and not off a fresh install

DO NOT INSTALL a new version of Linux

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> I haven't formatted the drive as stated earlier.

I had extracted that package to the root system and got into the dir through terminal.

I typed ../configure but some error is been stated at last saying - > cannot create executable....

Oye why are you trying to install testdisk

if you are using Ubuntu Live CD it is already installed on that

[COLOR="Red"][SIZE="6"]so to use testdisk do the following

[/SIZE][/COLOR]

Go to
APPLICATIONS -> ACCESSORIES -> TERMINAL

IN TERMINAL TYPE
```
sudo testdisk
```

press enter

make sure your testdisk terminal is full screen or atleast 25 lines long 

follow the instructions

---

### Post by GBLinux on 2009-07-15
[FONT=monospace]swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
swapnil@GB:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
bash: testdisk: command not found
swapnil@GB:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
swapnil@GB:~$ 
swapnil@GB:~$[/FONT]

---

### Post by Kraut~salat on 2009-07-15
> **ramnarayan said:**
> Not really , even after formatting the data is still there - its only when it gets overwritten by new data that the problems appear


well, formatting will create a file system infrastructure on the partition, which overwrites some parts of the old data. 
One should also consider that even overwriting a single block of a multi MB file will corrupt the entire file. Filesystem work like daisy chains in a way. each sector has the number of another sector that also belongs to the file. If that information is damaged the entire daisy chain is bust.

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> [FONT=monospace]swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
[/FONT]

what Linux are you using

??

Ubuntu if so what version

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> Oye why are you trying to install testdisk

if you are using Ubuntu Live CD it is already installed on that

[COLOR=Red][SIZE=6]so to use testdisk do the following

[/SIZE][/COLOR]

Go to
APPLICATIONS -> ACCESSORIES -> TERMINAL

IN TERMINAL TYPE
```
sudo testdisk
```press enter

make sure your testdisk terminal is full screen or atleast 25 lines long 

follow the instructions

No No i m not using live cd i have actual installed version of ubuntu on my one partition.

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> what Linux are you using

??

Ubuntu if so what version


**Ubuntu 8.04 LTS Desktop Edition**

---

### Post by ramnarayan on 2009-07-15
> **Kraut~salat said:**
> well, formatting will create a file system infrastructure on the partition, which overwrites some parts of the old data. 
One should also consider that even overwriting a single block of a multi MB file will corrupt the entire file. Filesystem work like daisy chains in a way. each sector has the number of another sector that also belongs to the file. If that information is damaged the entire daisy chain is bust.

True but not all the data will be either corrupted or lost

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> **Ubuntu 8.04 LTS Desktop Edition**

is it a live session ??

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> No No i m not using live cd i have actual installed version of ubuntu on my one partition.

Ok it should be on the installed version as well

however if its not there (for whatever strange reason) and you are connected to the internet then

go to Administration -> Synaptic package manager and find the packake testdisk and install

HOWEVER I STRONGLY RECOMMEND RE BOOTING INTO A LIVE SESSION OF UBUNTU BECAUSE IT WOULD MEAN YOU WILL NOT MESS YOUR HARD DISK UP ANY MORE

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> is it a live session ??

Sorry i new to linux arch can you explain.

Right im running ubuntu from hard drive not from cd my friend.

Rebooting............

---

### Post by estyles on 2009-07-15
run it from the CD (choose "Try Ubuntu without any changes to my system")

then in a terminal type "sudo testdisk".

if it's not found, then do "apt-get install testdisk", and then "sudo testdisk".

The second part of that should be easy enough since it looks like you already did that and posted the output.  You just want to do it while running from CD.

Edit: Also, read up on testdisk.  It's fairly complicated, but that's what makes it so powerful.  If you have any question about what you're doing, post a screenshot here before committing any changes.

---

### Post by aesis05401 on 2009-07-15
> **Kraut~salat said:**
> well, formatting will create a file system infrastructure on the partition, which overwrites some parts of the old data. 
One should also consider that even overwriting a single block of a multi MB file will corrupt the entire file. Filesystem work like daisy chains in a way. each sector has the number of another sector that also belongs to the file. If that information is damaged the entire daisy chain is bust.

I'm sorry, NTFS stores address map shadow files at the end of the boot partition.  Data recovery is possible unless a 'low-level' format has been performed - which you would know because it would have taken a while to complete as it was physically rearranging the disk (you do this when creating RAID partitions for instance).

Recovering data from high level formatted partitions should be easy and there are many tools to do it... Even in the Windows world where you can download a FreeDOS live cd to run the following utilities:[http://www.partitionsupport.com/utilities.htm]("http://www.partitionsupport.com/utilities.htm")

---

### Post by GBLinux on 2009-07-15
swapnil@GB:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'
bash: testdisk: command not found
swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
swapnil@GB:~$ apt-get install testdisk
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
swapnil@GB:~$

i don't know what is going the testdisk utility within the ubuntu is not working.

---

### Post by GBLinux on 2009-07-15
Good news swap drive is not been in use i checked it through
SYSTEM>ADMINISTRATION>SYSTEM MONITOR

This is because im having 4GB RAM.

The data within the drive which was converted to swap is not over written so i guess we should get some method to disable swap.

---

### Post by estyles on 2009-07-15
> **GBLinux said:**
> swapnil@GB:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'
bash: testdisk: command not found
swapnil@GB:~$ sudo testdisk
sudo: testdisk: command not found
swapnil@GB:~$ apt-get install testdisk
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
swapnil@GB:~$

i don't know what is going the testdisk utility within the ubuntu is not working.


Sorry, that's my stupid.  You should use "sudo apt-get install testdisk".  You can't install software unless you are root, even with the LiveCD, so you use sudo to pretend to be root.

However, from your prompt above, you are not running from the LiveCD.  Running testdisk from a live installation is a bad idea.  Boot from CD.  Also, you might need to do "swapoff", or maybe it's "sudo swapoff", I dunno.

---

### Post by GBLinux on 2009-07-15
swapnil@GB:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
swapnil@GB:~$

how do i install it manually i have the tar package downloaded from internet.

---

### Post by nikhilbhardwaj on 2009-07-15
yes 
sudo /sbin/swapoff
will make sure that you dont use the swap partition

compile testdisk from source 
tell us what errors you get

---

### Post by ramnarayan on 2009-07-15
> **estyles said:**
> Sorry, that's my stupid.  You should use "sudo apt-get install testdisk".  You can't install software unless you are root, even with the LiveCD, so you use sudo to pretend to be root.

However, from your prompt above, you are not running from the LiveCD.  Running testdisk from a live installation is a bad idea.  Boot from CD.  Also, you might need to do "swapoff", or maybe it's "sudo swapoff", I dunno.


Why is running testdisk from a Live CD a bad idea ??

thought that if its from a live cd the orginal HD is left alone till the data is recovered and the problem with swap also will not happen

---

### Post by nikhilbhardwaj on 2009-07-15
i assume that you have downloaded this
[http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2](http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2)
lets say to your desktop

open a shell and type

cd ~/Desktop
tar xf testdisk-6.11.3.linux26.tar.bz2

now a new directory testdisk-6.11.3 will be on your desktop
in the same shell do 

sudo ~/Desktop/testdisk-6.11.3/linux/testdisk_static

---

### Post by nikhilbhardwaj on 2009-07-15
the live cd also uses any swap partition it finds on the machine
so if you run an installed version or live cd 
its no difference

but lets hope testdisk works for him

---

### Post by estyles on 2009-07-15
> **ramnarayan said:**
> Why is running testdisk from a Live CD a bad idea ??


Running from a live installation is a Bad Idea.  Running from the Live CD is much better.  But the OP seems to be ignoring that.

---

### Post by ramnarayan on 2009-07-15
> **estyles said:**
> Running from a live installation is a Bad Idea.  Running from the Live CD is much better.  But the OP seems to be ignoring that.

Ah i got you wrong - onfused live installation for live CD

OYE GBLINUX(aka swanpnil) GOT THAT

go for testdisk through a LIVE CD

---

### Post by GBLinux on 2009-07-15
> **aesis05401 said:**
> I'm sorry, NTFS stores address map shadow files at the end of the boot partition.  Data recovery is possible unless a 'low-level' format has been performed - which you would know because it would have taken a while to complete as it was physically rearranging the disk (you do this when creating RAID partitions for instance).

Recovering data from high level formatted partitions should be easy and there are many tools to do it... Even in the Windows world where you can download a FreeDOS live cd to run the following utilities:[http://www.partitionsupport.com/utilities.htm](http://www.partitionsupport.com/utilities.htm)

> **ramnarayan said:**
> Ah i got you wrong - onfused live installation for live CD

OYE GBLINUX(aka swanpnil) GOT THAT

go for testdisk through a LIVE CD


How to go LiveCD mode.....

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> How to go LiveCD mode.....

Find your Ubuntu CD

Pop it into your CD drive

restart your computer

when presented with the options say try Ubuntu without changing the system

Voila you have a LIve session on

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> Find your Ubuntu CD

Pop it into your CD drive

restart your computer

when presented with the options say try Ubuntu without changing the system

Voila you have a LIve session on


Yes i have done that but the testdisk doesn't work in it.

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> Yes i have done that but the testdisk doesn't work in it.

meaning you tried 
```
sudo testdisk 
```

in the terminal and nothing happened

what did you do exactly

---

### Post by estyles on 2009-07-15
> **GBLinux said:**
> Yes i have done that but the testdisk doesn't work in it.

All of the outputs you posted are from your installed OS...  If you've indeed tried booting the LiveCD and weren't able to install testdisk, try running Synaptic from the LiveCD (it's in the Administration part of the menu), and search for testdisk.  It's probably best if you do the "swapoff" thing before you install testdisk, as I'm not sure if installing while running a LiveCD might touch the swap partition...  Probably depends on how much RAM you have available, but turn the swap off just to be safe.

---

### Post by GBLinux on 2009-07-15
swapnil@GB:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'

how do i enable component named universe

and yes also disable swap usage. ??

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> meaning you tried 
```
sudo testdisk 
```in the terminal and nothing happened

what did you do exactly


Now just i logged into LiveCD and tried the command sudo testdisk

same error again.... testdisk is not installed you have to install it so and so....

its showing you have to enable component name universe.

Also i want to disable swapping how do i do that ?

swapnil@GB:~$ swapoff
usage: swapoff [-hV]
       swapoff -a [-v]
       swapoff [-v] special ...

---

### Post by estyles on 2009-07-15
> **GBLinux said:**
> swapnil@GB:~$ testdisk


See your prompt above?  You are running from an installed copy of ubuntu.  You want to boot from the CD.  If you are running from the LiveCD, it will say something like ubuntu@ubuntu:~$

For how to disable swap, see posts earlier in the thread. 

To enable universe, it's probably easiest to do from Synaptic.  Run Synaptic and look for the settings for "Sources".  Sorry I can't be more specific, but I'm running on Windows at work right now - no access to Ubuntu.

---

### Post by GBLinux on 2009-07-15
> **estyles said:**
> See your prompt above?  You are running from an installed copy of ubuntu.  You want to boot from the CD.  If you are running from the LiveCD, it will say something like ubuntu@ubuntu:~$

For how to disable swap, see posts earlier in the thread. 

To enable universe, it's probably easiest to do from Synaptic.  Run Synaptic and look for the settings for "Sources".  Sorry I can't be more specific, but I'm running on Windows at work right now - no access to Ubuntu.


just now tested showing same error in both environments....

---

### Post by ramnarayan on 2009-07-15
> **GBLinux said:**
> swapnil@GB:~$ testdisk
The program 'testdisk' is currently not installed.  You can install it by typing:
sudo apt-get install testdisk
You will have to enable the component called 'universe'

how do i enable component named universe

and yes also disable swap usage. ??

How did you install Ubuntu in the first place 

was it through windows

I think you may need to enter your bios at boot up time and enable booting from CD (or make the cd drive the first in the boot order)

It seems like you are unable to boot into the live cd ??

---

### Post by GBLinux on 2009-07-15
Just now discovered that gnuc++ compiler is uninstalled in the system i guess because of this i was unable to compile the testdisk package given by you.

Let me install the compiler and then i try compiling and running the source.....

---

### Post by ramnarayan on 2009-07-15
why not try the windows version of testdisk - if you have windows functional

am not sure how well it will work and how much it will recover.

So if i were you i would still persist in figuring out how to make testdisk work through linux

---

### Post by GBLinux on 2009-07-15
> **ramnarayan said:**
> How did you install Ubuntu in the first place 

was it through windows

I think you may need to enter your bios at boot up time and enable booting from CD (or make the cd drive the first in the boot order)

It seems like you are unable to boot into the live cd ??


No i have got up with things like live sesison.(thorugh cd os is being loaded ! right)

Yes i was in live session recently may be 5 minutes ago, there i launched the terminal and typed sudo testdisk.

same error is being showing as of here.

Now im installing the gnuc++ compiler and will try compiling the sources given by you guys.

---

### Post by GBLinux on 2009-07-15
swapnil@GB:~/Desktop/ABC$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln -s works... yes
checking whether make sets $(MAKE)... (cached) yes
checking for windres... ./configure: line 3346: WARNING:: command not found
no
checking for special C compiler options needed for large files... no
checking for _FILE_OFFSET_BITS value needed for large files... 64
checking for _LARGE_FILES value needed for large files... no
checking for library containing initscr... no
*** The ncurses library is required!

I compiled testdisk-6.11.tar.bz2 and got this.....

---

### Post by GBLinux on 2009-07-15
Back again with 4 hours of sleep.

I wasn't sucessful in launching and installating testing "testdisk" for so i decided to go for window.I just downloaded the binary package and started it.

Here i choosed to analyze my HDD of 260GB.The below image is hierarchy of my HDD.
Before doing anything guys suggested me here to post screenshot before committing any changes to hdd.

Recent structure :-
I had 4 drives in my computer(windows xp) 
1.Windows XP (C:\)
2.Study (D:\)
3.Gaming (E:\)
4.Media(F:\)

The Media one(F:\) i choosed for unbuntu but during installation i choosed study drive as swap drive and which later wasn't visible to me.

Please experts give guidance on recovering that drive (Study [D:\])
It is currently acting as swap for linux and it has not been used because i have 4GB of RAM which is enough to handle any heat.

---

### Post by GBLinux on 2009-07-15
I selected the option search there "to find partitions"

I got this......

---

### Post by GBLinux on 2009-07-16
> **ramnarayan said:**
> why not try the windows version of testdisk - if you have windows functional

am not sure how well it will work and how much it will recover.

So if i were you i would still persist in figuring out how to make testdisk work through linux



testdisk launched successfully in Linux environment.


Waiting for future instructions.....

---

### Post by TravisNewman on 2009-07-16
swapnil@gb would not be showing up if you were booting from the live cd. It doesn't sound like you are successfully booting into the live cd to begin with.

---

### Post by GBLinux on 2009-07-17
> **panickedthumb said:**
> swapnil@gb would not be showing up if you were booting from the live cd. It doesn't sound like you are successfully booting into the live cd to begin with.

I can go into live but give me instructions to disable swap drive in ubuntu

and

should i change the type of Linux Swap drive to NTFS and write MBR which would enable the drive to show up in widows ad yes will it be sure that data will be present.

Please help two days have passed no one has replied me yet with what to do next.

I guess i have to take the risk to the thing's i have planned above..........................................................

---

