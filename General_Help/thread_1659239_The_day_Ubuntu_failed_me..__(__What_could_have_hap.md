---
title: "The day Ubuntu failed me..  :(  What could have happened?"
date: 2011-01-03
forum: General Help
---

### Post by Rasa1111 on 2011-01-03
Hey all, 
 (coming to you via LiveCD)

Very odd thing happened this afternoon with my Ubuntu desktop,
and i have no idea what could have gone wrong. 


It started when Ubuntu warned me of only 1.3 GB of disk space remaining, 
and informed me I should free up some space. 

So,
 I started to go through files , getting ready to delete/move files that I didnt need on the PC itself~
But Had a lot of resources running, so decided I would restart the PC before I started to "clean up". 

 So,
 I restart the PC, 
The purple Ubuntu loading screen appears...
and the orange dots underneath "Ubuntu" "load" as normal.. 
But..
 It never gets past this screen now.  :(

So, 
After about 10 minutes of waiting to see if it would do anything, (and it did nothing)
i gave it a manual shutdown, and turned it back on. 

Once PC booted back up..
It brought me to the GRUB menu/ screen!?

 I have only Ubuntu 10.10 installed,
and the GRUB menu never comes up when i boot my PC,
but now it just appears out of nowhere. 

Then,
I try to select my Ubuntu OS (first in the GRUB list)..
it takes me back to the purple loading screen.. 
and hangs,
and hangs,
and hangs...
Never to boot into my Ubuntu. 

What could have happened?

Is there a way i can fix this?
(without having to do a full re-install)

 My system is exactly how I want it now, (go figure)
and if I could recover my system without having to start from scratch all over again..
that would be beautiful. 

 But I guess Ill do what i have to. 

Anyone else know whats going on here?
and/or how I can remedy this? 

 Thanks for your time, and any insight you can provide. 
It is much appreciated.  <3

 Rasa

---

### Post by Dans564 on 2011-01-03
can u boot into recovery mode via grub os choices?

---

### Post by Rasa1111 on 2011-01-03
Hey Dan, 

 yeah, I can get into recovery mode via grub, 
but to be honest.. I don't know what to do once in there. 

 I have attempted recovery mode before I made this post..
and the screen filled up with a bunch of text, listing devices and what not..
but once the screen was full...

I let it sit for another 5 minutes or so..
and it had not progressed any further,
or done anything else. 

So either I do not know how to use recovery mode,
or it wasnt working right..
 Im really not sure..

---

### Post by frotzed on 2011-01-03
Have you ruled out a failing hard drive?

---

### Post by Rasa1111 on 2011-01-03
> **frotzed said:**
> Have you ruled out a failing hard drive?


 Hey,

 nah, I have not really ruled it out .. yet.. 
Honestly, Im not sure how I would? 

I can access it from the LiveCD, no problem..
and i have just copied my entire home folder onto an external drive.. just in case.. 

 But I really have no idea what to do, or where to go, from here. :confused:

---

### Post by deserthowler on 2011-01-03
> **Rasa1111 said:**
> Hey,

 nah, I have not really ruled it out .. yet.. 
Honestly, Im not sure how I would? 

I can access it from the LiveCD, no problem..
and i have just copied my entire home folder onto an external drive.. just in case.. 

 But I really have no idea what to do, or where to go, from here. :confused:

you might run bad blocks in the non-destructive mode and see what that gives you.
check the switches in the badblocks manpages to decide how you wish to run it.
Earl

---

### Post by Rasa1111 on 2011-01-04
Hey mate,
 I have no idea what that means. 
Im sorry. :(

I am confused on how I would install/run something, if I cannot get into my desktop ?

 I think I foresee a re-installation in my very near future... lol   :/

---

### Post by frotzed on 2011-01-04
For checking your HDD, I'm thinking something like Seatools for DOS [http://bit.ly/gYg1jM](http://bit.ly/gYg1jM)

Download, burn .iso to a CD, boot to that CD, let it do its thing.  At least then you can rule out a failing hard disk.

---

### Post by 23dornot23d on 2011-01-04
Hi Rasa1111

Just a few questions ....... 

What did you delete and did you actually run out of space while upgrading .....

do you know how much space is left on the drive

and lastly can you run gparted from the live cd ...... to show the state of the disk ......

(and maybe we need a screen shot using gparted and the drive layout to start with) ....

you can check the disk if you want for bad sectors ....... 

but gparted should give you a reasonable idea if there are any problems with space to start with.

if it shows the layout of the drive we have a start point .... and should see if the disk is just full up

might be worth running the bootscript too ..... in the footer here ..... you need to do everything from livecd

I have been in this position before .... through having no room left on the drive ...... hopefully thats all it is.

we need to be able to get to the prompt though to clean it up a little ........

apt-get clean

apt-get autoclean

may be useful if it is just a out of space problem .............

---

### Post by Nytram on 2011-01-04
Hi Rasa

**badblocks** is a terminal program, just type that name into a console to start it, or **man badblocks** for usage info. you should be able to do this with the live cd

something else i would try is **fsck** in a terminal, just make sure the hd isnt mounted

it might be a good idea to free up some more space, in case thats the cause of the problem

---

### Post by matt_symes on 2011-01-04
Hi

> The purple Ubuntu loading screen appears...
and the orange dots underneath "Ubuntu" "load" as normal.. 

If you press the escape key on this screen it should display boot up text. What is the last message it displays?

Kind regards

---

### Post by Rasa1111 on 2011-01-04
> **frotzed said:**
> For checking your HDD, I'm thinking something like Seatools for DOS [http://bit.ly/gYg1jM](http://bit.ly/gYg1jM)

Download, burn .iso to a CD, boot to that CD, let it do its thing.  At least then you can rule out a failing hard disk.

 Hey mate,

 How am I supposed to do that, when I can only get into the PC via LiveCD?

 The CD needs to be in to do anything.. 
So, I could download the iso, I guess... 
But since my CD drive is already occupied.. 
the rest seems 'impossible'. 

** @ 23dornot23d**~
 Thanks, <3

 I had actually not even deleted anything yet,
 I was going to wait until after I restarted the PC,
which never happened.. 

 There is currently 2.6 GB of unused space on the HDD~
Gparted shot~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180126&d=1294178212[/IMG]

 Anything else Im missing for the shot? 

@ Nytram, Thanks mate, Good to know! <3

 Many thanks for all replies. <3

---

### Post by Rasa1111 on 2011-01-04
> **matt_symes said:**
> Hi



If you press the escape key on this screen it should display boot up text. What is the last message it displays?

Kind regards

 I will try that momentarily and let you know,
 thank you. <3

---

### Post by 23dornot23d on 2011-01-04
Thats plenty of space  ...... 2.6 gig - 

so its not space then ...... was hoping that it would be actually
for a quick fix ...... and if you have not deleted anything then the system should boot .... have you done a cold boot

switch the machine fully of at the mains and restart it ?

Still we need to be able to get to the 

$ prompt


I would usually (if it gets stuck like this) install kdm ...... apt-get install kdm ...... 
and give it a different desktop manager ....... to see if that works ...... but you need to be able to get to the $ 
 

safemode .... have you tried it a few times or just the once ..... give it a few tries 

ctrl d used to go to interactive in boot .... but not sure if this still works nowadays  ...... or ctrl+alt+f1 ...... we need a terminal to do anything from .....

Will have a look see if there are any other interupt keys .......... ctrl c and ctrl y would always stop things ..... 

but not sure if they will work when booting the desktop up .

```

Thinking of options ,,,, rather than wiping the full drive ..... and other things it might be .....

1 ..........What graphics card is it and did you just upgrade ..... the system 
I wonder if its the graphics driver its hanging on ....... 
nomodeset ...... in the boot options ....... is the next thing that comes to mind.
but even then you need to edit the boot options ......
(just thinking out loud here ..... of what else may cause it .... thats easy to fix.)

2 .......... if it is bad blocks ..... then the hard drive may be ready for replacing ..... in which case you could get a bigger one
and transfer everything across ......

3 ........... other option ...... create the USB hard drive as a boot drive .....

and point to the old drive /home ...... but do not ask it to format the main drive when installing it ......

putting     / 
(root system)
on the USB drive ...... means having the USB plugged in all the time though ..... until you get another drive.

4 .......... Back up as much as possible ........ format it and start again ......... but ensure the drive is ok if its failing
its best to get a new drive


```

---

### Post by Rasa1111 on 2011-01-04
> **matt_symes said:**
> Hi



If you press the escape key on this screen it should display boot up text. What is the last message it displays?

Kind regards

Ok mate, 
 Here is the info I get when doing what you suggested..
(used phone to snap pics, sorry)

First pic~
[ATTACH]180128[/ATTACH]
My focus was the bottom line~
Which is....
>  Buffer I/O error on device sdb, logical block 496255Next pic, My focus was the entire wall of text~ 
[ATTACH]180129[/ATTACH]

Last pic~
 This is the message that pops up, after I insert the Live CD, and right before it boots to the desktop~
(never seen this before)
[ATTACH]180130[/ATTACH]

---

### Post by Rasa1111 on 2011-01-04
23dornot23d,
 I have not upgraded my graphics card or anything else in my PC. 

 Im sorry, Im very confused by the rest of the post? :( 

 Thank you,
 and Thanks all,
your help is greatly appreciated. <3
Sorry for being a simpleton. O_o lol

---

### Post by 23dornot23d on 2011-01-04
No problem with you ,,,, 

I think of all the things it could be but put them down incase anybody else can see things - my bad - from
the output shown ..... you have a problem on the second drive sdb ..... not the first main drive sda .........

Looking at the output ...... looks like a failing drive ..... **sdb** though ......

or its trying to access something that it cannot ..... but it refers to sdb ..... which would be a second drive ......

Could be the sdb (drive is on its way out) ........ 

**Do you have a flash drive plugged in ...... or usb ...... remove it  and try rebooting**

---

### Post by matt_symes on 2011-01-04
Hi

What is on sdb? Does your BIOS recognise that drive?

Kind regards

---

### Post by Rasa1111 on 2011-01-04
> Looking at the output ...... looks like a failing drive ..... **sdb** though ......

or its trying to access something that it cannot ..... but it refers to sdb ..... which would be a second drive ......

Could be the sdb (drive is on its way out) ........ 

**Do you have a flash drive plugged in ...... or usb ...... remove it  and try rebooting**I do not have anything plugged into USB other than my wireless mouse. 
(which is always plugged in)

 I am not sure exactly what sdb is. 

and Im pretty sure I have only the one drive,
no 'second drive' exists.. that i know of.. lol

 I do have a 1TB external drive that I sometimes plug in to access/move files. 
But it only gets plugged in once the PC is up and running. 

 But no second HDD in there. 

                                                  > Hi

What is on sdb?

Kind regards Hey,
 I have no idea! :( lol
Not even sure what it is, to be honest...

 man..
feeling dumb is never fun!

---

### Post by 23dornot23d on 2011-01-04
Ok in that case ,,,,, plug the 1 TB drive in


its got linked to it somehow ,,,,, and is looking for data on it .......... 

I think I understand now what has happened ..... you need to boot with the 1TB 

connected to the machine ........ then hopefully it will boot up ......


My guess is that at some point you did an update and upgrade with the USB plugged in
the boot file ..... grub 2 and the desktop manager probably got updated and is now expecting to see the 1TB drive
and because it is not there , you get all the errors ,,,, its reporting .

---

### Post by Rasa1111 on 2011-01-04
ahh,
 I hope you are right! lol

 I am going to make the attempt now. 
Fingers crossed!  <3

 Thanks again mate.
 Be back shortly..   <3

---

### Post by 23dornot23d on 2011-01-04
Well I hope that is the case ..... seems like it could be .

@matt symes ..... good call ..... asking for the screenshot .

---

### Post by Rasa1111 on 2011-01-04
ahh darn.

No go. lol :(

I dunno..
Guess I should attempt bodhis advice again, and try to get a list of all installed programs on the HDD. 

gahhh

 Thanks though mate,
I really appreciate it. <3

---

### Post by 23dornot23d on 2011-01-04
Is it still showing the same error message at boot ..... or is it different .... ?

The error was definitely pointing to sdb .... 
If you want to continue ..... do a screen shot of the errors again ..... to see if they are the same !!!
It is **sdb** though which is a second drive of some description ......
I wonder if it is not mounting properly ..... could try with both attached ..... boot from the live CD ,,, first

and see if sdb mounts ok ........ 

At some point earlier I think I read that you copied the /home to it, was it unmounted before removing it.

I just looked at the [other thread you are running at the same time]("http://ubuntuforums.org/showthread.php?p=10317449#post10317449") as this - no wonder it gets confusing ....

at least you have a list of programs to install now .... and a backup of /home .......

---

### Post by matt_symes on 2011-01-04
Hi

Those screen shots are odd. Why sdb and not sdb1. It looks like the file system is corrupted (maybe the superblock is corrupted) or the partition table. Open a terminal from the live CD and type

```
sudo fdisk -l
```

(Small L) and post back the results.

Also 

```
sudo dumpe2fs /dev/sda1 | grep -i backup
```

and post back results

Kind regards

---

### Post by Rasa1111 on 2011-01-04
Thanks, 

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f2b81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4661    37431296   83  Linux
/dev/sda2            4661        4866     1648641    5  Extended
/dev/sda5            4661        4866     1648640   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 


> ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sda1 | grep -i backup
dumpe2fs 1.41.12 (17-May-2010)
Journal backup:           inode blocks
  Backup superblock at 32768, Group descriptors at 32769-32771
  Backup superblock at 98304, Group descriptors at 98305-98307
  Backup superblock at 163840, Group descriptors at 163841-163843
  Backup superblock at 229376, Group descriptors at 229377-229379
  Backup superblock at 294912, Group descriptors at 294913-294915
  Backup superblock at 819200, Group descriptors at 819201-819203
  Backup superblock at 884736, Group descriptors at 884737-884739
  Backup superblock at 1605632, Group descriptors at 1605633-1605635
  Backup superblock at 2654208, Group descriptors at 2654209-2654211
  Backup superblock at 4096000, Group descriptors at 4096001-4096003
  Backup superblock at 7962624, Group descriptors at 7962625-7962627
ubuntu@ubuntu:~$ 


---

### Post by matt_symes on 2011-01-04
Hi

> Device Boot Start End Blocks Id System
/dev/sda1 * 1 4661 37431296 83 Linux
/dev/sda2 4661 4866 1648641 5 Extended
/dev/sda5 4661 4866 1648640 82 Linux swap / Solaris

No sdb so it does not look like your partitions are corrupted so i would suggest it's either the file system or a failing hard drive.

Lets perform an fsck but on a backup super block and see how that gets on.

So from the liveCD, make sure sda1 is not mounted.

```
mount | grep ^/
```

if sda1 is mounted unmount by

```
sudo umount /dev/sda1
```

and then lets check the partition.

```
sudo fsck -b 32768 /dev/sda1
```

Kind regards

---

### Post by Rasa1111 on 2011-01-04
Thanks Matt,

 Ok, sda1 not mounted..

> ubuntu@ubuntu:~$ sudo fsck -b 32768 /dev/sda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
One or more block group descriptor checksums are invalid.  Fix<y>? 

 It's asking me if i want to 'fix' something?

---

### Post by matt_symes on 2011-01-04
Hi

Select yes every time it asks you to fix.

Kind regards

---

### Post by Rasa1111 on 2011-01-04
ok, thanks a lot man. 
I chose "yes" must have been hundreds of times..
(most use my "y" key has ever gotten!)  lol

 Ok, 
Once all that was done.. 
This is what I see now~
> /dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sda1: 2302775/2342912 files (0.1% non-contiguous), 8618451/9357824 blocks
ubuntu@ubuntu:~$ 


 What should I do now? 

 Thanks so much. <3

---

### Post by dmizer on 2011-01-04
Please post the contentes of /etc/fstab. Not the live CD /etc/fstab, but the /etc/fstab file from the disk that's not booting.

Also please post the output of:
```
sudo blkid
```

---

### Post by matt_symes on 2011-01-04
Hi

> **dmizer said:**
> Please post the contentes of /etc/fstab. Not the live CD /etc/fstab, but the /etc/fstab file from the disk that's not booting.

Also please post the output of:
```
sudo blkid
```

+1. Lets have a look at how your partitions are being mounted at startup.

Kind regards

---

### Post by Rasa1111 on 2011-01-04
> **dmizer said:**
> Please post the contentes of /etc/fstab. Not the live CD /etc/fstab, but the /etc/fstab file from the disk that's not booting.

Also please post the output of:
```
sudo blkid
```

 Hi,

 I'm sorry,
 I don't quite understand how to do that. 

"sudo blkid" Im sure I can handle.. 
which would be 
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="0fb52879-78ba-4ae7-bfeb-447deb35bdeb" TYPE="ext4" 
/dev/sda5: UUID="8dd1ec90-e81f-485a-95d2-3f15c8af2cca" TYPE="swap" 



But I am unsure of how to post the contents of /etc/fstab "from the disk that's not booting'. 

Is there a simple command I can use? 

Thank you. 

@Matt~
Is there anything else I should do now after I "fixed" everything? 
(last post on previous page).

 Thanks soo much guys,
you're awesome. <3

---

### Post by dmizer on 2011-01-04
Even though the disk is not booting, you can still access the disk contents from the live CD. Just browse to the disk with Nautilus and look for /etc/fstab.

---

### Post by matt_symes on 2011-01-04
Hi

Cross your fingers and reboot. It would be useful to see your fstab first though. Just to be sure.

Kind regards

---

### Post by dmizer on 2011-01-04
> **Rasa1111 said:**
> @Matt~
Is there anything else I should do now after I "fixed" everything? 
(last post on previous page).

I'm trying to determine if you've actually fixed anything at all. The problem here is that your boot error is for a different disk than you fixed. So the disk problems you fixed could simply be a result of you having to manually power off the machine several times.

This means that the REAL problem may still exist. So, before you reboot I'd like to get a better picture of your disk layout as seen by your non-booting system.

---

### Post by Rasa1111 on 2011-01-04
> Even though the disk is not booting, you can still access the disk  contents from the live CD. Just browse to the disk with Nautilus and  look for /etc/fstab. Hey, thanks. 

 I know I can access the partition,
but I was just unsure of how to "post the contents" of said location. 

I think i have it though..
(sorry for being simple) lol

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=0fb52879-78ba-4ae7-bfeb-447deb35bdeb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8dd1ec90-e81f-485a-95d2-3f15c8af2cca none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0 
> This means that the REAL problem may still exist. So, before you reboot  I'd like to get a better picture of your disk layout as seen by your  non-booting system.


 is the fstab info what you mean? 

> Hi

Cross your fingers and reboot. It would be useful to see your fstab first though. Just to be sure.

Kind regards
 :) Will try that after you guys examine my fstab. lol <3
 Thanks again. <3

---

### Post by albert s on 2011-01-04
> **Rasa1111 said:**
> Hey mate,

 How am I supposed to do that, when I can only get into the PC via LiveCD?

 The CD needs to be in to do anything.. 
So, I could download the iso, I guess... 
But since my CD drive is already occupied.. 
the rest seems 'impossible'. 

** @ 23dornot23d**~
 Thanks, <3

 I had actually not even deleted anything yet,
 I was going to wait until after I restarted the PC,
which never happened.. 

 There is currently 2.6 GB of unused space on the HDD~
Gparted shot~
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=180126&d=1294178212[/IMG]

 Anything else Im missing for the shot? 

@ Nytram, Thanks mate, Good to know! <3

 Many thanks for all replies. <3


on that screenshot I dont see a /  partition  or a /home  , so I would also agree with the previous about maybe needing your other drive plugged in too,
if it still doesnt work you may need to play about with bios settings or something to get it to try and boot from USB .

---

### Post by matt_symes on 2011-01-04
Hi

Your fstab looks fine. 

Kind regards

---

### Post by Rasa1111 on 2011-01-04
> **matt_symes said:**
> Hi

Your fstab looks fine. 

Kind regards

 Awesome.
 So I should attempt a reboot now?  :confused:

:) <3

---

### Post by matt_symes on 2011-01-04
Hi

Yes, reboot. The only thing i am worried about is Grub, but... Press the escape key again while booting to see the boot text.

Kind regards

---

### Post by Rasa1111 on 2011-01-04
Ok,

 Rebooted..
to no avail. lol  :(
damn. 

I guess I attempt to re-install now,
and just hope that it is not the HDD.  lol O_o

 Thanks soo much for all your help and time,
i appreciate it greatly. <3 <3 <3

---

### Post by dmizer on 2011-01-04
> **Rasa1111 said:**
> Ok,

 Rebooted..
to no avail. lol  :(
damn. 

I guess I attempt to re-install now,
and just hope that it is not the HDD.  lol O_o

 Thanks soo much for all your help and time,
i appreciate it greatly. <3 <3 <3

It's very possible the disk is bad. I recommend using the smartctl tools to check the disk more deeply than fdisk. More on that here: [http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart](http://www.linuxjournal.com/magazine/monitoring-hard-disks-smart)

Sorry I didn't reply more quickly. I'm at work and got caught on the phone.

---

### Post by Rasa1111 on 2011-01-04
Hey dmizer,
 thanks man,
 no apologies mate. <3

Ok,
 So my only questions now, are..
 1.  I would need to have a working install first, in order to use the smartctl tools, correct?
and
2. If indeed.. the disk is 'bad'..
Would that prevent me from doing a fresh install? 

Or would the install work...
but have a good chance of failing soon after? 

 or would it just tell me something like..,
 *"Sorry, cannot complete install, your disk is finished!!"* ?  lol 

Ive read through your link.. 
and it feels rather complicated, especially for someone like myself who was confused on how to post his fstab info! :lol: 
haha. 

 I really appreciate it though, 
and If I get an install going properly.. 
I will do my best to use the tool and get what info I can. 

and If the disk is failing.. 
my next endeavour will be to replace it ..
(after i learn exactly how I would do so). lol

Many thanks. <3

---

### Post by dmizer on 2011-01-04
You can run smartctl from the live cd, just use the synaptic package manager to install smartmontools. There's also a GUI interface called gsmartcontrol that may make things much easier for you.

If you run a test, and you don't understand the output, simply post it here and we can review it and give you feedback. :)

Edit:
I've just installed gsmartcontrol, and it looks very useful. I highly suggest using it rather than trying to do things manually via the command line.

---

### Post by 23dornot23d on 2011-01-05
Not sure I am following this now ..... the error was related to

sdb

[IMG]http://img710.imageshack.us/img710/9691/81428768.jpg[/IMG]


So ....  


sda ..... was fixed ...... altered .... 

( a 40 gig drive is possibly old and maybe it does need replacing - so to monitor it may be a good idea )
personally I too would want to know too if my sda drive was failing ......

but the error as far as I can see pointed to the sdb the second drive ,,,,, and I doubt the (sdb) 1 TB drive
is old ..... but would have liked to have seen if the new errors are still related to this ....

or are the latest errors now to sda the first 40 Gig drive.  

_________________________________________________________


Now we are going to add a smart monitor for sda .... 

( why not get a new drive - the 40 Gig is probably ready for replacing and rules out that for future problems too )
if it is not too expensive to do ....

**Is it A desktop machine or laptop **..... desktops drives are usually dead easy to change  .... 
laptops are not too bad ,,,, but its getting a compatible drive that may be a problem.
 
[B]But we have not solved the error - which seems to be relating to sdb
[/B]


it may have linked to a swap area on sdb ..... that it was having problems with ..... because it is not attached 
or it has problems with it = errors on sdb ( 1 TB drive ) may then appear ...... who knows .... just a thought.

**What were the new errors** ....... after all the work you did ..... ?

---

### Post by matt_symes on 2011-01-05
Hi

> 
Not sure I am following this now ..... the error was related to

sdb

So .... 

sda ..... was fixed ...... altered .

I see where you are coming from, but you mount a partition (sdb1) not a device (sdb). If you look at the screen shot as well you will see that the fsck check had not finished on sda1. It's odd i know.

I think it's definitely worth checking out your suggestion. I thought Rasa tried to boot with sdb plugged in. What is worrying me more is the mount point shown for sda1 in gparted.

Kind regards

---

### Post by 23dornot23d on 2011-01-05
Running the bootscript file with both drives plugged in may be useful ....

more info the better on things like this ..

Seems odd ...... 

I still think it got linked to the second drive - sdb

How else would it know sdb exists ....... ?

I use USB drives a lot and adding and taking them away may cause problems
especially if a upgrade is done with the USB plugged in 
which it can do automatically when upgrading  .... 
and the user may not realize or be aware that it has done this .. 
and unplugging it after that may cause problems,

I boot from my USB .... and that too is an option here ..... if there is a worry about the main 40 gig drive ..... 

____________________________________________________________


I see what you are saying about the mount point ..... 

running the bootscript may help here to clarify things ......

I personally would check sdb is ok ..... 
find some free space on it and add a new version of linux .... 
with a separate /home

Also to boot from the sdb .

Rasi1111 can still access all the data on sda from this setup 


until such a time as a replacement is found .......for sda .... if
it is shown that this a problematic drive.

---

### Post by dmizer on 2011-01-05
> **23dornot23d said:**
> but the error as far as I can see pointed to the sdb the second drive ,,,,, and I doubt the (sdb) 1 TB drive
is old ..... but would have liked to have seen if the new errors are still related to this ....

or are the latest errors now to sda the first 40 Gig drive. 

According to [this]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-June/001061.html") article, the /dev/<blockdevice> naming convention has depreciated which is why we are now using UUID instead. Because of that, the /dev/<blockdevice> convention is no longer trustworthy. On some boots, it may be /dev/sda1, on others it may be /dev/sdb1.

Since the UUIDs match in both the live CD boot session and in the system disk's /etc/fstab, it's safe to say that there is no other drive involved here. Also, since the system disk's /etc/fstab doesn't show any other disks, the system should boot fine without the external drive attached.

Long story short, the cause of the problem is most certainly not the external disk.

Related (invalid) bug with lots more information here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119233](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119233)

---

### Post by 23dornot23d on 2011-01-05
Interesting .... so with only one hdd device running .... sda1

The system is reporting a **I/O error on sdb** .......

but as sdb does not exist on boot   ...... ? (how can it switch the id's)

or can we take it that the error message that was posted by Rasa1111 .... is giving wrong information ....

** This is from what you say and the links you provided ...... your pointing out that error message is of no use whatsoever .....**

_________________________________________________

[B] We cannot base anything on that error message ..... if the error message means nothing.

( But sdb .. as you are pointing out is actually sda - in the error message ..... 
** which makes no sense at all to me ** ...... 
but if that is the case we would have to ignore what the error messages show as regards drive identifications.


So .....the options left to the USER are ......

1 ...... **sda1 really needs replacing** ...... if in fact sda (4O Gig) is a problem disk and caused the first problems to occur.
 
2 ...... sdb as you say is not a problem - ** and it is the error message that is giving the wrong information ** - 

so if thats true a new OS could be installed onto sdb to get Rasa1111 up and working again that is if the USER wants to go this way.
( So what I asked - **that is re-checking error messages** is a waste of time as the error messages are false - 
*if it was mine ....*
I would prefer to check to make sure there is not a problem with sdb then the USER is safe to continue and install to it if the USER wants to ). 

3 ....... **Rasa1111 could install a clean version of LINUX onto sda1 with smartmon working and watch out and see if the drive is getting any worse ** .....  
Then and if once proved the drive is faulty by smartmon ...... 

The USER can then resolve it by replacing the drive and re-installing a new version of LINUX onto the new one. 

or in the case it is not a failing 40 Gig hard drive ... ( and maybe the error message was correct ) a problem may still exist.

_This is unless there are some more options ..... _

I think these 3 options cover what could be done .... to get the USER working again ....... 

[I]ps ...
I have seen the problem with drives swapping letters .... 
but I believe you need both drives plugged in at boot up for this to occur .....

Rasa1111 I think said that they use the 1TB drive by adding it after boot up.
[/I]

---

### Post by dmizer on 2011-01-05
> **23dornot23d said:**
> [I]ps ...
I have seen the problem with drives swapping letters .... 
but I believe you need both drives plugged in at boot up for this to occur .....

No, this is not the case.

Rasa1111's computer only officially has one hard drive attached to it. How do we know this? [There is only one listing for a hard drive in /etc/fstab]("http://ubuntuforums.org/showpost.php?p=10317817&postcount=37"). The second hard drive is only soft-mounted by udev after the system is up and running. The error posted earlier occurs on boot, for that to be a real problem the following conditions must occur:
1) The external hard drive must have an /etc/fstab entry.
**AND**
2a) The external hard drive is disconnected.
2b) The external hard drive has errors.

The reason this computer may be showing different blockdevice notations is simply because it's essentially being booted by two different OS. The hard drive install reads the blockdevice one way, and the live CD reads the blockdevice another.

The important part to see here is:
[LIST]
[*][There is only one drive listed in /etc/fstab]("http://ubuntuforums.org/showpost.php?p=10317817&postcount=37").
[*][The blkid test]("http://ubuntuforums.org/showpost.php?p=10317746&postcount=33") shows matching UUID numbers to the drive listed in /etc/fstab.
[*]This means that sda (livecd) = sdb (install).
[/LIST]

Edit:
I just happened to think of another situation where there could be a problem. If grub is configured to boot to the blockdevice rather than via UUID. To verify this, please post the contents of /boot/grub/menu.lst (from the system disk)

---

### Post by Rasa1111 on 2011-01-08
Hey all,
 Thank you soo much for all your help!
It is greatly appreciated! 
You guys are beautiful!

 Well,
 Everything is back to "normal"..
But I ended up just re-installing. 

 It was driving me nuts running from the liveCD constantly. 
And everything I tried..
produced the same results as previously mentioned. 

No idea what went wrong.. 
But since the new install.. 
(couple/few days ago)
I have had no issues whatsoever. 

The PC is running beautifully, 
(better than ever, I do believe)..
So i don't know what to think..

 I am still seriously considering buying a new HDD though. 
I mean... even if this one is still "good"..
I could definitely use a bigger drive than 40GB. lol

 I do have plenty of external space..
but really would be nice to have more internal. 

Ive never seen a tech. community so able and willing to help others who need it, as this one. 

You guys are special! really!
(not in the 'little bus' way.) lol
 More in the "i love you guys" way! :lol:

Thanks soo much, 
You guys rock! <3

---

### Post by 23dornot23d on 2011-01-10
Glad to hear that you got it re-installed and are having no more problems ... :D

maybe it was just a glitch between drives ..... :confused:

I keep buying new USB drives .... have 3 now ..... the main one I use is a 500 Gig seagate

( The 1 Terra IOMEGA that I have seems a little slow .... and the 250 Gig drive has no fan and in Summer gets hot.)

But if you do get a new internal ..... that would be even faster than USBs .... and if its a Desktop machine you could possibly
add it as well as the 40 Gig .... if they match each other ..... 
( if its a laptop then as above .... USBs or replace the internal drive - but as that does not appear a problem now  )

Best of luck in your future exploits using it ..... bye for now .. ):P

---

