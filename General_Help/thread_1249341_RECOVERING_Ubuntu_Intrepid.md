---
title: "RECOVERING Ubuntu Intrepid"
date: 2009-08-25
forum: General Help
---

### Post by davidds on 2009-08-25
I had some problems in the past with my Ubuntu Intrepid 8.10 installation. It started by refusing to mount NTFS partitions and strange errors. I fed up and deleted files under /bin and /boot (but the grub ones), working with and old, fast Ubuntu 7.04 boot disk. Now I want my Ubuntu 8.10 customized system to work again from my hard drive. I tried to copy the /bin and /boot files from the CD to the root partion, but when I try to load the oldest kernel image it just says "file not found".

I need to keep my system running. There are many customized things and data there. Any ideas in how to get it back to work? :(

---

### Post by jonnymccullagh on 2009-08-25
Have you also tried copying files back into the /boot directory ?

---

### Post by davidds on 2009-08-25
I am getting a bit desperate now. I have managed to make an external NTFS system work, and made  a backup of /home there, but both of the 2 internal NTFS partitions seem to have errors that need a chkdsk, so I will try again with the latest Hirens Boot CD. The last time I tried it, I think the ntfs tools put things worse, but perhaps I can manage to boot in xp mode and make a chkdsk from there. I cannot even install xp from scratch, since it hangs "looking for existing xp installations". Gparted tells the NTFS partitions

---

### Post by davidds on 2009-08-25
I tried to copy the files back to the boot directory, as I told you, and tried to boot from that oldest boot file, but the result is "file not found"

---

### Post by davidds on 2009-08-25
gparted tells the ntfs partitions are not readable. I just want to get my Ubuntu working againg and try to recover my xp  as well,but I guess it will be a hard job. Any help please?

---

### Post by davidds on 2009-08-25
Ok, enough is enough. I managed to make a backup of /home and had most of the NTFS data backed up in the external drive, that is now working. I will destroy everything and try to build it again from zero, both the xp and the Ubuntu system.

Thank you to those marvellous people who enjoy destroying things from others. They are called crackers, and I hope not to see them again in my desktop systems, will really low level of protection (just updated and ufw).

Hackers are NOT crackers: 
[http://db.glug-bom.org/lug-authors/philip/docs/hackers-not-crackers.html](http://db.glug-bom.org/lug-authors/philip/docs/hackers-not-crackers.html)

"hackers build things, crackers break them."

---

### Post by bobbob1016 on 2009-08-25
> **davidds said:**
> gparted tells the ntfs partitions are not readable. I just want to get my Ubuntu working againg and try to recover my xp  as well,but I guess it will be a hard job. Any help please?

First off, deleting files when you don't know exactly what they are used for is never a good idea.

Your best bet is to reinstall Intrepid over itself.  Is /home on the same partition as /?  You said you backed up /, if you simply install Intrepid over / and do not format, I'm 99% sure be able to keep your files and settings, the installer should say something like "You are installing me over an existing install, and I will have to delete the duplicate files".

The worst case is you'd have to copy your old /home (assuming you backed up) over the new /home.  Your /usr/bin (basically Program Files from Windows) should be fine too.

The reason it'd be easier to reinstall is because /bin is where the OS programs usually go, and the "kernel" (basically the brain, or software equivelent of the CPU) is usually kept in /boot.  When you install updates, settings get tweaked and changed to match each kernel.  Simply copying the old kernel back would be like putting a stock engine in a car that had a different engine in it.  It requires a lot of work removing the other parts, and getting everything hooked back up correctly.

NTFS works basically fine now, so long as you do "safely remove" and never just unplug it, and forcing the Windows to shutdown is the same as unplugging it.

EDIT:  Patience is a virtue.  If people don't respond in 20 minutes, it could be because they are typing a long response like I was.  Mark the thread as solved, if you feel it is solved.

---

### Post by davidds on 2009-08-25
Bob, I find yours a good advice. I will try to reinstall Ubuntu on top of itself. Anyway, I still have a problem with the NTFS partitions, that seem to be corrupted. I will try Hirens boot cd in xp mode for that. It is only the external USB NTFS partition that goes well.

Once again, thank you very much for your clear help. :-)

---

