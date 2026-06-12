---
title: "Weird partitions"
date: 2010-02-05
forum: General Help
---

### Post by ratcheer on 2010-02-05
So, I finally understand why I couldn't get Clonezilla to work on my system. But, I am more baffled than ever.

You see, my system has been in great working order for months. I am running 9.10 32-bit and I keep everything maintained on a daily basis. I just updated to kernel 2.6.32-19 and, like I say, everything is working pretty much perfectly.

But, yesterday, I volunteered to help with some official Canonical Ubuntu testing. This morning, I got an email from them that they want me to do the work and giving me instructions on how to proceed. The first thing to do is free up some disk space in order to have a special partition on which to install their testing kernels.

So, I downloaded their suggested tool for doing this, gparted. And, when I ran gparted, the first thing I discovered is that my disk drive has absolutely nothing on it! No partitions, at all. It only sees an empty device, /dev/sda. This is exactly what Clonezilla told me a couple of months ago - no partitions could be located to be backed up.

However, I and Ubuntu think I do have partitions:

```

$ df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     19G  1.5G   16G   9% /
udev         tmpfs    502M  360K  501M   1% /dev
none         tmpfs    502M  204K  501M   1% /dev/shm
none         tmpfs    502M  328K  501M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw
/dev/sda3     ext3     28G  3.2G   23G  12% /home
/dev/sda4     ext3     27G  3.8G   22G  15% /usr

```Does anyone have any idea what is going on, making Clonezilla and gparted see no partitions on my disk?

Thank you,
Tim

---

### Post by audiomick on 2010-02-05
It wont answer the question of why gparted isn't seeing the partitions, but show us the output of
```
sudo fdisk -l
```
for a different view of the partition structure.
The last character in the command is a lower case L, not a figure one.

---

### Post by rnerwein on 2010-02-05
hi
df is quite nice but was

fdisk -l /dev/sda

will tell you
ciao

ups audiomick was faster then i

---

### Post by ratcheer on 2010-02-05
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sda2             123        2554    19535040    5  Extended
/dev/sda3            2555        6201    29294527+  83  Linux
/dev/sda4            6202        9729    28338660   83  Linux
/dev/sda5             123        2554    19535008+  83  Linux

---

### Post by audiomick on 2010-02-05
curious....
The fdisk output looks fairly normal. It is not that common to have the swap partition first, but I have seen that recommended as a speed improver, so I don't think it is a problem.

I'm at a bit of a loss, to be quite honest. I would probably burn a gparted live CD and see what that says. You can get an iso from their site
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Another thing occurs to me:
In system> administration> disk utility
you can start palimpsest, which is a different disk tool. Open that and see if it can see the partitions.

---

### Post by ratcheer on 2010-02-05
> **audiomick said:**
> curious....

I'm at a bit of a loss, to be quite honest. I would probably burn a gparted live CD and see what that says. 

A gparted Live CD is what I used, version 0.5.1-1 dated January, 2010

Tim

---

### Post by audiomick on 2010-02-05
> **ratcheer said:**
> A gparted Live CD is what I used, version 0.5.1-1 dated January, 2010

Tim
Oh, ok, I thought you had installed it and were running it from the Ubuntu install.
What does the disk utility see?

---

### Post by ratcheer on 2010-02-05
[IMG]file:///tmp/moz-screenshot.png[/IMG][IMG]file:///tmp/moz-screenshot-1.png[/IMG]

---

### Post by Highest on 2010-02-05
New to this forum and you guys seem educated. I made a post with this question but no one answers.

I installed Ubuntu latest version and everything is sweet. Except now i want to remove my single vga nvidia vid card which ubuntu saw and set up for me upon installing ubuntu. Now i want to switch to a ATI better card and am having trouble. I cant run terminal cause i cant just remove my working vid card? Any help would be great>

---

### Post by Ordes on 2010-02-05
truly weired.. 

but your disk utility sees the correct partitions...
did you try to run gparted from inside your system... just curious if an installed gparted would see the partitions.. 

normally there should be no difference...but in this case might be worth a try to get a checkpoint-list...

edit:
>> did u  choose your correct harddrive in the gparted? >> top right corner ?..

>> but anyways, weired that clonezilla had the same output..

---

### Post by rnerwein on 2010-02-05
hi
is it possible for you to install "testdisk"

sudo apt-get install testdisk     ( - Scan and repair disk partitions )

try this, it's a pretty - but also a little dangerous tool
ciao

---

### Post by audiomick on 2010-02-05
@ highest: it is really not good form to jump in on someone elses thread. If you haven't had an answer in your own thread after a day or so, just put another post in it to bring it back up to the top.

@ratcheer: I have to cook dinner now, so I will be away for a while, but I am going to PM a couple of others to have a look here. Your problem is really a bit strange...

---

### Post by ratcheer on 2010-02-05
Thanks. I hope you have a nice dinner. It is still early afternoon, here. ;)

Tim

---

### Post by Ordes on 2010-02-05
late night here... going to bed now.. 3am... but i am curious about this...gonna check tomorrow, ... good luck so far ;)

---

### Post by warfacegod on 2010-02-05
Is the Properties windows reading the data properly?

If you have it available, try using an older kernel. One from the 31- set if possible.

---

### Post by Jackzor on 2010-02-05
I am afraid that I will not be of any help. I just want to throw something out there.

About 6 months ago I was running windows 7 and my brother wanted to dual boot Ubuntu for me. So, I was willing to give ubuntu another try since my childhood playing. Well when he booted up Gparted it came up with 7 or 8 different blank partitions. This was before ubuntu was ever even installed on the hard drive. It was simply windows 7 just a c drive 250gb out of 250 gb. I'm not sure what happened. I honestly believe that gparted read it wrong.

He ended up halfway installing grub on my computer So I couldn't boot it at all.

I had to format and I ended up doing the dual boot just fine on my own.

---

### Post by Leppie on 2010-02-05
i have never ever used the gparted cd myself.
why don't you use gparted from ubuntu? you can just install it from the repos and if you can see all the partitions from your ubuntu install i'm sure gparted running from that install will be able to access all those partitions as well.
to install gparted:
```
sudo apt-get install gparted
```
to launch it:
```
gksudo gparted
```
or just launch it from the menu: System>Administration>Gparted

---

### Post by ratcheer on 2010-02-05
Ok, gparted within Ubuntu does see my partitions. But, how does this help me? It is my understanding that I cannot resize a partition when it is mounted and, with Ubuntu running, they are all mounted. That is the purpose of the Live CD, to be able to change your partitions when they are not being used.



Tim

---

### Post by Leppie on 2010-02-05
> **ratcheer said:**
> Ok, gparted within Ubuntu does see my partitions. But, how does this help me? It is my understanding that I cannot resize a partition when it is mounted and, with Ubuntu running, they are all mounted. That is the purpose of the Live CD, to be able to change your partitions when they are not being used.
then use an ubuntu livecd. they are more flexible anyways i think as you can install things if you need them.
you can use the same commands to install gparted when booting off the livecd. the only difference is that the installation isn't persistent (but the partition modifications will be).

---

### Post by warfacegod on 2010-02-05
> **ratcheer said:**
> Ok, gparted within Ubuntu does see my partitions. But, how does this help me? It is my understanding that I cannot resize a partition when it is mounted and, with Ubuntu running, they are all mounted. That is the purpose of the Live CD, to be able to change your partitions when they are not being used.



Tim

The only partition you won't be able to resize from within Linux is the one that your OS is running on. Gparted can unmount any other partition or drive that you need it to.

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> The only partition you won't be able to resize from within Linux is the one that your OS is running on. Gparted can unmount any other partition or drive that you need it to.
very true :)

---

### Post by ratcheer on 2010-02-05
So, I can unmount /home with Ubuntu running and resize it? That sounds scary.

Tim

---

### Post by audiomick on 2010-02-05
Hi.
Yes, it is a disconcerting idea, but it should work. It would interest me to follow Leppies suggestion to try gparted from a live CD.

I see two things here: one is to do your partitioning so that you can do the testing, the other is why live CDs aren't seeing the partitions, i.e. clonezilla and the gparted CD.

I am also a bit more comfortable with partitioning from some kind of live CD, if only because I then don't have to worry about un-mounting.

---

### Post by ratcheer on 2010-02-05
Ok, I will try it. If I kill my system....

Tim

---

### Post by audiomick on 2010-02-05
I should also have said, if no-one has mentioned it, and again if someone has, one should always back up critical stuff before any partitioning work. It is generally not an issue, but there is always a small risk.

---

### Post by ratcheer on 2010-02-05
It wouldn't let me do it, anyway. "Device is busy". I am kind of glad.

There's nothing really important on this machine, except all the time I've put into building it. It was my son's old WinXP box, but he got a new Macbook Pro 17" to take to college. I formatted the disk and installed Ubuntu 9.04. Eight months later and here I am. :p

As you can probably infer, once I tried to use Clonezilla to back it up, but it couldn't see the partitions, either.

Very strange.

Tim

---

### Post by audiomick on 2010-02-05
Lucky son...
I can't really make a rhyme of it, I must say. The only thing left would be to try the Ubuntu live CD route.
That still doesn't answer why clonezilla and the Gparted CD can't see the partitions, though.

---

### Post by warfacegod on 2010-02-05
I wonder if a Live environments' inability to not see partitions is some strange quirk of your computer and/or hardware set up. Possibly some kind of "locking feature".

---

### Post by audiomick on 2010-02-05
> **warfacegod said:**
> I wonder if a Live environments' inability to not see partitions is some strange quirk of your computer and/or hardware set up. Possibly some kind of "locking feature".
Hmmm...
Might be worth having a look through the BIOS, maybe?

---

### Post by ratcheer on 2010-02-05
Well, I originally formatted the disk and partitioned it for Ubuntu using the 9.04 Live CD, so maybe it will work, again. I'm off to try it.

Thanks very much for all the help, everyone!

Tim

---

### Post by warfacegod on 2010-02-05
Or even an actual hardware switch on the motherboard. I have seen some weird stuff in older computer models.

---

### Post by Leppie on 2010-02-05
> **ratcheer said:**
> Well, I originally formatted the disk and partitioned it for Ubuntu using the 9.04 Live CD, so maybe it will work, again. I'm off to try it.

Thanks very much for all the help, everyone!

Tim
if you download and burn a karmic livecd, i'm positive it will recognize all your partitions (unless you've got something very very exotic on the drive ;)).

---

### Post by ratcheer on 2010-02-05
Ok, it is good news, bad news. The good news is that the Karmic Live CD does indeed run gparted and all the partitions are seen and can be manipulated. The bad news is that I already have the maximum number of primary partitions on the disk (4), so even if I shrink one, I still cannot add another one. Poor planning by a newbie. My only extended partition is the one containing / (root) and it is the smallest one I have.

I guess that is that. I don't want to try to back up everything and repartition and restore. I will just have to live with things the way they are.

Tim

---

### Post by Leppie on 2010-02-05
> **ratcheer said:**
> Ok, it is good news, bad news. The good news is that the Karmic Live CD does indeed run gparted and all the partitions are seen and can be manipulated. The bad news is that I already have the maximum number of primary partitions on the disk (4), so even if I shrink one, I still cannot add another one. Poor planning by a newbie. My only extended partition is the one containing / (root) and it is the smallest one I have.

I guess that is that. I don't want to try to back up everything and repartition and restore. I will just have to live with things the way they are.

Tim
what is your exact partition layout?
if you're root partition is next to the /home partition you most probably can add another partition into the extended partition.

---

### Post by warfacegod on 2010-02-05
How many partitions did that other guy have? 18? With 4 swaps?

---

### Post by audiomick on 2010-02-05
> **Leppie said:**
> what is your exact partition layout?
if you're root partition is next to the /home partition you most probably can add another partition into the extended partition.
@ Leppie: There is a gparted screen shot in post #18

@ ratcheer: all is not lost, but it will be a bit of dicking around to get it done. You would have to shrink sda4, then move the right side of sda3 to include the now empty space, then the left side of sda3 to make empty space again, then grow sda2, the extended partition, into the space. Then you can create a new logical in sda2 for your test system. You don't need a new swap, the new install is able to use the existing one.

I would personally do that really one step at a time, maybe even boot into the existing install in between to make sure I haven't shot anything down.

And back up anything critical before you start doing anything, as always when you change your partitions.

---

### Post by Leppie on 2010-02-05
> **warfacegod said:**
> How many partitions did that other guy have? 18? With 4 swaps?
something like that... even though you could have virtually illimitate logical partitions in your extended partition.

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> @ Leppie: There is a gparted screen shot in post #18
thanks, i'm getting old... lol

> **audiomick said:**
> @ ratcheer: all is not lost, but it will be a bit of dicking around to get it done. You would have to shrink sda4, then move the right side of sda3 to include the now empty space, then the left side of sda3 to make empty space again, then grow sda2, the extended partition, into the space. Then you can create a new logical in sda2 for your test system. You don't need a new swap, the new install is able to use the existing one.
what i personally would do is copy the contents of the /usr partition to the /usr folder on the root partition (sda5). you could then either use sda4 for the new test system, or move the /home partition all the way to the right. the latter will give you the advantage that you can add more partitions as they will be added into the extended partition. obviously you also need to remove the /usr entry in your fstab ;)

---

### Post by audiomick on 2010-02-05
That sounds like an elegant solution. I'll just put my gas torch and four by two away then...;)

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> That sounds like an elegant solution. I'll just put my gas torch and four by two away then...;)
why? a gas torch is always good fun :D

---

### Post by warfacegod on 2010-02-05
I prefer baseball bats over 4x2's any day. The corners tend to hurt my hands when I club somebody. Of course, in a pinch, I'll go for a pointed stick just as well. (In the U.S. there called 2x4's)

---

### Post by Leppie on 2010-02-05
isn't it better to hit someone with a 4x4? :P

---

### Post by warfacegod on 2010-02-05
> **Leppie said:**
> isn't it better to hit someone with a 4x4? :P

Corners thing. Besides, I played baseball for 9 seasons when I was a kid, I *know* how to swing a bat!

---

### Post by audiomick on 2010-02-05
> **Leppie said:**
> isn't it better to hit someone with a 4x4? :P
Only if it has a bull bar...

---

### Post by Leppie on 2010-02-05
> **audiomick said:**
> Only if it has a bull bar...
how a bout a nice spiky grill?

---

### Post by ratcheer on 2010-02-05
Ok, so post #38 is the plan. I'll work on it, but it may be tomorrow before I really get into it.

Thanks a million!

Tim

---

### Post by Leppie on 2010-02-05
let us know if you need help.

---

### Post by ratcheer on 2010-02-05
> **Leppie said:**
> let us know if you need help.

Thanks, I really appreciate it.

Tim

---

### Post by Ordes on 2010-02-05
for the backup... you could use remastersys

as your overall data is not that much, u could put everything into the liveISO (including /home, /usr) .. and than put that on a usb drive, with the usb live disk creator..

restart, format and partition hdd, install and you have your running system back in minutes with all your stuff...

if you dont have a big enough usb drive, you could exclude /home... make the backup;
backup /home on a different medium e.g (DVD). Than reinstall, copy /old-home into /new-home

Edit:
>> remastersys repo:
[http://www.geekconnection.org/remastersys/ubuntu.html](http://www.geekconnection.org/remastersys/ubuntu.html)

>> remsys backup is pretty straightforward, and gui supported. Two clicks to start your backup

---

### Post by warfacegod on 2010-02-05
> **ratcheer said:**
> Ok, so post #38 is the plan. I'll work on it, but it may be tomorrow before I really get into it.

Thanks a million!

Tim

I like post #41 for a plan.

This works for a backup:

[http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

---

### Post by Leppie on 2010-02-06
who needs a backup? just a waste of precious disk space :P

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> who needs a backup? just a waste of precious disk space :P

Stop trying to corrupt the new guys:tongue:. Just because the he's from Alabama doesn't make him a Linux Redneck. Don't think we should discount the possibility either though.

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> Stop trying to corrupt the new guys:tongue:. Just because the he's from Alabama doesn't make him a Linux Redneck. Don't think we should discount the possibility either though.
you calling me a linux redneck? i never do backups...:lolflag:

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> you calling me a linux redneck? i never do backups...:lolflag:

I think we've established the Linux Rednekkedness of pretty much everyone in the "Stupid" thread. That definitely includes you!:rolleyes:

---

### Post by willowave on 2010-02-06
me too? lol yeah who needs backup when it's just going to break anyways.

---

### Post by willowave on 2010-02-06
btw, the multiboot 9 os from [www.pendrivelinux.com]("http://www.pendrivelinux.com") is damn handy for stuff like this. it's got gparted and 3 versions of ubuntu on it, plus a few other handy os's. It's saved my butt more than once. As my butt needs saving quite often as you've seen.

---

### Post by warfacegod on 2010-02-06
> **willowave said:**
> me too? lol yeah who needs backup when it's just going to break anyways.

Yup, you too! With your ability to break a system within minutes, backups are probably pointless.

---

### Post by Leppie on 2010-02-06
> **willowave said:**
> btw, the multiboot 9 os from [www.pendrivelinux.com]("http://www.pendrivelinux.com") is damn handy for stuff like this. it's got gparted and 3 versions of ubuntu on it, plus a few other handy os's. It's saved my butt more than once. As my butt needs saving quite often as you've seen.
multiboot 9? haven't been able to find that one...

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> multiboot 9? haven't been able to find that one...

This one maybe?

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/]("http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/")

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> This one maybe?

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)
i saw that one, but that's not multiboot 9... wonder what that would be...

---

### Post by ratcheer on 2010-02-06
I am making progress on the work. I copied the contents of /usr from its partition (sda4) to a folder in the root partition (sda5). I could not rename /usr with the installed Ubuntu running, so I went to the Live CD and renamed it to /usrold. Then, I moved the /usr I had copied to /usrnew up a level, so I now have a /usr with all its contents in the root partition.

Next, I started gparted (still booted to Karmic LiveCD), and unmounted sda4 and deleted it. Now, I am moving sda 3 to the far "right", so that the new unallocated space will be adjacent to sda5. This operation looks like it will take 15 - 20 minutes.

Finally, I plan to enlarge the primary partition that root is in, without expanding the root extended partition. This should give me the space to create new extended partitions, as needed. At least, that is the plan.

So far, so good.

Tim

---

### Post by Leppie on 2010-02-06
good, let us know if you encounter any difficulties.

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> Yes, please do. We like difficulties. More beanses.
beanses are the stuff :)

---

### Post by ratcheer on 2010-02-06
Ok, I am done and my system still lives. ;)

```

df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     19G  5.1G   13G  30% /
udev         tmpfs    502M  360K  501M   1% /dev
none         tmpfs    502M  264K  501M   1% /dev/shm
none         tmpfs    502M  332K  501M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw
/dev/sda3     ext3     28G  3.2G   23G  12% /home

```Oops. sudo no longer works. :eek: **So, I do need more help.**

```

sudo fdisk -l
sudo: must be setuid root

```Tim

---

### Post by warfacegod on 2010-02-06
> **ratcheer said:**
> Ok, I am done and my system still lives. ;)

```

df -Th
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda5     ext3     19G  5.1G   13G  30% /
udev         tmpfs    502M  360K  501M   1% /dev
none         tmpfs    502M  264K  501M   1% /dev/shm
none         tmpfs    502M  332K  501M   1% /var/run
none         tmpfs    502M     0  502M   0% /var/lock
none         tmpfs    502M     0  502M   0% /lib/init/rw
/dev/sda3     ext3     28G  3.2G   23G  12% /home

```Oops. sudo no longer works. :eek: **So, I do need more help.**

```

sudo fdisk -l
sudo: must be setuid root

```Tim

Try wiping your hard drive and starting from scratch.

---

### Post by warfacegod on 2010-02-06
Scratch that, just kidding.

---

### Post by warfacegod on 2010-02-06
Have a look at this:

[http://ubuntuforums.org/showthread.php?t=1132821&highlight=setuid+root]("http://ubuntuforums.org/showthread.php?t=1132821&highlight=setuid+root")

---

### Post by ratcheer on 2010-02-06
I have looked at it and, it seems to be a Catch 22. To edit the file to fix it, I am supposed to "sudo visudo". But, I can't sudo.

Tell me what I am missing.

Thanks,
Tim

---

### Post by Leppie on 2010-02-06
did you remove the reference to /usr (sda4) from your fstab?

---

### Post by ratcheer on 2010-02-06
> **Leppie said:**
> did you remove the reference to /usr (sda4) from your fstab?

Yes, I did. But, I am still getting a reference to something not being found what I boot. But, it then boots just fine.

I fixed the problem with sudo and I understand what went wrong. When I copied /usr from the old sda4 partition to a subdirectory of root, the permissions were not preserved. So, while sudo is now fixed, I am worried about how many other things might be screwed up?

```

sudo fdisk -l
[sudo] password for tim: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sda2             123        6084    47889765    5  Extended
/dev/sda3            6085        9729    29278462+  83  Linux
/dev/sda5             123        2554    19535008+  83  Linux
/dev/sda6            2555        3832    10265503+  83  Linux

```

Tim

---

### Post by Leppie on 2010-02-06
> **ratcheer said:**
> Yes, I did. But, I am still getting a reference to something not being found what I boot. But, it then boots just fine.
it would be good to know what the exact message is.
try going through dmesg (can be a whole lot to read through):
```
dmesg | less
```

> **ratcheer said:**
> I fixed the problem with sudo and I understand what went wrong. When I copied /usr from the old sda4 partition to a subdirectory of root, the permissions were not preserved. So, while sudo is now fixed, I am worried about how many other things might be screwed up?
did you create a backup of the partition first? how did you resolve the sudo issue (to see if there might be other issues)?

---

### Post by ratcheer on 2010-02-06
> **Leppie said:**
> 
did you create a backup of the partition first? how did you resolve the sudo issue (to see if there might be other issues)?

I am afraid I didn't create a backup. I fixed it by going to root in recovery mode and commanding: chmod 4755 /usr/bin/sudo

Which means any other program that got its permissions messed up is not fixed.

Tim

---

### Post by ratcheer on 2010-02-06
I don't see anything in the dmesg output that rings any bells. I will watch carefully, the next time I reboot. It goes away pretty fast, though.

Tim

---

### Post by Leppie on 2010-02-06
> **ratcheer said:**
> I am afraid I didn't create a backup. I fixed it by goint to root in recovery mode and commanding: chmod 4755 /usr/bin/sudo

Which means any other program that got its permissions messed up is not fixed.
which would be most of them...

---

### Post by Leppie on 2010-02-06
> **ratcheer said:**
> I don't see anything in the dmesg output that rings any bells. I will watch carefully, the next time I reboot. It goes away pretty fast, though.
did you install/remove a lot of apps after the initial installation? if not, you could easily do a re-install and leave your home partition as is. instead of going through the pain of resetting all permissions in /usr and subfolders and checking the filesystem error.

---

### Post by ratcheer on 2010-02-06
> **Leppie said:**
> did you install/remove a lot of apps after the initial installation? if not, you could easily do a re-install and leave your home partition as is. instead of going through the pain of resetting all permissions in /usr and subfolders and checking the filesystem error.

Oh, yes. Tons of stuff. I guess I'll just see how things go.

Thanks,
Tim

---

### Post by warfacegod on 2010-02-06
This is probably a stupid question but did you update GRUB2?

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> This is probably a stupid question but did you update GRUB2?
should be the same, but doesn't hurt to update it. run update-grub:
```
sudo update-grub
```

are apt and dpkg still working?

---

### Post by ratcheer on 2010-02-06
Ok, I ran update-grub.

aptitude is working, so I think that means dpkg is working.

Tim

---

### Post by Leppie on 2010-02-06
> **ratcheer said:**
> Ok, I ran update-grub.

aptitude is working, so I think that means dpkg is working.
well, just generate a list of all the installed packages then. just in case:
```
dpkg --get-selections | gawk '{ print $1 }' > ~/InstalledPackages.txt
```
this will help restore your system should you encouter bigger issues later on ;)

---

### Post by ratcheer on 2010-02-06
That worked just fine. I have 1769 installed packages. :)

Tim

---

### Post by Leppie on 2010-02-06
> **ratcheer said:**
> That worked just fine. I have 1769 installed packages. :)

Tim
perfect, should your system become unusable you can easily restore it later on (it will just take a long time, but at least you can leave it unattended).

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> perfect, should your system become unusable you can easily restore it later on (it will just take a long time, but at least you can leave it unattended).

And you didn't feel the need to mention this to me? Around the time I started my "Stupid" thread?=;:tongue:

---

### Post by Leppie on 2010-02-06
> **warfacegod said:**
> And you didn't feel the need to mention this to me? Around the time I started my "Stupid" thread?=;:tongue:
cos it's true... i am stupid... :D

---

### Post by warfacegod on 2010-02-06
> **Leppie said:**
> cos it's true... i am stupid... :D

Your a Linux Redneck not stupid.

---

### Post by ratcheer on 2010-02-06
I thought I was the Linux redneck. 

Tim

---

### Post by warfacegod on 2010-02-06
> **ratcheer said:**
> I thought I was the Linux redneck. 

Tim

That has yet to be determined. There is a Redneck quiz in post #162. If you have done or would consider doing anything there, you are a Linux Redneck.

[http://ubuntuforums.org/showthread.php?t=1379471&page=17]("http://ubuntuforums.org/showthread.php?t=1379471&page=17")

---

### Post by warfacegod on 2010-02-06
Actually, scratch that. If you have done or would consider doing anything in the *entire thread,* you are a Linux Redneck.

---

### Post by willowave on 2010-02-07
> **warfacegod said:**
> This one maybe?
 
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)
Yeah thats the one. When I made it , he only had 9 on there. Looks like he's added more.

---

### Post by Leppie on 2010-02-07
> **ratcheer said:**
> I thought I was the Linux redneck. 

Tim
you have yet to fight me for the title :P

---

### Post by warfacegod on 2010-02-07
> **willowave said:**
> Yeah thats the one. When I made it , he only had 9 on there. Looks like he's added more.

See Leppie? I was right.:tongue:

---

### Post by ratcheer on 2010-02-07
Ok, the practical need of this thread has been satisfied, but the original question remains open. Why can't the Gparted and Clonezilla Live CD's see anything on my hard drive but unallocated space?

Tim

---

### Post by warfacegod on 2010-02-07
> **ratcheer said:**
> Ok, the practical need of this thread has been satisfied, but the original question remains open. Why can't the Gparted and Clonezilla Live CD's see anything on my hard drive but unallocated space?

Tim

I thought the original question was whether or not you are a Linux Redneck.

Have you tested the discs? Checked for "locking" features?

---

### Post by Leppie on 2010-02-07
> **ratcheer said:**
> Ok, the practical need of this thread has been satisfied, but the original question remains open. Why can't the Gparted and Clonezilla Live CD's see anything on my hard drive but unallocated space?

Tim
as i stated, i've never used the gparted discs before. however, it could be that they don't support all the formats and i don't know if you can update the image while running it. ubuntu livecd's can be updated as long as there's an internet connection.

---

### Post by warfacegod on 2010-02-07
> **Leppie said:**
> as i stated, i've never used the gparted discs before. however, it could be that they don't support all the formats and i don't know if you can update the image while running it. ubuntu livecd's can be updated as long as there's an internet connection.

Could be the same with Clonezilla.

---

### Post by Leppie on 2010-02-07
> **warfacegod said:**
> Could be the same with Clonezilla.
yeah, most of the *zilla range is quite nice and very flexible

---

### Post by SecretCode on 2010-02-07
> **ratcheer said:**
> Ok, the practical need of this thread has been satisfied, but the original question remains open. Why can't the Gparted and Clonezilla Live CD's see anything on my hard drive but unallocated space?

Tim

I'd take that question to the gparted forums [http://gparted-forum.surf4.info/index.php](http://gparted-forum.surf4.info/index.php) - at least one of the developers, Curtis Gedak, hangs out there. Or [http://www.clonezilla.org/forum/](http://www.clonezilla.org/forum/)

---

### Post by ratcheer on 2010-02-07
Maybe I don't understand this at the most basic level. My thinking is that the reason for both the Gparted and Clonezilla CD's is so you can run another OS to manipulate or back up the not-mounted partitions of your machine's OS. I may be wrong, but this is what makes sense, to me.

Tim

---

### Post by Leppie on 2010-02-07
> **ratcheer said:**
> Maybe I don't understand this at the most basic level. My thinking is that the reason for both the Gparted and Clonezilla CD's is so you can run another OS to manipulate or back up the not-mounted partitions of your machine's OS. I may be wrong, but this is what makes sense, to me.
i would expect the same behaviour... good thing i've never tried those images... i actually prefer images with a bit more tools on them, like Ultimate Boot CD or Hiren's Boot CD, or even the ubuntu livecd for that matter. usually if you need to resort to images like that, just being able to mount/format a drive doesn't really occur that useful to me. very often other things are wrong as well, so having a couple of other tools would help a lot.

---

### Post by ratcheer on 2010-02-07
This is from the gparted documentation: 
**Tip**

           If           Partition &#8594; Unmount           does not succeed, then the partition is probably in use.           
           To have all partitions unmounted and available for           partition editing actions, boot from a Live CD and            use gparted.           See [the section called “Acquiring  GParted on Live CD”]("http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-acquire-livecd")
[U]
[/U]
__

---

### Post by Leppie on 2010-02-07
i still don't understand what would be the advantage of using a gparted disc over an ubuntu livecd...

---

### Post by warfacegod on 2010-02-07
> **Leppie said:**
> i still don't understand what would be the advantage of using a gparted disc over an ubuntu livecd...

I can't think of one aside from boot time.

---

### Post by ratcheer on 2010-02-07
> **Leppie said:**
> i still don't understand what would be the advantage of using a gparted disc over an ubuntu livecd...

First, I guess it just disturbs me that it is not working. Second, so many people on this forum highly recommend Clonezilla, and it is apparently having the same problem.

I am more comfortable when things work as expected. These kinds of oddities undermine my confidence in my system. I have worked professionally with HP-UX and Solaris for the past 14 years. I know the software for those OS's is not free, but it almost always works, and that is what I am used to.

Tim

---

### Post by audiomick on 2010-02-07
> **ratcheer said:**
> First, I guess it just disturbs me that it is not working. Second, so many people on this forum highly recommend Clonezilla, and it is apparently having the same problem.

That would irritate me too.
As I understand it, those sort of tools are supposed to work no matter what. Clonezilla from a live CD so that you can do images without the drive being accessed for anything else, and gparted so that you can do partition operations when your system is completely shot down. 
It seems to me that there is something odd going on with your system, and if it was mine I would want to get to the bottom of it.

---

### Post by Leppie on 2010-02-07
well, another possibility could be that those disks cannot access your drive because it used to be in a raid. but of course, if these images should be able to access drives "no matter what" they will have to have raid support as well...

---

### Post by warfacegod on 2010-02-07
> 
I am more comfortable when things work as expected.

That goes without saying. Most everybody is like that. Except me. Gives stuff to do.

---

