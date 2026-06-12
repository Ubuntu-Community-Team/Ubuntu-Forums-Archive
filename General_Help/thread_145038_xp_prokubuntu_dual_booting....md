---
title: "xp pro/kubuntu dual booting..."
date: 2006-03-15
forum: General Help
---

### Post by questionasker on 2006-03-15
so i got a nice new HD, and partitioned it just right, with the larger half dedicated to Linux, of course. 
but, what i didnt pay attention to is that all the guides that deal with dual booting (or at least all the one sive found), are when you have windows installed first, then go back and install linux-
but i didnt do that. in my haste to get that brand new harddrive roarin', i installed kubuntu first. then xp pro. now i cant get back into kubuntu... :(

i saw something about booting with the install cd, going into resuce mode, and trying to install grub again, but that gave me some "/boot/grub/stage1 not read correctly"...

so now im stuck using xp for the moment...
anyone have any ideas? 
or am i just gonna have to re-install kubuntu, and follow one of those guides, since this time, i do already have xp installed...

---

### Post by ajgreeny on 2006-03-15
You will need to make sure that windows is on the primary partition of the disk, as windows insists on this, I believe.  If you have it on the secondary partition then I think you will have to start again, but do wait for more info from others who know about this in more detail before you go back to the beginning, as I may have misunderstood what I've read in other threads.  I think it is also worth putting grub on the floppy drive if you have one as that allows you to get into kubuntu whatever happens to your MBR.  You can always install it to hard drive after everything is proved OK.  Good luck, and I hope I'm wrong about the partition bit of this message.

---

### Post by nrwilk on 2006-03-15
The easiest way to solve your problem is to wipe the drive and install XP first, Linux second.  I hate to tell you that, but at least you've just installed, and you won't lose any data.

Good Luck!

---

### Post by carlos1 on 2006-03-15
Correct.
I have been through this several times with different hardware. 
If you don't already have things you have to save on the Windows partition, re-install both O/Ses starting with Windows.
On the Windows XP installer, just use the amount of space you need for the Windows partition, and leave the rest unformatted (don't format them even if you're going to leave them empty).
Then, when (if) if you do re-install Kubuntu, Grub will become the boot loader, enabling you to boot either O/S.

---

### Post by incubus on 2006-03-15
Remember, as pointed above, that you just have to start all over if windows is not in the beginning of the hard drive. Microsoft requires its OS to be in the first 10Gb, not necessarily the first partition (in my case it's the second).

If you comply to those rules, you just have to reinstall GRUB manually. Instead of going into details here, let's wait to see which one is your case.

incubus

---

