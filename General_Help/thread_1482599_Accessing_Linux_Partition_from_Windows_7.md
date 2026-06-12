---
title: "Accessing Linux Partition from Windows 7"
date: 2010-05-13
forum: General Help
---

### Post by IQAndreas on 2010-05-13
[SIZE="1"]Yes, I know, this has probably been answered a hundred times before, and I did do a Google search, but it's not really what I'm looking for...[/SIZE]

I dual boot Ubuntu 10.4 and Windows 7 (actually, just installed the Win7 a few hours ago. :)


I like that I can access the Windows 7 partition from Ubuntu, but not the other way around. I found links for several file explorers, but **is there any way to install an extension for the standard Windows Explorer that can open EXT3 partitions** (and the files therein) as if they were NTFS?

Most of the links I found refer to custom file explorers. I only want to use one file explorer, not switch between two different ones depending on which partition I want to open. :P Also, if I use a custom file explorer, how will dialogs like "Save as..." be able to handle saving directly to EXT3?

---

### Post by philcamlin on 2010-05-13
you could try 

[http://www.fs-driver.org/](http://www.fs-driver.org/)
ive never used it but its worth a shot. :popcorn:

---

### Post by Mark Phelps on 2010-05-14
That driver will almost certainly NOT work.  It works with Ext2 filesystems and with Ext3 as well.  I don't believe it will work with Ext4 filesystems -- the default for Ubuntu 10.04.

---

### Post by Skid420 on 2010-06-20
im have the same problem with my pc (exact same actually :P)
i have tried a few different programs but none of them seem to work.
the furthest ive got was with the program 'Ext2Fsd', it opened the partition even showed the folders but showed every folder as empty
i hope someone has a solution

---

### Post by jerome1232 on 2010-06-20
You can't access ext4 from Windows. The best option is to store your data on the windows drive, that way it's accessible to both os's.

---

### Post by Mark Phelps on 2010-06-20
> **Skid420 said:**
> im have the same problem with my pc (exact same actually :P)
i have tried a few different programs but none of them seem to work.
the furthest ive got was with the program 'Ext2Fsd', it opened the partition even showed the folders but showed every folder as empty
i hope someone has a solution

What part of my response was unclear -- the driver doesn't work with Ext4 filesystems.

---

### Post by GhostCard on 2010-10-29
You can use Ext2Read to save files from the Ubuntu side.[http://sourceforge.net/projects/ext2read/]("http://sourceforge.net/projects/ext2read/")
Don't get turned off by the name is does work with Ext4, although there is a catch, you can only save the files to the windows side. No add, cut, copy, paste, delete, or rename.

---

