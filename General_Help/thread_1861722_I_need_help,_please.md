---
title: "I need help, please"
date: 2011-10-15
forum: General Help
---

### Post by modestmachine on 2011-10-15
Here's the story, and as a warning this goes on for a bit, I don't like to leave anything out:

I quoted it so you can skip it if you really want and get to the point.

> I have always used windows on my computers, but a few months ago I decided to try out Ubuntu and I installed it so I can dual boot Windows and also have my new Ubuntu 11.04 partition. I only used Windows for games and everything else was catered for by Ubuntu. Things were great.

A couple of days ago when Ubuntu 11.10 was available, I was asked if I would like to upgrade through the update manager. Not knowing any better, I accepted. A couple of failed installs later (server was overloaded and cut out in the middle twice, I switched server and then the upgrade worked), Ubuntu 11.10 finally installed.

With absolutely massive problems. It was unusable, clicking the rubbish bin (amongst other things) would open the movie player for some reason, everything was unbearably slow, the new menus and interface were frankly crap and restrictive so I set out to find out what was going on and if I could revert back to 11.04.

I came onto these forums looking for an answer and was told that I shouldn't have upgraded, especially this early as there would no doubt be problems with the latest package. While I appreciate the warning for next time, I am still annoyed that I was given no warning, surely Canonical or whatever should say this release is unstable or something, because these forums have been lit up over people complaining about this release. (If someone says this happens with every release that is not good justification, it only proves my point)

I was told to start over, wipe the disc and do a normal install from USB or CD. I started to look into how to uninstall Ubuntu from the Windows side, and I was warned that I couldn't just willy nilly delete the entire partition because the bootloader/GRUB (I'm sorry, I'm not 100% what to call this, it's the ubuntu multiboot screen) is now the default and if I go ahead and delete that I couldn't even access windows anymore.

This is the guide I decided to follow :
[http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/](http://www.makeuseof.com/tag/nongeeks-guide-safely-uninstall-ubuntu-dualbooting-machine/)
It seemed to be perfectly relevant to my situation, so I downloaded the EasyBCD and followed the guide's instructions. I was pretty sure I did everything right, so when it asked me to restart as a check, I double checked my steps and then went ahead with it.

Well something went wrong because Windows won't start anymore. It has a serious error, and the only option is to restart the computer.
Thankfully I could at least get into the boot menu after restarting so I could boot the grub off the partition (which would still be there, as per the guide) 

So right now in my story I have the following:

1. A windows partition that doesn't work, but I have plenty of important stuff on it (60 GB)
2. An Ubuntu partition that barely works, and is ready to be eviscerated ( 15 GB)
3. Ubuntu 11.10 ready to be installed off a USB stick 

At this point, I figure that I should install 11.10 and overwrite my existing Ubuntu partition.

Seems like the best course of action, right?
Well, I get into the installer part and it's giving me 3 options; to create a new partition alongside everything I have, wipe the entire hard drive, or edit the partitions.

I go to edit the partitions thinking there would be a straightforward management menu or something, but no it was all stuff I'd never seen before, nor could I make sense of it. And to think all I wanted to do was delete/overwrite one partition and it didn't let me do that.

So after trying to figure it out, I made a new partition alongside the rest (I don't have much room left; I only have an 80GB hard drive on this laptop, and no this isn't 2007) with the intention of editing the partitions later.
That all went fine, stable install which is better than the upgraded one I had for but not by much, I still don't like it at all.At the minute I have about 100 MB of free space so I can't download Chrome or Skype, the two things I use more than anything.

I went into disk utility, and have so far managed to delete the other Ubuntu partition, freeing up 15GB of space, but now I don't know how to expand this partition into the free space (or will that do it automatically?)

Could someone help me out on that? As in, how do I adjust partitions? I would like to adjust the windows side too.

Alternatively, I want to "downgrade", or reinstall Ubuntu 11.04, this link will work? 

[http://releases.ubuntu.com/natty/](http://releases.ubuntu.com/natty/)

I have backed up almost everything important on the entire computer, but there is still some windows things I need to cover because I wasn't planning on having to wipe that.

I'm starting (ha) to ramble, so I'm going to finish this and answer queries/responses and edit this with any more necessary information.

It's 4:29am, I'm tired. I'm annoyed at how this entire escapade has turned out, thanks to Ubuntu being crap at upgrading.

Thank you if you read all this.


_**[COLOR=black]TL;DR :[/COLOR]**_[B]Ubuntu 11.10, some tech website, windows vista and myself have collectively dug me a hole so deep I can hear the Rugby World Cup and I need a big ladder
P.S: "dig up, stupid" is not real advice
[/B]

---

### Post by gsmanners on 2011-10-16
Okay, I think this may be what you were looking for:

[http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C](http://gparted.sourceforge.net/display-doc.php?name=help-manual&lang=C)

---

### Post by wojox on 2011-10-16
Download [bootinfoscript]("http://sourceforge.net/projects/bootinfoscript/") and run it from a live cd or usb. Post back in code tags.

---

### Post by SBJ95 on 2011-10-16
Well, first off, if you want 11.04, you'll need to download and create an 11.04 stick/disc.  The link you gave is indeed what you want.  What you'll probably need to do first though, in order to have room to download 11.04, is burn/create a disc/stick of [Parted Magic]("http://partedmagic.com/doku.php?id=start"), preferably from a different computer, if that's an option.  I may be mistaken, but there's no way I know of to resize a partition you're using.  It may be doable from the USB stick you have, but I'm not familiar with the partition managing tools on the Ubuntu LiveCD.

Anyways, if you can use Parted Magic or GParted (per the above poster) to resize your Ubuntu partition, then you can download Natty and create a stick/disc of it.  Then install it like normal.  You'll probably need to handle the partitions manually; delete all partitions that aren't NTFS and are ext2/3/4 and swap, and recreate them; also choose the NTFS (Windows) partition and pick a mountpoint for it (e.g. /mnt/windows).  Then continue the install as normal, and voila, your system should be in a completely usable state.

I hope this makes at least a little sense and is at least slightly helpful.

---

