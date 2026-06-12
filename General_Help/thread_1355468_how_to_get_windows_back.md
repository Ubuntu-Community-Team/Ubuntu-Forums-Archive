---
title: "how to get windows back"
date: 2009-12-15
forum: General Help
---

### Post by inversionce on 2009-12-15
I installed linux and I was wondering if theres anyway i can get my windows xp back on. I dont have the xp disc anymore. and when my computer starts back up it  shows linux then under that is a linux recovery mode and  another linux and another recovery and theres about 9 of them, and there all the same. But no windows XP

---

### Post by Mr Nemo on 2009-12-15
How did you install linux (ubuntu...?)? Did you dual boot or completely use the disc?

---

### Post by inversionce on 2009-12-15
yeah it was ubuntu and i used a disc

---

### Post by Mr Nemo on 2009-12-15
When you installed Ubuntu, did you choose the option to install it side by side with windows or did you choose the option to overwrite windows and use your whole harddisk?

---

### Post by MooPi on 2009-12-15
Well inversionce, do you own a laptop or desktop. Model# and Make ? Can you find the Microsoft COA ( Certificate Of Authenticity) sticker ? Do you have a friend that has a XP install disc ?

---

### Post by inversionce on 2009-12-15
i have a feeling i chose the whole harddisc option. is there a way to find out?

---

### Post by F3arMagick on 2009-12-15
> **inversionce said:**
> i have a feeling i chose the whole harddisc option. is there a way to find out?
Tell us what's in '*Places -> Computer*'

---

### Post by Mr Nemo on 2009-12-15
As far as I know you've lost all of your files from windows. Hopefully MooPi or someone else will know how/if you can recover your files. You can of course reinstall XP if you can find a disk.

---

### Post by inversionce on 2009-12-15
its a desktop i dont know anybody with a windows xp disc.  the computer looks pretty old and only thing i can see is tandex logo and a intel inside Pentium 4 sticker.

---

### Post by inversionce on 2009-12-15
20.5 GB Media
CD-RW Drive
Floppy Drive
Disk
Filesystem

---

### Post by F3arMagick on 2009-12-15
> **inversionce said:**
> 20.5 GB Media
CD-RW Drive
Floppy Drive
Disk
Filesystem
That looks like you've overwritten everything from XP.  Sorry, but your files are most likely gone.

---

### Post by Mr Nemo on 2009-12-15
what happens when you click on the 20.5 media icon?

---

### Post by inversionce on 2009-12-15
It brings up these files:
Bin
boot
cdrom
dev
etc
home
initrd
lib
lost+found
media
mnt
opt
proc
root
sbin
srv
sys
tmp
usr
var

and this box with an arrow
initrd.img

paper with arrow:
initrd.img.old
vmlinuz
vmlinuz.old

paper with some letters:
usplash.conf

---

### Post by MooPi on 2009-12-15
Boot from the Ubuntu disk and after it has loaded go to the top bar and look for " Places" pull down the menu and open "Computer"
If more than one hard disk is listed then your XP installation probably exist. If you see two open them up and see what the contents hold.

---

### Post by Mr Nemo on 2009-12-15
Go ahead and try what MooPi said, but it looks like you completely overwrote windows xp with ubuntu.

---

### Post by Cope57 on 2009-12-15
[www.support.microsoft.com](www.support.microsoft.com)

---

### Post by lisati on 2009-12-15
My $0.02: from the terminal, do the following, which should show if there's anything not accessible via the Places menu:
```
sudo fdisk -l
```
If you're in luck it will show an NTFS partition of some kind, and, hopefully a recovery partition. If not, as others have said, you'll have to track down a Windows disk (preferably a legal one) and possibly the Windows key/serial number (often on the side of a desktop machine, and on the bottom of a laptop)

---

### Post by TetonsGulf on 2009-12-15
Like the others here, I think your XP installation is probably gone, but I have to ask...

What's pulling you back into Windows? If you have that many kernels in the boot menu it would seem that you've been running Linux for more than a couple months, so what's up? Maybe it's something we can help with, maybe not, but it can't hurt to ask.

What were you hoping to use the rig for? I'm not an expert but I would say an average user would have a music library of about half of that hard drive! That's not to mention the lack of a DVD writer/burner.

What's the goal of going back to XP as opposed to keeping Linux or upgrading to a new PC?

---

### Post by inversionce on 2009-12-15
ok i just opened the terminal and typed sudo fdisk -l in and it says at the bottom for systems is :
Linux
Extended
Linux
Linux Swap
Linux Swap



and im just going to boot up the cd and check the places and tell you whats in there

---

### Post by MooPi on 2009-12-15
No need really your XP files seem to be Missing. I'd like to suggest letting the forum and it's helpful crew correct you Linux install.  Seems like you've got one to many swap on the hard disk.

---

### Post by inversionce on 2009-12-15
any help would be amazing. 

what I want to go to windows for is so i can finally put music on my Zune ahahaha. and play some starcraft. and its just easier for the rest of my family to do things when im not around and they need to do something. (sometimes they can't find the firefox icon at the top ahahaha)

---

### Post by MooPi on 2009-12-15
Well it's late for me and I'll have to look you up later as I need my 40 winks. I'll log on early tomorrow and see how your progressing.

---

### Post by TetonsGulf on 2009-12-15
> **inversionce said:**
> any help would be amazing. 

what I want to go to windows for is so i can finally put music on my Zune ahahaha. and play some starcraft. and its just easier for the rest of my family to do things when im not around and they need to do something. (sometimes they can't find the firefox icon at the top ahahaha)

Starcraft can be played through Wine, see [http://joshhighland.com/blog/2008/02/26/starcraft-in-ubuntu-yes-drink-the-wine]("http://joshhighland.com/blog/2008/02/26/starcraft-in-ubuntu-yes-drink-the-wine/").

As for familiarity with the XP GUI for your family, you can try [http://ubuntuforums.org/showthread.php?t=821146]("http://ubuntuforums.org/showthread.php?t=821146").

I have no experience with the Zune and Ubuntu, but I'm assuming there will be problems there, much like there are with iPhones and iTouches.

Hope that helps, and good luck!

---

