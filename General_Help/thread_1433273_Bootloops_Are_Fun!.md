---
title: "Bootloops Are Fun!"
date: 2010-03-18
forum: General Help
---

### Post by Sanus Compleo on 2010-03-18
So my computer was booted to Ubuntu (Karmic), and the power went down.  Logged back on, and it got stuck in a bootloop.  Logged onto the earlier kernel (I think that's what it is), and it works.  Everytime I log into the 2.6.31-20 kernel it goes back to Bios.  Help?

---

### Post by dcstar on 2010-03-18
> **Sanus Compleo said:**
> So my computer was booted to Ubuntu (Karmic), and the power went down.  Logged back on, and it got stuck in a bootloop.  Logged onto the earlier kernel (I think that's what it is), and it works.  Everytime I log into the 2.6.31-20 kernel it goes back to Bios.  Help?

Use a Live CD to do a fsck on the partition and then boot the good kernel and reinstall all the later kernel packages.

---

### Post by Sanus Compleo on 2010-03-18
Alright, well I requested a CD (eight different cds I've burned have been corrupted, even after re-downloading the package over and over), so I should be good to go in a few weeks.  (Not complaining, a free OS is pretty awesome)  Also isn't 2.6.31-14 part of the same partition?  Or is that what that is?

---

### Post by hansdown on 2010-03-18
Hi Sanus Compleo.

2.6.31-20 is the latest kernel, to date.

A power outage has the potential to corrupt files, so you could boot into 2.6.31-14 , and use update manager to get the newer kernel.

---

### Post by Sanus Compleo on 2010-03-18
What would the package look like?

---

### Post by lordskid on 2010-03-18
try running synaptic from the old kernel and search for 2.6.31-20 there should be three files 

linux-headers-2.6.31-20
linux-headers-2.6.31-20-generic
linux-image-2.6.31-20-generic

reinstall all of them.

---

### Post by Sanus Compleo on 2010-03-18
How do I search with the package updater?  The software center comes up with nada.

---

### Post by hansdown on 2010-03-18
> **Sanus Compleo said:**
> How do I search with the package updater?  The software center comes up with nada.

Click system> administration> update manager.

---

### Post by Sanus Compleo on 2010-03-18
Well... yeah, but it gives me no option to search, and there was nothing that had 2.6.31-20 on it.

---

### Post by tilixibr on 2010-03-18
I didnt get a bootloop but my screen got all messed up, the whole desktop got shifted to the right and on the left it was the right side of the desktop, but i couldnt do anytinhg, the icons didnt work and the mouse was frozen, had to reboot manually (hold the power button for 6s) and swithed to 2.6.31-19....... now everything works fine as I'm posting this...

---

### Post by tilixibr on 2010-03-18
> **Sanus Compleo said:**
> Well... yeah, but it gives me no option to search, and there was nothing that had 2.6.31-20 on it.
use the synaptic package manager (System>Administration>Synaptic Package Manager), and search for "linux-image", the newest version (2.6.31-20) should be there, click on it and mark for reinstallation then click "apply". The update manager only updates, as it says in the name...

---

### Post by Agent ME on 2010-03-18
> **Sanus Compleo said:**
> How do I search with the package updater?  The software center comes up with nada.
System -> Administration -> Synaptic Package Manager is what you want.

EDIT: Just beaten to this post.

---

### Post by tilixibr on 2010-03-18
> **Agent ME said:**
> System -> Administration -> Synaptic Package Manager is what you want.

EDIT: Just beaten to this post.
1st place XP :lolflag:

---

### Post by Sanus Compleo on 2010-03-19
So... what package should I be looking for?

EDIT: Nevermind, didn't see page 2, looking now.

---

### Post by Sanus Compleo on 2010-03-19
Wooo... So I'm booting into Ubuntu right... or, trying... Click it in OS chooser... goes to grub minimal bash shell.  Yaaaay.  Help?

EDIT: If help fails, I can just run wubi again.  Le sigh.  I do have lots of documents to retrieve, not sure how to do that from windows.

---

### Post by Sanus Compleo on 2010-03-19
So, starting to find my problem here, I think.  Couldn't update the images, cause I used Wubi, going to use it again to install, that's fine and dandy, but how can I retrieve my files from Windows?  I've used several software programs that just.... did nothing.

---

### Post by tilixibr on 2010-03-19
> **Sanus Compleo said:**
> So, starting to find my problem here, I think.  Couldn't update the images, cause I used Wubi, going to use it again to install, that's fine and dandy, but how can I retrieve my files from Windows?  I've used several software programs that just.... did nothing.
You mean the files in the the root.disk file? I have no idea on how to do it. What I did was save all my files from ubuntu in a Windows directory, just in case that kind of thing happens....

---

### Post by Sanus Compleo on 2010-03-19
Okay, well, retrieved files, but my current ubuntu partition is only like... 3 gigs, I would like it to be much higher, is there any way to increase that?  Gparted doesn't recognize it as a partition, because it's not really a partition, just a windows file.

---

### Post by tilixibr on 2010-03-19
> **Sanus Compleo said:**
> Okay, well, retrieved files, but my current ubuntu partition is only like... 3 gigs, I would like it to be much higher, is there any way to increase that?  Gparted doesn't recognize it as a partition, because it's not really a partition, just a windows file.
i dont think you can resize it, yhe only way I know is to reinstall it and make it bigger...

---

### Post by Sanus Compleo on 2010-03-20
Woo!  That was a fun day of utter suck.  So my Ubuntu 9.10 CD came in the mail (Hallelujah!), and started to install, everything went smooth, until I rebooted it.  Bios (Phoenix AwardBios 6.00PG or w/e) stalled on "Grub is Loading."... forever.  Rebooted, booted back to live cd, found some stuff, used lilo to get a new mbr on sda (First harddrive), and installed grub on sdb (Second harddrive, Ubuntu partition, still with me?  Good!).  Booted up, and joy glory hallelujah!  I've got Windows for the time being.  (I'm sure it's only temporary)  Now, to get the good OS back, meaning Ubuntu of course!  C'mon guys, help me out, why isn't Grub working?  It worked when I used wu...bi... maybe... Maybe I can frankenstein Wubi's grub settings?  So that it uses the generic boot loader, and then goes into a working grub upon choosing Ubuntu?  How do I do that?  Halp.  :C

EDIT: so... is anyone going to ask for any outputs from the LiveCD terminal or anything?  I finally HAVE a liveCD to use.  Please?

EDIT2: Found a wubi.mbr line in boot.ini, although there's no wubi.mbr to be found in the C drive.  How can I change that to open up whatever master boot record I have now?

---

### Post by Sanus Compleo on 2010-03-20
I haven't been able to find the rules on bumping since the old forums got archived, so... Please don't ban me:
Bump.

---

### Post by cgroza on 2010-03-20
> **Sanus Compleo said:**
> Alright, well I requested a CD (eight different cds I've burned have been corrupted, even after re-downloading the package over and over), so I should be good to go in a few weeks.  (Not complaining, a free OS is pretty awesome)  Also isn't 2.6.31-14 part of the same partition?  Or is that what that is?
  8 cd's ... !!!???:eek:

---

### Post by Sanus Compleo on 2010-03-20
Yep.  Eight.

---

### Post by Sanus Compleo on 2010-03-20
Okay, so this guide told me to do some dd command and I made a ubuntu.bin file in C, and and and...  I set the boot.ini file to boot to ubuntu.bin, and the guide said it was 'sposed ta work... but it really didn't.  It hang at a flashing underscore.  Probably going to have to reinstall Ubuntu yet again, though since that didn't help the second time, I don't think it'll help this time.  (By the way, used Lilo to fix the MBR, so that it uses Window's MBR before anything.  It cannot connect to whatever boots Ubuntu yet.)

EDIT: Also, I assume that Grub2 would just hang back at "Grub is loading." as it has before.

---

### Post by Sanus Compleo on 2010-03-20
Well, I re-reinstalled Ubuntu (Yaaaay!), but Grub still hangs at "Grub is Loading." (Boooo!).  Help guys?  I really want to get this all to work.

---

### Post by tilixibr on 2010-03-20
You installed Ubuntu in its own partition this time right? Did you uninstall the other one(the one which is only a windows file)? I think it may mess up the boot loader, I'm not sure...

---

### Post by Sanus Compleo on 2010-03-20
Okay, it's now 630 PM where I'm at.  I've been up since 3 pm yesterday trying to fix this.  Now, I've got grub working, and Windows might work (Haven't checked yet), only problem is when I try to boot into ubuntu, it says that device (My device's long uuid) doesn't exist!  Maybe this is an issue in the search command?  Either way... Please Please Please help.

---

