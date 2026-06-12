---
title: "Deleting a mount point in /media"
date: 2010-10-09
forum: General Help
---

### Post by ZhuaSD on 2010-10-09
Hi All:

I have a bad mount point, I had some mounting problems before, and made this wrong entry, when I mount the volume it works but then the system tells me the hard drive is empty, which is wrong and some kind of error.

My problem here is pretty simple, this point is in /media, but it disappears when the volume is unmounted.  I want to delete it and re-mount using the storage device manager, which hopefully will solve the problem.

So how can I delete this entry when it disappears?  I don't really want to delete it while the volume is attached and mounted.

Anyone got a good idea?

---

### Post by Chethan S on 2010-10-09
Mounting of drives can be taken care of in /etc/fstab file. You can check it using the command 
> gksudo gedit /etc/fstabThen edit the file as you require. You can even delete the entries or make entries such that the drives remain mounted. Care is to be taken when you key in the device(filesystem) details and also the type.

Some of the entries I have in my fstab file are:
> /dev/sda3        /media/DOWNLOADS    ntfs        defaults        0        0
/dev/sda4        /media/MOVIES    ext4        defaults        0        0If you want to know the device name you can actually use the system monitor(System>Administration>System Monitor) which provides the exact details.

---

### Post by yetiman64 on 2010-10-09
> **Chethan S said:**
> ....> sudo gedit /etc/fstab                      ....Please note this command should be used with "gksudo" as gedit is a graphical application. Link #4 in my sig, "RootSudo", has a section titled "Graphical Sudo" down the page a bit, which explains the reasoning for using gksudo and NOT sudo in this instance.

---

### Post by Chethan S on 2010-10-10
I agree with what you say but I would like to inform you that the command > sudo gedit /etc/fstab also works the same way when provided in terminal. Give a try.

---

### Post by yetiman64 on 2010-10-10
> **Chethan S said:**
> I agree with what you say but I would like to inform you that the command  also works the same way when provided in terminal. Give a try.

Yes it "works" but can leave a users home folders or files (such as .ICEauthority -- google it and problems regarding it) with ownership/permission problems under certain circumstances, which in turn can stop an installation from booting successfully. 

If you are going to give advice please understand its full possible outcomes, and with regard to graphical applications please try and use either **gksudo or gksu** as the RootSudo link indicates (also please note that the RootSudo link is "Community Documentation" and is as such is regarded as the "correct" advice with regards to using sudo and graphical applications). 

Although your advice may not necessarily  cause problems in this case, would it not be better to get in the good habit of giving the correct information that will work without problems in all cases? yetiman64

---

### Post by Chethan S on 2010-10-10
Thank you for guiding me in the right direction. It is my lack of knowledge to be blamed. I just thought, since it works for me it would work for everyone. 

Anyway I will be more careful now onwards.

---

### Post by yetiman64 on 2010-10-10
> **Chethan S said:**
> Thank you for guiding me in the right direction. It is my lack of knowledge to be blamed. I just thought, since it works for me it would work for everyone. 

Anyway I will be more careful now onwards.
OK :). I would suggest for the sake of the OP and others reading this, you edit post #2 to read "gksudo". Don't worry too much about subsequent replies etc. Cheers and see you in the forums, yetiman64.

---

### Post by ZhuaSD on 2010-10-10
Hi guys:

Thanks for the help, I do appreciate it, but unfortunately I don't think I got a useful answer.  :P

(By the way the whole command issue is not a problem for me so no harm done).

I might be able to put the entry in fstab, but I did try that before and the drive wont go online or whatever quickly enough, when I start up the install tells me that the drive is not available or not responding or something like that.

So, maybe I can do it right in fstab, but what I am trying to do now is to remove this old entry in /media that keeps disappearing when the drive is unmounted.

I dunno, maybe if I do the fstab right (I didn't figure that out yet) then this bad mount in /media might not matter.

But seeing as the fstab is going to cause a whole new problem, I want to avoid that.  I want to use the storage device manager to do the mounting for me, which is going to be in /media (but I want a fresh one, as the old one is not working, as I said it tells me there is no data on the drive and I know that's not true, and I just checked the drive, its not a bad drive, this is a mounting problem I am 99% sure).

fstab, by the way, is usually not for usb devices.  This drive is a normal drive in a usb enclosure. 

So, can anyone tell me how to clear out this old mount point once and for all?  I would be much appreciative!

Or, feel free to tell me I got it all wrong and should be approaching this problem from another way.  I am open to suggestions!

:lolflag:

Thanks!

---

### Post by yetiman64 on 2010-10-10
> This drive is a normal drive in a usb enclosure. OK with the drive mounted you could trying viewing mtab (maybe post it here) with,
```
cat /etc/mtab
```If you know the volume label or mount folder of the volume then you can add to the above command,
```
 | grep <label or mount name>
``` Note: copy and paste all, including the space before the pipe symbol (|) and alter<label or mount name> to its actual name.

Knowing how it is being mounted may be of help in blocking it and resetting up with storage manager.

> fstab, by the way, is usually not for usb devices.spot on, look at mtab. 
If you sort out any mount problems and use volume labels on the USB drive then mtab should automatically mount it to /media/<volume-label> when the external drive is plugged in, you will then have automatic access to any linux contents through nautilus.

Actually using storage manager here seems a bit unnecessary, if the external drive is NTFS then adding ntfs-config and setting it up to support writing to external devices is easy as well.

---

### Post by coffeecat on 2010-10-10
> **ZhuaSD said:**
> So, can anyone tell me how to clear out this old mount point once and for all?  I would be much appreciative!

Or, feel free to tell me I got it all wrong and should be approaching this problem from another way.  I am open to suggestions!


You haven't got it all wrong, but I think you're looking in the wrong place.

> **ZhuaSD said:**
> I have a bad mount point, I had some mounting problems before, and made this wrong entry, when I mount the volume it works but then the system tells me the hard drive is empty, which is wrong and some kind of error.

My problem here is pretty simple, this point is in /media, but it disappears when the volume is unmounted.  I want to delete it and re-mount using the storage device manager, which hopefully will solve the problem.

So how can I delete this entry when it disappears?

You can't because it's already been deleted. A mountpoint is just an empty directory. Even if it was "bad" in some way, a mountpoint created for an automounted drive is autodeleted when the drive is unmounted. There is nothing more you can do.

So - where's the problem? The only other place it can be: in the filesystem. That is, the filesystem in the partition that is being mounted.  Whether you use /etc/fstab or have the drive automounted the problem will persist. 

What filesystem is the drive/partition? NTFS? Ext3? Something else? What is the *exact* error message you get?

**Edit:** by the way/ What was the "wrong entry" that you made.

---

### Post by ZhuaSD on 2010-10-10
Thanks coffeecat and yetiman64, I have to go to work now but will follow your instructions when I get back.

Coffeecat, its true that I have had problems with this drive before, but its not the drive but some bug in ubuntu.  When I do a fresh install the drive will be fine, but then there will be problems later.

The bug is this one:
[https://bugs.launchpad.net/ubuntu/+bug/622494](https://bugs.launchpad.net/ubuntu/+bug/622494)

The drive checks out, and the problem has been happening for at least a couple years, I think I had 9.04 installed for a long time.  Back when I still had windows installed I checked it many, many times.  The drive is ok.  I just checked it in gparted a couple weeks ago.  But this time I didn't mount it right the first time after a new install to 10.04, so instead of having the annoying pauses when listening to music, I don't have any access at all to the drive...

Ultimately I think the problem is caused because I have to many different drives.  3 internal plus the file system, and also at least 5-7 external devices.  However, in general only this drive has problems.

Anyway, got to run, will reply again later when I get back.  Trying to avoid yet another re-install...

---

### Post by coffeecat on 2010-10-11
> **ZhuaSD said:**
> The bug is this one:

It's easy to blame a "bug", but let me tell you a cautionary tale. Two, in fact. When you are connecting a USB drive to a system there are four variables to consider:

1 The operating system and its drivers.
2 The BIOS of the host machine.
3 The firmware of the enclosure
4 The firmware of the actual HD.

These can interact in unpredictable ways. The two tales:

I have a USB SATA docking station. Really useful. It had worked well with every OS I use with every SATA drive I had tried it with, until one day when Ubuntu refused to recognise it. Strange, I thought, it was working well with Ubuntu the day before. Long story short: Ubuntu couldn't recognise the drive in my Sony Vaio. It was fine with every other machine I tried. The Sony BIOS was the variable in this case.

Tale two is stranger.

Using Carbon Copy Cloner in my Mac Mini, a particular USB enclosure with a Western Digital ide drive would unmount itself after half an hour or so. A bit tedious when you are trying to do a complete system backup which is what CCC is for. But when I put a Hitachi drive in the enclosure it behaved itself. Do I blame WD? No. Some odd interaction between the various firmwares must have been the cause.

So - the moral. :) I would suggest you take the pragmatic course and simply not use the problematic drive in Ubuntu. You have 5-7 others to choose from! :p It might be a bug in Ubuntu; it might not. Certainly having it work OK in a fresh install but not later is odd. But either way, you could waste a lot a time trying to get the drive to work with Ubuntu.

---

### Post by ZhuaSD on 2010-10-12
Thanks for your unfiltered opinions.  I have thought about it, and you are probably right that it is a conflict like that.  Its a WD IDE 250 gig HD, and I seem to see lots of problems like this with WD drives.

Thinking back, it has been since the day this drive and this comp (a cheap HP) got together, there have been problems with Ubuntu's mounting of the drive.  Only the U version has changed.

I didn't know that the enclosure had anything to do with it, and so I might try to buy a better enclosure because the one I have is super cheap.  And those docks that you just slide the hd into are so cool and don't cost all that much.

Still, your solution is not very attractive. For me its ok but if someone goes out and buys a 1.5 T drive to use as backup, and then it doesn't work, well your solution is not acceptable in that case, right?  The drive works, the comp works, and so they should be able to work together.  Hopefully that bug gets fixed at last!

But I still want to know where the data goes for the mount.

If I get off my *** I will re-install yet again and maybe get it right this time.  Don't mind re-installing, its pretty easy with partitions and the live disk, and if I do it again, I will just have one big partition outside the filesystem on the internal hd. But maybe I will just leave it until the comp changes or until I get a new, bigger drive.

Finally, I think you can't say that it might or might not be a bug in Ubuntu.  Because Ubuntu's job is to coordinate the various resources it works with.  This is just a tricky problem that hasn't been worked out yet.  But if all WD drives didn't work because of the same conflict (say, for the sake of argument) with Sony comps, and lots of towers are sold with that setup, well that would be called a bug in Ubuntu.

Heh, no offense.  Just saying :popcorn:

Anyway, thanks again, I wasn't all that happy with your post at first, but when I thought about it you made a bunch of useful points even if I don't completely agree with your conclusion.  Appreciate it.

:guitar:

---

### Post by coffeecat on 2010-10-12
> **ZhuaSD said:**
> Thanks for your unfiltered opinions.

....

I wasn't all that happy with your post at first

Unfiltered? :( I'm sorry you  interpreted my post as anything but helpful and friendly, particularly when I went to the trouble of adding a couple of smileys. Hard work that - adding smileys. :wink:

> **ZhuaSD said:**
> Still, your solution is not very attractive. For me its ok but if  someone goes out and buys a 1.5 T drive to use as backup, and then it  doesn't work, well your solution is not acceptable in that case, right?   The drive works, the comp works, and so they should be able to work  together.  Hopefully that bug gets fixed at last!

Agreed about the person who buys the expensive drive only to find it doesn't work. From various threads here over the years I get the sense that some Seagate drives are or have been a recurring problem. Unfortunately, this sort of annoyance can occur in Windows and MacOS as well as Ubuntu. With the four variables I listed there are zillions of combinations of possible conflicts to deal with so good luck to the developers! It was particularly frustrating to find my SATA docking station would not work with Ubuntu on my Vaio.

Good luck with your choice of an enclosure and docking station. :|

---

### Post by ZhuaSD on 2010-10-12
Hey coffeecat, I meant no harm with the unfiltered.  Unfiltered is good! :P

Yeah, I guess you are right.  I will try out a new enclosure just to see, would be funny if that did the trick.

With all the variables you mentioned, it seems easy for things to break down. If Ubuntu was M$, they would issue standards that the drive and enclosure manufacturers would have to follow.

But then, M$ sucks, so there you go  :guitar:

Peace my friend, and thanks for your knowledge on the subject!  :)

Smileys rock!!  :mad:

---

### Post by QLee on 2010-10-12
I seem to remember (well, almost remember) that there have been some issues around WD drives around the jumpering. Some models at least, have a master, single and master, with slave present, option where a lot of drives only have master; slave; and CS. Sometimes too, new drives ship jumpered as slave (I suppose because a new drive might be an "addition") and sometimes that doesn't get changed appropriately during assembly. I think in many instances a drive can work OK jumper as slave even if it isn't the second drive on an IDE port. I don't remember if cable select always worked or not. However, I also think some hardware doesn't work perfectly in every situation when a drive might be jumpered incorrectly. I don't know if this is going to apply to your issue but it might and I wanted to mention it in case you think it worthwhile to check the jumpering. Sorry my memory of the issue is so sketchy.

---

