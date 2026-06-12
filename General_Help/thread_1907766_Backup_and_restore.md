---
title: "Backup and restore"
date: 2012-01-12
forum: General Help
---

### Post by MidnightbluRose on 2012-01-12
Hello,

I'm looking to move my Ubuntu installation from my laptop to a custom build desktop.  

Is there a good program that will let me backup my ubuntu installation on my laptop and restore it on a blank harddrive?  So that I don't have to do a start from scratch.

---

### Post by ptsubin on 2012-01-12
There are a lot of them. If you have a big enough portable hard disk and time dd command can do the work.

---

### Post by fisch246 on 2012-01-12
Depends on what you're looking for. Do you want GUI, or CLI? Do you have plenty of space?

---

### Post by MidnightbluRose on 2012-01-12
> **fisch246 said:**
> Depends on what you're looking for. Do you want GUI, or CLI? Do you have plenty of space?

GUI preferred, but I wouldn't be against CLI if there was a good guide.

Yeah, my laptop was split between W7 and Ubuntu.  My Ubuntu partition is only 70GB.

---

### Post by tea for one on 2012-01-12
> **MidnightbluRose said:**
> GUI preferred, but I wouldn't be against CLI if there was a good guide.

Yeah, my laptop was split between W7 and Ubuntu.  My Ubuntu partition is only 70GB.

I use Remastersys to make a live cd/dvd/usb of the OS including all additional software. This new live OS will include the Ubuntu install utility.

I then use Grsync to back up and restore data.

Good luck with the move.

---

### Post by Lars Noodén on 2012-01-12
I assume you already have the data covered by backups. 

For the system files, you can get a listing of all the packages using dpkg.
```

dpkg --get-selections > packages.txt

```

Then once you have another machine with a bare bones setup you can restore them.

```

sudo dpkg --set-selections < packages.txt
sudo apt-get dselect-upgrade

```

The smallest installation comes from the Alternate install CD, and takes only a few minutes.  At the startup screen it is F4->Install a command-line system.  Then once you can log in do the restore.

---

### Post by MidnightbluRose on 2012-01-12
Thanks for the replies!

---

