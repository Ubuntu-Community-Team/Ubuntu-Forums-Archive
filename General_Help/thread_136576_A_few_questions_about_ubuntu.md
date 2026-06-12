---
title: "A few questions about ubuntu"
date: 2006-02-26
forum: General Help
---

### Post by PowerJC on 2006-02-26
I am thinking about dual boting ubuntu/kubuntu with xp.  I'm going to use parttition magic to resize my windows partition.  Then install ubuntu in the free space.  I was going to boot grub on floppy will this leave the mbr alone.  I have a radeon x800gt and to boot the live cd i have to put it in expert mode to get the vesa driver will i have to put the install in expert mode?  And is using partition magic safe?  Will all this work ok?  And i'm going to install my bt voyager and use it to connect as shown here [http://www.ubuntuforums.org/showthread.php?t=132171&highlight=bt+voyager](http://www.ubuntuforums.org/showthread.php?t=132171&highlight=bt+voyager) should this work ok?  I also have a dual core processor does ubuntu/kubuntu support them?
Also is this all the same for kubuntu?
Thanks for your help.

---

### Post by gumbald on 2006-02-26
Only thing I'll say is I've had bad experiences with Partition Magic, I prefer to use Acronis Partition Expert these days. No need to leave the MBR alone imho, it can easily be restored using a Windows CD if required (using Recovery Console: fixmbr).

---

### Post by PowerJC on 2006-02-26
Does anyone know about using the x800gt?  Do i have to put the install in expert mode to force it into vesa?  Because I might install ubuntu in a few hours and need to know

---

### Post by timetunnel on 2006-02-26
I had a really bad experience with Partition Magic once (version 4, I think). It messed up my whole harddisc and instead  of a nice resize of my partitions, nothing worked anymore. The only thing that helped was a low-level format of the disc. No idea why that happened, but I've never tried Partition Magic again after that. One thing I learned from this incident: **always** make an image of your disc before playing round with partitions.

Oh, yes, another thing was that when I had my first dual boot (Suse / Windows) set up and wanted to change partition sizes afterwards, PM destroyed the boot sector: I started Partition Magic in Windows, it said "have to reboot to apply changes", it then wrote it's own MBR and that was it. Gone. 

HTH
Jens

---

### Post by aysiu on 2006-02-26
No need for Partition Magic.
No need to leave the MBR alone (just make sure you have a Windows CD around so you can do a fixmbr if you ever want to delete Ubuntu).
This dual boot guide will walk you through everything in the process:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by sas13 on 2006-02-26
I've actually had good experiences with Partition Magic 8.

used it several times to resize NTFS partitions and then install linux after XP on the disk with good results. IIRC you need to make sure you actually use PM 8.02 or something, which you get by applying a patch to PM 8 )

And using a floppy can be a good idea sometimes too - true, the MBR can usually be wiped clean with a windows boot disk, but sometimes it's not that straightforward.

having the MBR on a floppy has other advantages too - if you have multiple OS's on your computer you can use a different floppy for each, and determine which OS will be loaded by which floppy is in the drive when you restart (usefull if you share the comp. with non linux users). Also some installers have not-so-great detection of what other OS are on the computer, which means you'll have to go back and edit your bootloader manually.

and you can always use floppies till you have your system set up the way you want, and then move the MBR onto your HD

---

### Post by Ramses de Norre on 2006-02-26
About the ati card: you can run normal install, but you have to go directly to a text-only environment when it's finished (alt+ctrl+F1) and change the driver to vesa so X will work. Then configure you internet and download the fglrx driver (I can't remember the actual package name, just type it in google) and change vesa to fglrx.
That's what I did and it works perfect:)

---

### Post by aysiu on 2006-02-26
[QUOTE=sas13]
having the MBR on a floppy has other advantages too - if you have multiple OS's on your computer you can use a different floppy for each, and determine which OS will be loaded by which floppy is in the drive when you restart (usefull if you share the comp. with non linux users).[/QUOTE] Ubuntu is pretty darn good at detecting Windows and adding it to the Grub menu. It may not add other Linux OSes properly, but once they're added, it's a lot easier to choose which OS to boot up (press the up and down arrows) than inserting and removing a floppy.

---

### Post by PowerJC on 2006-02-26
I'm using paragon partition manager 2005 is it ok?  And how do you switch it to vesa mode?

---

### Post by ronmarley1 on 2006-02-26
For what it's worth, I used Partition Magic 7 to set up my hard drive to load Ubuntu.  I loaded Ubuntu and everything worked fine.  However, when I boot into Winblows and try to run Partition Magic, I get an error and it closes out.  Everything works fine on Ubuntu and Winblows, but I can no longer use Partition Magic.  I reinstalled PM and I still get errors.  The error tells me that it can't read the drive letter, Error 115 or something like that. 
PS, I'm not looking for a solution here, just sharing what happened.

---

### Post by Ramses de Norre on 2006-02-26
To change your driver: 
in a shell do ```
cd /etc/X11
sudo cp xorg.conf xorg.conf.bak
sudo vi xorg.conf
```

Then search for the device section with something that makes you think of your graphics card at the identifier line. At the driver line press i to get into insert mode and change "ati" to "vesa".
Then press ESC and shift+q to get a command line below and type wq! there.
then alt+ctrl+F7 to get back into X and press alt+ctrl+backspace to restart it.

---

