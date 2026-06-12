---
title: "how to fix bootloader on unbootable HD with single DVD drive"
date: 2012-04-20
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2012-04-20
It's one of those horse shoe nail stories that begins with pouring a liter of water in my monitor and then stuff happens.  Anyway, while waiting for the U.P.S. guy to bring me some hardware that may make things easier the challenge is this:

I've got a hard drive with a good Oneiric on sda2 which is the only primary usable as a boot partition, sda1 being only 2 mb, a borked GRUB, and an sda7 partition perfectly suitable as a bootable partition (it had Maverick until the same recent misadventure in which GRUB was a casualty). Since the single cd/dvd drive is the only thing I can boot from until I get the HD bootable I can't burn a CD or DVD. I'm limited to what I already have on hand which is a miscellany of bootable CDs and DVDs accumulated over years.

Isn't there a way I can repair the GRUB or install some bootloader (I've always wanted to try LILO) on the hard disk while booted from the CD/DVD drive?    The other solution of course is to install another OS on sda7 and work from there. But so far I haven't been able to get any of the installation CDs that will install to a non-primary partition to work with the VGA.

And I'm a bit reluctant to wipe out my Oneiric with all the tweaking I've done on sda2. I do have it backed up with remastersys live disks which is what I'm booting from atm, but they are failing when I try to restore the backed up system to sda7 and I'm therefore reluctant to count on them.

I also tried to install from a cd made from the oneiric mini iso and it also failed to work with the VGA which I find surprising since the HD Oneiric installation had no problem with the VGA before I screwed up the GRUB, nor does the remastersys-made Oneiric live disk/system backup disk. I can't find the installation disk I installed the Oneiric from originally.

I tried forcevesa modes on some of these things but it didn't help. I thought that "text install" options would be just that and should work but the darn things popped up an unreadably distorted gui anyway. I guess they should be called "mostly text" options. I think the native resolution on this monitor is 640 x something and the installers are treating it as higher than that. Not the ubiquity installer on the remastersys-made Oneiric system-backup/live-disk. It's failing for some other reason under the category "ERRNO 9 ... [huge error message in a gui pop up box that won't let me copy it and suggest eleventy-seven possible causes with the leading candidate being a bad DVD]"
_________
Edited later 'cause I figured out what made the forum eat my line feeds & fixed it. Firefox extension NoScript blocking java script causes that.

---

### Post by ZekeGraal on 2012-04-20
Unfortunately I think you're stuck until you can burn a CD. Find a friend with a computer and make a boot repair disk as outlined here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Read under the heading "Getting boot-repair" and follow the instructions.

Good luck!
~Zeke

---

### Post by oldfred on 2012-04-20
Boot-Repair is both a liveCD of its own or an app you can download into most LiveCDs.

If booting Windows you can install the lilo boot loader, or you can repair grub. I think Boot-Repair installs syslinux boot loader as it also works like lilo or the Windows boot loader in looking for a boot flag and jumping to the PBR to find more boot code.

Restore basic windows boot loader - universe enabled if error on lilo not found
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If you want to directly reinstall grub2's boot loader.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

But if your install has major issue you may have to chroot into it and repair it.
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

---

### Post by Dreamer Fithp Apprentice on 2012-04-22
> **ZekeGraal said:**
> Unfortunately I think you're stuck until you can burn a CD. Find a friend with a computer and make a boot repair disk as outlined here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) Read under the heading "Getting boot-repair" and follow the instructions.

Good luck!
~Zeke
Thanks, Zeke. I've already tried boot-repair. There are several things I could do if I could burn a new CD or DVD from scratch. All these problems will be solved by the UPS guy bringing some stuff in the pipeline soon. In the meantime, I'm trying to take it as a puzzle/challenge to see if I can do it before he gets here without offsite resources so to speak.

> **oldfred said:**
> 
If booting Windows you can install the lilo boot loader, or you can  repair grub.
Thanks, Fred.  I don't have Windows on the system atm and rejected the idea of installing it because if I recall correctly, Windows insists on using a primary partition so I'd have to overwrite the Oneiric installation. But I hadn't thought about going through part of the installation procedure and stopping short of overwriting sda2 which part of your post seems to suggest as a possibility. In making me think about Windows, you've also reminded me I may have an old IDE drive with W2k on it somewhere. That could at least provide a platform from which I could burn a DVD if nothing else. I'll look for it. I should have thought of that.

> **oldfred said:**
> 
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

Tried something similar and didn't get it to boot. Then I read your post and tried this exact syntax and then other concerns demanded my attention and I'm just getting back to it.  Hasn't booted yet but I will try this again and look up all the error messages to see if there is anything in them suggesting an avenue of attack.

I've also tried some approaches involving chroot. With that I have only a vague understanding of what I'm doing and I'm mostly just copying and pasting stuff into the terminal.  I'll study chroot some and give these other links you mention a go. I do appreciate this.

Don't anybody knock yourself out over this. I'm not hurting. I can boot from my remastersys-made Oneiric backup CD and I can access the data on my hard drive just fine. And soon new hardware will fix things if I don't figure out a way before it gets here.  Right now it's as much a puzzle I want to work through to stretch my mind as anything. The surprising part to me is that my remastersys-made Oneiric system backup disk can boot live and has no problem with VGA while none of my other install disks, including older versions of Ubuntu and Sabayon, and current versions of PC-BSD and Dragonfly BSD, all of which worked fine with my more modern monitor, can't work with the VGA.

---

### Post by oldfred on 2012-04-22
Lilo, syslinux & Windows boot loaders all boot Windows. You have to install all of Lilo or syslinux not just boot loader to boot anything other than Windows.

If install is configured correctly you can just install grub2's boot loader to the MBR. But if other changes are needed then a full chroot or reinstall is required.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

You can also run a lot of repair, refresh, update & reinstall commands from the chroot.

---

