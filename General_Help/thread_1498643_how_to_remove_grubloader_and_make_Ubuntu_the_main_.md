---
title: "how to remove grubloader and make Ubuntu the main OS system"
date: 2010-06-01
forum: General Help
---

### Post by Zerocool Djx on 2010-06-01
Ok,.. I am going to delete the windows partition and just run it in VB inside Ubuntu if I ever need to,... why? cause I hate windows but WINE isn't running the programs I need....

SOOOO.... all I need to know is how do disk partitions, grub loader, MBR,.. all this work?

as it is right now I got a dual boot with Ubuntu... Grub loader pops up upon power up and you get to choose... I want to remove grub loader, and the wondows partition and expand the linux partition to the whole hard drive. 

My number one question is,.. how to I point the computer to load Ubuntu on power up without loading grub, so it will just load Ubuntu...??

---

### Post by xfearxnxloathing on 2010-06-01
> **Zerocool Djx said:**
> Ok,.. I am going to delete the windows partition and just run it in VB inside Ubuntu if I ever need to,... why? cause I hate windows but WINE isn't running the programs I need....

SOOOO.... all I need to know is how do disk partitions, grub loader, MBR,.. all this work?

as it is right now I got a dual boot with Ubuntu... Grub loader pops up upon power up and you get to choose... I want to remove grub loader, and the wondows partition and expand the linux partition to the whole hard drive. 

My number one question is,.. how to I point the computer to load Ubuntu on power up without loading grub, so it will just load Ubuntu...??

once the windows partition is delete it should boot straight to ubuntu.  you can expand the partition to the whole disk via gparted im pretty sure.  Applications>Ubuntu Software Center (at the very bottom), search gparted.  you can move your ubuntu installation to the front of the disk in gparted aswell.

---

### Post by Elfy on 2010-06-01
Assuming that ubuntu is number one on the list - you just need to hide the grub menu - do not remove grub.

To remove windows and use the freed up space you will need to boot the livecd - there is a partition editor in the sys admin menu.

To allow you to resize the linux partition it is likely you will need to turn off the swap - right click the swap partition and choose from the menu.

Before you can add the free space to your install partition you need to expand the extended partition if you have one - which is likely. Then you can add the space to the install.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

---

### Post by Elfy on 2010-06-01
See also [http://ubuntuforums.org/showthread.php?t=1498611](http://ubuntuforums.org/showthread.php?t=1498611) where the OP is discussing the same thing.

---

### Post by BoneKracker on 2010-06-01
You don't.

You need to run a bootloader, even if linux is the only operating system on your machine.  You can, however, configure it so that you never see it and it just boots right into linux automatically.  Refer to the GRUB documentation.

I don't use GRUB2, so you should confirm the specifics of the rest of what I tell you below.

GRUB comes up for a period of time (specified by the variable "timeout" in your GRUB configuration) and waits for you to make a choice.  If you set that to 0, it will just skip showing you the menu and immediately boot the default.  If you do want to access the menu, you can press Esc as GRUB is starting and the menu will come up.  I don't recommend this, because you may forget what you're supposed to press, and you may want to load the rescue option some time.

But if you want to do it, you can scout around in the forums and the wiki, and I'm sure you'll find instructions on configuring GRUB2.

As to the partitioning, first make sure you back up any important files, because people have a way of losing data when they're trying to move or resize partitions. You want to boot into the CD to do that, because you can't mess with partitions that you are running.  Using Gparted is the easiest way to go about this sort of thing.  From there, you can delete the Windows-related partition (or partitions).  Do that first and apply the change.

The rest should be pretty obvious.  I recommend doing things one at a time and applying the change before going on to do more.  Assuming your Windows partition was first on the disk with your Linux partitions to the "right", you want to work from the left to the right.  Move a partition to the left, expand it to the right if necessary, apply the change.  Then move on the next one.  If you have partitions inside an extended partition (i.e. "logical" partitions), then you must first expand the extended partition before moving and growing the logical partitions it contains.

There are limitations on moving and growing certain kinds of filesystems, but if you're using only ext partitions, you shouldn't have a problem.  Don't waste time moving the swap partition because swap is trashed when you boot anyway, just turn the swap off, delete it and create a new one in the new place.  If you have separate partitions for /tmp or /var/tmp (which you probably don't) the same goes for them.

Remember: back up important files first.

[Edit: dang -- 100% redundant with faster posters above] :)

---

### Post by Zerocool Djx on 2010-06-01
> **forestpiskie said:**
> Assuming that ubuntu is number one on the list - you just need to hide the grub menu - do not remove grub.

To remove windows and use the freed up space you will need to boot the livecd - there is a partition editor in the sys admin menu.

To allow you to resize the linux partition it is likely you will need to turn off the swap - right click the swap partition and choose from the menu.

Before you can add the free space to your install partition you need to expand the extended partition if you have one - which is likely. Then you can add the space to the install.

[https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")


Ok,.. I'm going to leave grub a lone then it seems liek a pain so silence anyway,.. Is there anyway I can remove windows xp from the list then? like edit it? and how would I do that?

---

### Post by Elfy on 2010-06-01
Edit the file as root

```
gksudo gedit /etc/default/grub
```

Find this line 

GRUB_HIDDEN_TIMEOUT=0

make sure there is no # at the beginning. Save and close editor. Run

```
sudo update-grub 
```

---

### Post by bigsmitty64 on 2010-06-01
Heres a couple good links that should come in handy

[HERE]("http://ubuntuforums.org/showthread.php?t=1195275")  and   [HERE]("http://ubuntuforums.org/showthread.php?t=1302743")

The second one is probably what you are looking for. Even if you don't use them now, bookmark them for future ref!  :)

---

### Post by Zerocool Djx on 2010-06-01
> **forestpiskie said:**
> 
To allow you to resize the linux partition it is likely you will need to turn off the swap - right click the swap partition and choose from the menu.



What do you mean "turn off swap"?

---

### Post by Elfy on 2010-06-01
You cannot work with partitions while they are mounted. 

The swap partition will likely be in use - in gparted when you are trying tow ork with the partitions - right click the swap partition and turn it off. 

I will also take this opportunity to repeat what binekracker said - make sure you have backups of important files.

---

### Post by Zerocool Djx on 2010-06-01
I'm backing up files now,.. I think it will actually be much easyer to just back files up,.. pop in disk and just format thw whole freakin drive,.. I mean I got back ups of all programs, so it would just be a nusance to re install everything in Ubuntu,.. but I done it a few times this week doing program testing and preparing fro this move so it wouldn't be that hard to do really..

---

### Post by BoneKracker on 2010-06-01
> **forestpiskie said:**
> ... The swap partition will likely be in use...
Live CDs typically activate any swap space they find on a system's hard drives.  You can check to see if this is the case once you've booted the LiveCD:
```
cat /proc/swaps
```

---

### Post by Zerocool Djx on 2010-06-01
yea know I been at this for 7 hours now to get this going,.. I had less problems with windows,.... just sayin'


Is there like certain parts your supposed to reset the computer to have changes go into effect? Cause I been fighting with drivers, updates, and all sorts of crap all night. It was like picking a safe blind to get this thing working.

---

### Post by Zerocool Djx on 2010-06-01
you know something funny,... after I got all this set up the way I wanted,... Win XP actually runs faster (than as if where on it's own on a dual boot in it's own partition) in Linux, in VB... lol that's funny...

---

### Post by BoneKracker on 2010-06-01
> **Zerocool Djx said:**
> I had less problems with windows,.... just sayin'
Well, UNIX variants aren't for everybody.  Maybe you'd be better off with Windows or a Macintosh.

---

### Post by Zerocool Djx on 2010-06-01
> **BoneKracker said:**
> Well, UNIX variants aren't for everybody.  Maybe you'd be better off with Windows or a Macintosh.

Maybe you'd be better off learning how to read some constructive criticism. I know what I am doing. I been building computers for 16 years... A courtesy, "restart now" is all I'm asking for.

---

### Post by BoneKracker on 2010-06-01
> **Zerocool Djx said:**
> Maybe you'd be better off learning how to read some constructive criticism. I know what I am doing. I been building computers for 16 years... A courtesy, "restart now" is all I'm asking for.
That comment was not intended to offend you; it's simply a fact.

---

