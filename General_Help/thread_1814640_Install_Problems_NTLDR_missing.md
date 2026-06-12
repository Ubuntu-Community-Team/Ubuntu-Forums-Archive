---
title: "Install Problems NTLDR missing??"
date: 2011-07-29
forum: General Help
---

### Post by bradlees on 2011-07-29
I am trying to install ubuntu 11.04 from a live cd on a recently formatted 80gb hard drive. Ubuntu seemed to hang and become unresponsive after waits exceeding 40 minutes. As I had some difficulty creating the media, burning the iso to disc, I attempted to install a couple other distros, mint and xubuntu, to see if they worked. These displayed the NTLDR missing message and prompted me to restar
PC: pentium 4 2.93 ghz processor
80 gb hd
512mb RAM
lite on dvd/cd burner 

There is a working 150gb hd with xp on it set as the #2 hd in bios. I would like to install a linux-based os on the smaller drive, preferably ubuntu, but am growing a little impatient.
Any suggestions? Is there a bootloader or anything I will need to install, and what should be the final configuration of the two hard drives once I get another os installed on the hd dedicated to it?

---

### Post by Theredbaron1834 on 2011-07-29
Do you have more the 1 drive?

If not here is what you do:

The problem is that the bootloader isn't working. NTLDR is a part of the windows bootloader. The only time it shows up is when trying to boot a drive that was formatted, but didn't have the boot sectors changed.

First, boot up a live disk. Once booted mount the drive that has /boot/ on it. IE where you installed it.
Run in a term
```
mount | tail -1 
```It will give something like this.
```
/dev/sdX1 on /media/xxxxxxxxxx  type ext4  (rw,nosuid,nodev,uhelper=devkit)
```To make sure this is the right drive type, type this, changing the x's to match what your output says.
```
ls /media/xxxxxxxxxx/boot
```If the output shows an intrd.img, a grub folder, ect then that is the right drive. If not try unmounting the drive and trying it again.

Now that you know the right place to install grub to, let's get to it. Type this, again replacing x's with what you have.
```
sudo grub-install --boot-directory=/media/xxxxxxxxxx/boot /dev/sdX
```

That should replace the boot sector with one to grub.

---

### Post by bradlees on 2011-07-29
I have another drive, with xp running on it. Is there an easier workaround utilizing the other drive?

Thanks

---

### Post by bradlees on 2011-07-29
also, being new to this forum, is there a place to thank other posters?

---

### Post by Theredbaron1834 on 2011-07-30
I don't think that there are any spots to thank posters, except in said thread.

Back on subject of the thread, can you boot up the windows hard drive, I would guess you do. If so, what boot loader do you see when it boots, or do you see one?

Also, I know that you can install grub from windows, I just don't know how.

---

### Post by bradlees on 2011-07-30
I don't see any bootloader when I install from windows. if I leave the blank hd set as the first drive in bios, nothing happens, it just keeps looping back to the emachines logo and restarting. 
 I downloaded grub on the xp drive, but I am too dense to figure out how to use and where to extract the .tar package it comes in. I also tried to install the wubi on the empty drive through xp and this resulted in an access denied, permission not granted or something to that effect.

Now I get this message:
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
can not mount /dev/loop 0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

Anything?

Thanks for responding.

---

### Post by Theredbaron1834 on 2011-07-30
Sorry, I don't know anything about wubi. At all, never used it.

There are only 2 things I could think of about grub. One is to reinstall ubuntu, and when it comes to the partition part, set up your disk, and then change the boot loader to be installed onto the main disk, ie windows disk. The only thing is that if this doesn't work, though I don't know why it wouldn't, it will stop windows from booting.

Second is to unhook the power from your windows drive, leaving only the drive you want ubuntu on. Then run a full install on that, turn off and reconnect. When your computer is booting pres esc to load the boot menu. and boot the second drive. 

That really is the only other thing I could think of.

---

### Post by Mark Phelps on 2011-07-30
If you have two physical drives, I've found the BEST solution is along the lines of what Theredbaron1834 already recommended ...

Have ONLY the Ubuntu drive connected when you do the install.  That will guarantee that GRUB is installed to the correct drive.

Then, reconnect the Windows drive -- but continue to boot from the Ubuntu drive. This is important!

Then, when into Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu and add an entry for Windows XP.

When you restart, you will see a selection menu that includes both Windows XP and Ubuntu.

---

### Post by bradlees on 2011-07-30
I have two physical drives, but I cannot get ubuntu period. I had formatted the drive and tried to install ubuntu and that's when these error messages started popping up. Since all else has failed, I copied an image of the other hd(the xp) onto the drive I planned to use solely for ubuntu. Now I think I am going to run the wubi and hopefully be able to do a full install after that.

---

### Post by Theredbaron1834 on 2011-07-30
Yeah, I don't know what else to do, with out being there. And I don't know wubi either. Got to hope someone else can help I guess.

---

### Post by cjcobb on 2011-07-31
I just had a similar problem with the NTLDR missing error. I had installed XP on a 2nd drive after using Ubuntu 10.04 on my primary. That's when the errors started...

I tried several solutions from the forum and google but nothing worked til I found the link below. Here's what I did: 

I rebooted to the 10.04 live CD and installed Boot-Repair using option #2 here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I ran boot-repair and it forced me to re-install GRUB2 (1.97 IIRC) on my primary. I then was able to re-boot into Ubuntu on my primary. So I ran sudo update-grub in the terminal, and now I can dual boot into both Ubuntu and Win XP.

Hope this helps you.

---

### Post by Mark Phelps on 2011-08-01
> **bradlees said:**
> I had formatted the drive and tried to install ubuntu and 

Sorry if this has been asked before ... but have you tried REMOVING all the partitions from a drive and THEN installing Ubuntu to the unformatted drive?

---

