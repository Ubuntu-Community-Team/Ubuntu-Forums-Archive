---
title: "Uninstall 11.04"
date: 2011-06-11
forum: General Help
---

### Post by cowboy7305 on 2011-06-11
I want to uninstall ubuntu 11.04 totally  from my hard drive  want to reinstall ubuntu 10.04 ,i have windows7 on drive as well dual boot i would like to make the windows partition smaller  so ubuntu 10.04 has more room ,is ther a way to do it with out having to reinstall windows

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **cowboy7305 said:**
> I want to uninstall ubuntu 11.04 totally  from my hard drive  want to reinstall ubuntu 10.04 ,i have windows7 on drive as well dual boot i would like to make the windows partition smaller  so ubuntu 10.04 has more room ,is ther a way to do it with out having to reinstall windows

  Boot from the installation disc of Ubuntu you want to install. Do a side-by-side installation. After it is done installing you can remove whatever other partitions you want with gparted. 

sudo gparted

---

### Post by nzjethro on 2011-06-11
Nice timing, I'm doing almost the same thing myself. Tried 11.04 for a few weeks but reverting back to Maverick. I also mucked around with a 7 install, but ended up backing up, wiping, and reinstalling Windows. ANd then, just for laughs I've installed the Oneiric alpha!

I'd suggest launching the live CD, booting Gparted, wiping 11.04, then installing 10.04 back. Then once that's done, look around for a non-destructive ntfs partition resizer (there are some out there, none off the top of my head, unsure if Gparted does it), to resize your Win partition, and then merge the freed up space with your Lucid partition.

Or alternatively find the resizer first, then boot to the live CD, use the resizer to resize your 7 partition, delete 11.04 partition, and claim all the free space for 10.04. This order would save having to boot the Live CD twice.

And as usual, make sure you back up first.

---

### Post by Mark Phelps on 2011-06-13
Do NOT, repeat NOT, use the Ubuntu installer to resize the Win7 partition space.  While it might work, it also might cause filesystem corruption and render Win7 unbootable.

When using Win7, it is better to use their Disk Management utility to resize the Win7 partitions.  Also, reboot into Win7 a couple of times after the resize to let the filesystem do its adjustments.

Also, BEFORE, you do an Win7 partition resizing, it would be a good idea to run the Backup feature to create and burn a Win7 Repair CD.  That could come in handly later if you need to restore the Win7 boot loader.

---

