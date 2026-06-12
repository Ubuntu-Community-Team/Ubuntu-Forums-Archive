---
title: "Mint Kernel Panic"
date: 2010-01-07
forum: General Help
---

### Post by kindledwind on 2010-01-07
My computer developed a new trick tonight. 4 times in the last 2 hours it's booted & ran fine...for about 30 minutes or so. Then some apps become unstable & crash, and some don't notice anything wrong. Firefox keeps running fine, but if I have a nautilus window open, the next time you click anywhere, it crashes. 

So, try to restart the machine & it comes back with the "kernel panic -not syncing vfs unable to mount root FS on unknown block" message. The first time I restarted it, I managed to get to a root terminal & fsck the drive. It found 2 errors that it fixed, supposedly. The next collection of restarts, it would just go through bios, then grub, then hang on the error.

So, power down the machine first & then boot it....magically, I'm back to the desktop again for another 30-45 minutes. Anyone have any idea what's going on? It's been fine since the day mint was released...and the only system change was plugging my 2nd monitor back in 3 days ago. Why would it go kukoo in the last 2 hours?

The machine is a quad core intel with 4 gigs of ram, Asus mobo and a 250gig sata drive for the system drive.

Any advice other than 'nuke it, start over'?

Todd

---

### Post by sanderd17 on 2010-01-07
You think nautilus is the problem, maybe you could try using konqueror instead. To get completely rid of nautilus you'll have to install the KDE window manager. and log in to KDE instead of gnome. Or use XFCE instead of gnome, see if it works with one of these. If it works you can try searching the package you need to get rid of.

---

### Post by kindledwind on 2010-01-07
I should have been more clear. I don't think nautilus is the problem, because I can get a terminal window to crash too...or xchat/gedit/brasero you name it. Firefox just happens to be immune to whatever state it manages to go into after running 30 mins.

Anyway, I really think there's something funky like mint is losing contact with the filesystem after so long...but I can't explain why it's comes back to life only on a power-up & not on a reboot. Don't quite get it.

---

