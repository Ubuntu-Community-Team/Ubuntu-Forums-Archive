---
title: "Partition Magic Error - Urgent Help Needed!"
date: 2006-04-29
forum: General Help
---

### Post by marcog on 2006-04-29
Hi guys. I've got myself into some nasty problems here and I need your help.

I was resizing my swap partition using Partition Magic 8.0. It was about 75% complete when it hit an error. I remember it saying something about a "%lo error". Since it was doing nothing and said "Reboot, press any key to continue" I pressed a key and it did a reboot.

A little backround is required to explain what hapenned next. I have Windows XP (/dev/hda1), Ubuntu Dapper (/dev/hda3) and Gentoo (/dev/hda4). My Gentoo install is very minimal, use it only to fiddle around with new stuff (no x installed). Ubuntu is my main install. And Windows is there just for things that I can't use in Ubuntu.

As Ubuntu is my mainly used os I have Grub stored in my Ubuntu partition. Now when I tried rebooting, Grub tried loading, but then I got an "Error 17" message (which I see is a partition error) and then nothing further happens. Then I tried booting into the Gentoo Live CD - and that's where I am now.

I then tried mounting my partitions. Windows and Gentoo partitions mount with no problems and everything is still there, and my swap partition (/dev/hda5) is ok too. Ubuntu partition is the one that is not mounting. The error message I get is:

> #SQUASHFS error: Can't find a SQUASHFS superblock on hda2

I then tried running fsck on the partition and then got the following error:

> Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/hda2

and some other stuff about the superblock being corrupt. The thing is that the partition is an ext3 fs, so  tried running fsck.ext3, but then I got the exact same error message.


Any ideas on what I could do to sort this out? Partition Magic was just moving the data on my Ubuntu partition when the error occured, so my guess is that there must be some recovery software that can recover my data.

Is there a way to boot into my Windows partition at least, since that is not corrupt? I wouldn't know how to bypass the loading of Grub to do so.

Please help me in this desperate situation! Thanks!

---

### Post by tazzik on 2006-04-29
I don't know how to fix the superblock error thing, but when I had a grub problem i booted into ubuntu livecd in recovery mode and typed something like install grub hd0,1 (something like that) 
hope that helps
tazzik

---

### Post by Herman on 2006-04-29
[GAG Boot Manager]("http://users.bigpond.net.au/hermanzone/p12.htm") is a great help for those occasions when GRUB isn't available.
It is operating system independant so if one operating system goes you can still boot the others. Especially Windows.
GAG actually saved my bacon earlier this evening, I was putting a nice Kubuntu grubsplash in my wife's computer and i made a mistake and lost the GRUB menu for a while. Kubuntu was unbootable, it would only boot Windows. I fixed it before she came home by installing Lilo in her Kubuntu partition and booting it with GAG and then fixing the menu.lst  Now it's fine.  (Installing Lilo in the Ubuntu partition (boot directory) doesn't erase grub, we can have both grub and Lilo together).
If tazzick's method works for you it will be the easiest.
You shouldn't use Partititon Magic for Linux, it isn't perfectly compatible. Try [GParted livecd]("http://gparted.sourceforge.net/livecd.php") instead, it's free and will do a better job, and easier too.
Anyway, good luck with it, Regards, Herman :D

---

### Post by marcog on 2006-04-29
I installed grub onto my Gentoo partition. Didn't realise it would be that easy (was a little more complicated than you mention though).

So anyway, I can boot into Windows and Gentoo now. Need to see what I can do to recover my Ubuntu partition now. I have a feeling that's going to be a rather panfull process if possible at all.

However, at least I can *use* my pc now, albeit in Windows (arggg). So it's not *as* urgent now, but I'd still like to see what can be done.

Die Partition Magic, die...DIE...

---

### Post by marcog on 2006-04-29
Sorted that out now. But thanks for the tips anyway.

[QUOTE=Herman]You shouldn't use Partititon Magic for Linux, it isn't perfectly compatible. Try [GParted livecd]("http://gparted.sourceforge.net/livecd.php") instead, it's free and will do a better job, and easier too.
Anyway, good luck with it, Regards, Herman :D[/QUOTE]

Will definately have a look at using that next time. Thanks!


Any ideas on recovery software? I can boot into Windows and Gentoo, so software for either.

Thanks again for your help. Much appreciated!

---

### Post by Herman on 2006-04-29
Well I think there might be a chance you can use GnuParted from the command line and try the '[rescue']("http://www.gnu.org/software/parted/manual/html_mono/parted.html#SEC24") command, that might work.
You can get a 'Parted' command line from 'aterm' on the GParted livecd by typing the following command ```
#parted
``` Then you type 'p' for print and it will show you the numerical details of your beginnings and endings of your partitions.
'h' is for help, that will give you a list of commands you can use, but you should be able to read about those better in the manual I linked you to a few lines above here. The command I'm hoping might help your is 'rescue'. You need to have an idea of the numerical start and end of your partition to put after  the command.
A 'parted command line is also available in a Ubuntu install CD, by typing 'rescue' instead of pressing 'enter' to install.  Or a Ubuntu LiveCD, (or Knoppix) by opening a terminal and typing 'sudo parted /dev/hda'. (Without the inverted commas).
I hope this helps you. (Herman)

Edit: Try and see if you can get 'Parted from a gentoo terminal, I don't know much about gentoo, but it might have 'parted in it, it might be the easiest for you. make sure the partition is not mounted too, before you do anything. That's why a GParted liveCD is good. It has a special way of handling that, so you don't have to worry.

---

### Post by marcog on 2006-04-29
I've got a Breezy Install CD as well as a Breezy Live CD. So I could follow either of those options right now. I don't however have the GParted Live CD though. I could however download it.

Is there any difference between the three options? Would it be better to download the GParted Live CD? I will do so if it would improve the chances of recovery.

One more question - is there a significant chance that this would damage my working partitions without repairing my Ubuntu partition? (My Windows/Gentoo partitions are working, although my Ubuntu partition is far more important to me.)

---

### Post by Herman on 2006-04-29
> Is there any difference between the three options? Would it be better to download the GParted Live CD? I will do so if it would improve the chances of recovery. As far as I know 'Parted will work the same, but when you have the GParted livecd, which gets updated every two weeks or so, as opposed to every six months or maybe more, you have the latest cutting edge technology if any of the software connected to 'Parted has been improved recently, and a lot has. I can't say specifically though because I'm just a user like you , not a software engineer or developer.
> One more question - is there a significant chance that this would damage my working partitions without repairing my Ubuntu partition? (My Windows/Gentoo partitions are working, although my Ubuntu partition is far more important to me.)I don't think it will be as risky as using Partition Magic was in the first place, however you should back up any valuable data just to be sure anyway. It's hard to get experience with this sort of thing, it's not something most people do every day, so it's hard to say for sure, but I think either it will work and fix your problem or at least not do any harm. If you want to wait, there are experts around these forums who can advise you better than me, but you might be lucky and get one right away, or wait for a week or more. Then they might just say the same thing I said. I guess as long as your data is backed up nothing really matters. If worse comes to worst It might cost you some time, that's all, but I hope it works for you. :-D Herman.

---

### Post by marcog on 2006-04-29
From what you are saying I think I'm going to go ahead and download the GParted LiveCD. I'll try that out and post my results here.

Thanks a lot. I hope I haven't been asking too many questions! :-)

---

### Post by marcog on 2006-04-29
Finished downloading the GParted LiveCD. Followed your instructions, but I get a segmentation fault, which doesn't sound good.

It picks up all my partitions, as well as my Ubuntu partition (although it cannot detect the file system). It also picks up a ~770MB unallocated section after and tiny section before the Ubuntu partition (I presume this is from when PM was moving the Ubuntu partition).

It picks up the Ubuntu partition as being the exact size it was before, which looks promising.

Any ideas on the segmentation fault? I'm going to go home and then I'll try out the Ubuntu Install/Live CD.

---

### Post by Herman on 2006-04-29
Okay, there's a special area in the first sectors of any partition which is a little bit like an index in a book and it controls how the computer sees and reads your partition. Linux partitions don't like being 'moved'. They can be copied and pasted though. Maybe that has been damaged or destroyed if Partition Magic has tried to 'move' the partitiion.
When you have the GParted CD booted it normally gives you a nice Graphic user interface ( 'GUI', ). After you are finished looking at that, you close it (click 'GParted', then 'Quit'and you should get a plain blue desktop. Well it could be greenish, I'm not very good with colors, doesn't matter, right-click on that desktop and click 'aterm'. A black windows will appear with 'root@Parted:~# in the top left corner.
That's where you type the word parted after the # prompt eg:  #parted
That gives you a parted shell, the new prompt looks like: (parted)
After the (parted) prompt you can type help or h for help and press enter. It will give you a list of commands you can use.
It's best to read more about those from the [manual here]("http://www.gnu.org/software/parted/manual/html_mono/parted.html").
The first command you might use is 'p' or print, to give you information on the beginning numbers and ending numbers of each partition. In this case it appears to be in GB, normally it's given in megabytes.
Then you will need to type the command; rescue, followed by the beginning and ending numbers for the partition.
The example given in the manual shows how the rescue command works after the partition has been removed with the rm command, and then shows the rescue command restoring it. That's what you need to do, something like that.
You need GParted to make you an new 'index' sector at the beginning of your partition that partition magic has destroyed. I hope that will work for you, it should. Try that, and good luck!  Regards, Herman

---

### Post by marcog on 2006-04-29
I ran parted off the Ubuntu Live CD. It did the search, but couldn't correct anything. I've also ran several other tools without any luck.

I've started a [new thread]("http://ubuntuforums.org/showthread.php?p=969124#post969124") with a more appropriate title for my current situation. Hope that doing so is ok.

---

### Post by marcog on 2006-04-29
[QUOTE=Herman]Okay, there's a special area in the first sectors of any partition which is a little bit like an index in a book and it controls how the computer sees and reads your partition. Linux partitions don't like being 'moved'. They can be copied and pasted though. Maybe that has been damaged or destroyed if Partition Magic has tried to 'move' the partitiion.[/quote]

Yes I know about the index table and I realise that's what my problem must be.

> When you have the GParted CD booted it normally gives you a nice Graphic user interface ( 'GUI', ). After you are finished looking at that, you close it (click 'GParted', then 'Quit'and you should get a plain blue desktop. ...

Not to try sound arrogant or anything, but I'm a little more  advanced than that! :-) But now that you mention all that I think what it might have been is that I didn't close gparted and it was holding a lock maybe. I got it to work on the Ubuntu liveCD though so it doesn't really matter that any more.

> You need GParted to make you an new 'index' sector at the beginning of your partition that partition magic has destroyed. I hope that will work for you, it should. Try that, and good luck!  Regards, Herman

Unfortunately it didn't work as mentioned in my previous post! ](*,)

---

### Post by Herman on 2006-04-29
Oh, :opps: I tried it too and I also got a segmenttation fault. I wonder if that's a bug or if we're doing something wrong. I'll file a bug report anyway and see what the GParted people say.  Well, yes, try Gnu Parted from a normal Live or Install CD then. Sorry about that. Regards, Herman

Edit, okay, sorry, I can read you post immediately before this now that I've submitted mine. I didn't mean to insult you by being overly verbose, lots of times it could be someone very new to all this who's getting help. 
Anyhow if that won't work then I don't know what to suggest. I hope someone will come along who has a better plan. Sorry that  didn't work for you. Regards, Herman

---

### Post by marcog on 2006-04-29
[QUOTE=Herman]Oh, :opps: I tried it too and I also got a segmenttation fault. I wonder if that's a bug or if we're doing something wrong. I'll file a bug report anyway and see what the GParted people say.  Well, yes, try Gnu Parted from a normal Live or Install CD then. Sorry about that. Regards, Herman[/QUOTE]

Already done that (Ubuntu Live CD). No segmentation fault, but it doesn't recover the partition.

---

### Post by duderonomy on 2006-07-08
[QUOTE=marcog]```
#SQUASHFS error: Can't find a SQUASHFS superblock on hda2
```
[/QUOTE]

Hello,

I am seeing a similar issue. I would like to determine the root cause... and I am 
hoping that someone on this thread can help me.

I was not having any specific trouble other than migrating my Gentoo image and a newly 
installed Ubuntu image to a single drive. At top level, I started with a drive 
configuration like this:

 hda: Gentoo
 hdb: Ubuntu
 hdc: new drive

After successfully copying all Gentoo-related files from the boot (ext2) and root 
(reiserfs) from hda to hdc, I re-installed grub on the new drive then rebooted into a 
new drive configuration running Gentoo. I tested and it was working great. I built new 
kernel, ran desktop GNOME, and proved to myself that 2.6.16-gentoo-r12 was operating 
OK. 

Now the drive configuration looks like this:

 hda: Gentoo (on NEW DRIVE)
 hdb: Ubuntu

Then I proceeded to copy the single / partition on which Unbunta was installed, hdb3, 
to the new disk, at partition hda4. When I attempt to mount the partition I plan to 
copy, I see this error on STDOUT and I also see the following in my logs:```
# mount 
/dev/hdb3 /mounts/hdb3
mount: you must specify the filesystem type

# mount -t ext3 /dev/hdb3 /mounts/hdb3
mount: wrong fs type, bad option, bad superblock on /dev/hdb3,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
kernel logs:```
Jul  8 07:39:59 [kernel] kjournald starting.  Commit interval 5 seconds
Jul  8 07:39:59 [kernel] EXT3-fs: mounted filesystem with ordered data mode.
Jul  8 07:40:26 [kernel] SQUASHFS error: Can't find a SQUASHFS superblock on hdb3
```

This partition was created by the Ubuntu 6.06 Server installer and seems to work OK 
when I was booted into Ubuntu. I checked my Gentoo kernel and it indicates that ext3 is 
built-in to my kernel, but I am no kernel expert... perhaps there is a missing option 
somewhere.

Why does the file system on this Ubuntu partition appear to operate OK with Ubuntu 
kernel but not the Gentoo kernel? Admittedly I configured the Gentoo kernel but I was 
hoping someone could suggest some things to examine... :) 

Thanks in advance!
-D

---

