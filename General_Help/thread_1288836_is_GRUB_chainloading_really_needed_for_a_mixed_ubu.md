---
title: "is GRUB chainloading really needed for a mixed ubuntu/vista machine?"
date: 2009-10-11
forum: General Help
---

### Post by wamanning on 2009-10-11
isnt the bios drive-selection power-up menu enough?  

i'm in the process of re-staging my machine and here's my thinking...with a completely independent install of ubuntu on /dev/sda and vista on /dev/sdb...why bother with commingling those bootloaders with GRUB?

why not have GRUB manage just /dev/sda and *SEPARATELY* the windows bootloader just manage /dev/sdb...at power-up i get a drive-select menu where i can just pick the drive i want to use.

my plan is eventually/soon to access the vista partition via virtualbox, and this method will avoid the potential problems of booting into linux inside of a virtual machine that's being run inside linux.  since the option to boot into vista doesnt appear on GRUB, i avoid that problem completely.

am i missing something?  quite likely i am!  :)

---

### Post by jeremyswalker on 2009-10-11
Grub shouldn't be installed to the MBR of both drives, only the one. Have you changed the boot first device to the Vista drive to see if it boots?

---

### Post by jeremyswalker on 2009-10-11
..

---

### Post by wamanning on 2009-10-11
> **jeremyswalker said:**
> Grub shouldn't be installed to the MBR of both drives, only the one. Have you changed the boot first device to the Vista drive to see if it boots?

correct.  i'll have ONLY GRUB on /dev/sda and ONLY the vista bootloader on /dev/sdb.  yep -- the machine is already booting to vista now (just restaged from scratch) in that position.  

it is VERY important to disconnect /dev/sda before starting the vista install to /dev/sdb, so that vista doesnt see any other drives.

i actually forgot to do that and accidentally wiped out part of my linux partition...when i realized my error, literally 5 seconds after vista started doign its thing, it was too late...so i'm re-staging linux on /dev/sda from scratch.  :( :( :( 

at least i have a fresh backup of all my important files - phew!  :)

for the ubuntu install to /dev/sda, to be sure GRUB doesnt try to do anything w/ vista on /dev/sdb i'll disconnect that drive.

doing some googling...found someone else that describes essentially the exact process i'm going thru...great minds, eh?!  ;)

[http://www.faqs.org/docs/Linux-HOWTO/MultiOS-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/MultiOS-HOWTO.html)

---

### Post by rb0171610 on 2009-10-11
> **wamanning said:**
> isnt the bios drive-selection power-up menu enough?


Do you mean to say that your computer has a menu that pops up automatically upon booting that asks you which drive you wish to boot from, sda or sdb for example?  Is this automatic or can it be turned off?  I am just curious.

---

### Post by LoREZ on 2009-10-11
> **rb0171610 said:**
> Do you mean to say that your computer has a menu that pops up automatically upon booting that asks you which drive you wish to boot from, sda or sdb for example?  Is this automatic or can it be turned off?  I am just curious.

That would be wicked.  Hopefully the answer is "yes" and "yes" followed by the model of the motherboard...  :popcorn:

---

### Post by rb0171610 on 2009-10-11
> **LoREZ said:**
> That would be wicked.  Hopefully the answer is "yes" and "yes" followed by the model of the motherboard...  :popcorn:

Hopefully "yes" as in "Yes it can be turned off?" LOL.  I would hope. ;)

---

### Post by LoREZ on 2009-10-11
LOL.  True.  I'm not a glutton for pain...

---

### Post by rb0171610 on 2009-10-11
I guess I don't see what the benefit would be. You get to bypass Grub if you are going to boot from the Windows drive? In this scenario, does Vista on sdb need boot files to be stored on sda?

---

### Post by CatKiller on 2009-10-11
> **wamanning said:**
>  why not have GRUB manage just /dev/sda and *SEPARATELY* the windows bootloader just manage /dev/sdb...at power-up i get a drive-select menu where i can just pick the drive i want to use.

That's absolutely fine. I used to do it myself for similar reasons.

Disconnect the *other* drive when you install *either* OS, and there's no reason at all why either OS should know of the existence of the other.

---

### Post by rb0171610 on 2009-10-11
> **CatKiller said:**
> That's absolutely fine. I used to do it myself for similar reasons.

Disconnect the *other* drive when you install *either* OS, and there's no reason at all why either OS should know of the existence of the other.

I guess the trouble of disconnecting and reconnecting the drive is why I would never think to do such a thing. LOL.  I'd have to unplug the computer, open it up, unplug, close it up, restart, install, and repeat.  And in his case, reinstall Linux.  I'd settle for Grub. LOL.

---

### Post by louieb on 2009-10-11
> isnt the bios drive-selection power-up menu enough?  

2 hard drives = 2 MBRs.  Sure if you want to use Startup drive selection menu to select which drive to boot. That will work. I have a PC thats set up that way. XP in one MBR, GRUB in the other MBR (I can boot XP from GRUB too). 

> my plan is eventually/soon to access the vista partition via virtualbox,

Have see some articles about that - seems to be a pain to set up - let us know how it works out.

---

### Post by CatKiller on 2009-10-11
> **rb0171610 said:**
> I guess the trouble of disconnecting and reconnecting the drive is why I would never think to do such a thing.

It doesn't take too long (especially if you're used to fiddling inside a computer case), and it's not like you need to do it especially often. I've found that a healthy dose of paranoia is a sensible addition to any computer interaction. When I first installed Ubuntu it was on a strictly experimental basis, and I wanted it to be instantly reversible - largely because my housemates were using Windows on my computer pretty frequently and I didn't want to mess anything up for them. Ah, the heady days of 2004... :)

---

### Post by rb0171610 on 2009-10-11
> **CatKiller said:**
> It doesn't take too long (especially if you're used to fiddling inside a computer case), and it's not like you need to do it especially often. I've found that a healthy dose of paranoia is a sensible addition to any computer interaction. When I first installed Ubuntu it was on a strictly experimental basis, and I wanted it to be instantly reversible - largely because my housemates were using Windows on my computer pretty frequently and I didn't want to mess anything up for them. Ah, the heady days of 2004... :)
 I think I was trying to say that Grub seems like a lot less work.  I am not afraid to open a computer. ;) I have built and maintained quite a few systems over the years. 

I understand what you are saying though. That is a benefit I had not thought of. A shared computer. Gotcha.

---

### Post by LoREZ on 2009-10-12
> **rb0171610 said:**
> I think I was trying to say that Grub seems like a lot less work.  I am not afraid to open a computer. ;) I have built and maintained quite a few systems over the years. 

I understand what you are saying though. That is a benefit I had not thought of. A shared computer. Gotcha.

Did you get the idea that one needs to unplug the alternate drive every time an OS is booted?  I don't think that is the situation.  You just do that for installation (once per OS install).  I think you just pick the proper boot drive at startup (sort of a metaMBR) from the BIOS, and each OS can still see the other drive, they just don't mess with the boot sector of the subordinate drive.  The advantage is that it's impossible to foul up the works by overwriting MBRs.  This actually would be very helpful if you want to see if a distro will work on your hardware, because liveCDs aren't always enough.  Ubuntu proved that to me the hard way.  And it does add a comfort level to experimentation when you have to maintain workspace for somebody else.

---

### Post by rb0171610 on 2009-10-12
> **LoREZ said:**
> Did you get the idea that one needs to unplug the alternate drive every time an OS is booted?  I don't think that is the situation.  You just do that for installation (once per OS install).  I think you just pick the proper boot drive at startup (sort of a metaMBR) from the BIOS, and each OS can still see the other drive, they just don't mess with the boot sector of the subordinate drive.  The advantage is that it's impossible to foul up the works by overwriting MBRs.  This actually would be very helpful if you want to see if a distro will work on your hardware, because liveCDs aren't always enough.  Ubuntu proved that to me the hard way.  And it does add a comfort level to experimentation when you have to maintain workspace for somebody else.

No, I understood all of that. I just could not understand why you would not just let grub install itself to the MBR and go from there as one normally does on a dual boot situation.   It makes perfect sense if you are on a shared computer. I just couldn't fathom why someone would go to all that trouble to avoid installing grub to the MBR. Well I would have to say though, it might be helpful if you are not sure how to restore the MBR back to its original state. It is an easy situation to remedy, especially since each OS is on its own drive.  But it makes perfect sense that you would not want to bother someone else's Windows installation if you can avoid it.  They simply have to select which drive they want to boot from on startup, as you would with grub. Except this way, you dont have to touch the MBR of the Windows Drive.  I guess I just have a lot of experience and think that is extremely over cautious, unless it is not your computer. Then I can entirely understand.

---

### Post by P4man on 2009-10-12
Of course it works. And to the poster who asked, most motherboards have such a feature. This only works for physical harddrives though, you can't make the bios boot a certain partition (ie, no dual booting with 1 hdd). On my BIOS I can access the boot menu using F11, but it varries from machine to machine.

Some advantages: if a drive fails or you remove it, the other OS still works fine. Its idiot proof to install.

Disadvantage: slightly tedious if you (re)boot often. You have to endure the bios boot menu, and then still the slow down of grub (if you boot linux). 

You can work around the disadvantage by combining both approaches. Thats how I set it up: sda has windows with windows bootloader and can be booted independently, sdb has linux with grub, and grub also configured to boot windows on sda. This gives me all of the advantages and none of the disadvantages :)

---

### Post by LoREZ on 2009-10-12
You are both right.  But as for the experience question, if you are trying many different operating systems (as I do), some of which are poorly documented and not common (not *nix or ms), then sometimes you won't have the luxury of experience.  I'm a tinkerer.  That's why I run linux to begin with.  Running vms isn't enough many times to get a true since of an OS or how it works on your machine.  Frankly, I don't relish the idea of running grub at the command line everytime I screw up, or having to mess with ntldr, etal.  I'd rather have a reference system that I know will work once I'm fed up with messing about and just want to go to sleep and wake up with a working rig.  It's the laziness in me.  Plus, I don't really like the idea of a bootloader bloated with a bunch of fly-by-night installs from my half-baked schemes...

---

### Post by CatKiller on 2009-10-12
> **rb0171610 said:**
> No, I understood all of that. I just could not understand why you would not just let grub install itself to the MBR and go from there as one normally does on a dual boot situation.   It makes perfect sense if you are on a shared computer. I just couldn't fathom why someone would go to all that trouble to avoid installing grub to the MBR. 

It's a guarantee, that's all. At the point where you know quite a lot about hardware but absolutely nothing about GRUB (or GNU/Linux for that matter) it means that you absolutely know that you won't cock anything up. It was my computer that I was experimenting with, but I didn't want there to be a situation where my housemates urgently needed to do something in Windows and I'd broken it. I rarely needed to do anything urgently.

As it turned out, some months later when I shuffled the partitions around I did break Windows. It's just too fragile. By that time they were both comfortable with Ubuntu so I never bothered to fix Windows. When they got their own computers, they put Ubuntu on those, too. We've never looked back.

---

### Post by rb0171610 on 2009-10-12
> **CatKiller said:**
> It's a guarantee, that's all. At the point where you know quite a lot about hardware but absolutely nothing about GRUB (or GNU/Linux for that matter) it means that you absolutely know that you won't cock anything up. It was my computer that I was experimenting with, but I didn't want there to be a situation where my housemates urgently needed to do something in Windows and I'd broken it. I rarely needed to do anything urgently.

As it turned out, some months later when I shuffled the partitions around I did break Windows. It's just too fragile. By that time they were both comfortable with Ubuntu so I never bothered to fix Windows. When they got their own computers, they put Ubuntu on those, too. We've never looked back.
Awesome.

---

### Post by wamanning on 2009-10-12
> **rb0171610 said:**
> I just could not understand why you would not just let grub install itself to the MBR and go from there as one normally does on a dual boot situation.

for me, the driver is virtualbox and not wanting the 2 OSes to be commingled at all.

---

### Post by rb0171610 on 2009-10-12
> **wamanning said:**
> for me, the driver is virtualbox and not wanting the 2 OSes to be commingled at all.
Yes, I can understand there are reasons someone would need this setup.  I just couldn't think of a scenario to save my life.  It does not apply to me is why.  
I am happy with grub on the MBR.  I am not afraid to mess anything up. I do not share my computers.  I do not want the bios to pop up a drive selection menu on start.  
For the last time, I can see now why others would want to go to the trouble of having two completely independent hard drives with their respective boot managers and MBR's managed by the bios selection dialog on start up. I get it, I respect it.  
Peace.
:P

---

### Post by P4man on 2009-10-12
> **rb0171610 said:**
> 
For the last time, I can see now why others would want to go to the trouble of having two completely independent hard drives with their respective boot managers and MBR's managed by the bios selection dialog on start up. 

BIOS will only prompt when you press the function key on boot up (not unlike pressing escape in grub), and its entirely optional. Dont press the key, and it will just boot the default drive. 

 Having a bootloader on either drive isn't any extra work, each OS will install one anyway, just let it do its thing. 

If you got 2 drives, both dedicated to another OS, I can't see a reason NOT to have a workable bootloader on each. You can still use grub menu to chainload the other OS than your bios default, my boot process is exactly like yours (I use grub on sdb to boot windows on sda), except mine still works with either drive is removed, fails,  if I mess up or decide to remove one or the other OS 

;)

---

### Post by rb0171610 on 2009-10-12
> **P4man said:**
> BIOS will only prompt when you press the function key on boot up (not unlike pressing escape in grub), and its entirely optional. Dont press the key, and it will just boot the default drive. 

 Having a bootloader on either drive isn't any extra work, each OS will install one anyway, just let it do its thing. 

If you got 2 drives, both dedicated to another OS, I can't see a reason NOT to have a workable bootloader on each. You can still use grub menu to chainload the other OS than your bios default, my boot process is exactly like yours (I use grub on sdb to boot windows on sda), except mine still works with either drive is removed, fails,  if I mess up or decide to remove one or the other OS 

;)
I don't have any use for it.  I only have Linux on my desktop.  I only have the one hard drive.   I have a file server with two hard disks.  My laptop is dual boot Vista/Kubuntu.

So this scenario does not apply to me.

---

### Post by rb0171610 on 2009-10-12
> **P4man said:**
> BIOS will only prompt when you press the function key on boot up (not unlike pressing escape in grub), and its entirely optional. Dont press the key, and it will just boot the default drive. 

 Having a bootloader on either drive isn't any extra work, each OS will install one anyway, just let it do its thing. 

If you got 2 drives, both dedicated to another OS, I can't see a reason NOT to have a workable bootloader on each. You can still use grub menu to chainload the other OS than your bios default, my boot process is exactly like yours (I use grub on sdb to boot windows on sda), except mine still works with either drive is removed, fails,  if I mess up or decide to remove one or the other OS 

;)
I understand.

---

