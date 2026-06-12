---
title: "Please help me get rid of Windows!"
date: 2011-04-29
forum: General Help
---

### Post by pyromaniac77 on 2011-04-29
Okay, I really hate Windows.
Why isn't really relevant, but I need some help.
So, here's the deal:  I had Windows 7 for about a year, and I got Ubuntu a couple months ago.  Being the fool I was, I didn't give it near enough space, nor did I give it its own partition.  I'm not that educated in this sort of thing, but I can provide any extra info you guys need, so please help me out.
Thanks!

---

### Post by cymbaline42 on 2011-04-29
Please provide more information.  What do you want to do exactly?  Remove Windows completely and install Ubuntu?  Or do you want to install it side-by-side?

---

### Post by 3Miro on 2011-04-29
Did you use Wubi, it seems like it (this is the only way you can install Ubuntu without its own partition).

If you have installed Ubuntu via Wubi and you want to remove windows, complete reinstall of everything is your only option. Backup everything important from both windows and Ubuntu, then boot from a LiveCD and install Ubuntu on your entire HDD.

NOTE: Whatever you do BACKUP EVERYTHING IMPORTANT, messing with partitions and reinstalling OS can destroy all of your files.

---

### Post by pyromaniac77 on 2011-04-29
So I just have to back everything up and then delete everything else, and then reinstall ubuntu?

---

### Post by bcbc on 2011-04-29
Here's another option:
[How to migrate wubi]("http://ubuntuforums.org/showthread.php?t=1519354")

---

### Post by 3Miro on 2011-04-30
> **pyromaniac77 said:**
> So I just have to back everything up and then delete everything else, and then reinstall ubuntu?

When Ubuntu installs, if you tell it to use the entire disk, it will delete everything. You only have to backup.

If you use the other method (which is more involved), then also make sure to backup, since doing something wrong may still destroy your files.

---

### Post by pyromaniac77 on 2011-05-02
Okay, so which of the following folders do I need to back up and which ones will replace themselves:

bin, boot, cdrom, dev, etc, home, host, lib, lib32, lib64, lost+found, media, mnt, opt, proc, root, sbin, selinux, srv, sys, tmp, usr, var

And also these files:

initrd.img, initrd.img.old, vmlinuz, vmlinuz.old

---

### Post by kaspar_silas on 2011-05-09
Naturally Your whole drive will be wiped if you install on the entire drive which is the easiest method by far.

So you need to plugin in an external drive or usb stick and copy all user files (probably in home)  that are important to you. NOTE: only files that are on the external drive will survive the reinstall. Once you are sure that all files important to you are on the external drive then unplug the external  drive and install the new Ubuntu on the main hard drive.

All the system files files and programs will be replaced in the new install so dont worry about them its only personal files you need to copy. In the unlikely event you have non-ubuntu conmerical programs you'll have to install those again after. Check with the vendor if you don't have installation media for these.

Once your new Ubuntu is installed, use synaptic is install any programs you are missing. Then plugin the external drive and copy back across your files.

---

### Post by wilee-nilee on 2011-05-09
Here is a thread on moving the wubi to a partition. The OP hasn't responded for a week, but this is a thread we all should know about if we are to help.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by Telengard C64 on 2011-05-09
> **3Miro said:**
> NOTE: Whatever you do BACKUP EVERYTHING IMPORTANT, messing with partitions and reinstalling OS can destroy all of your files.

And please bear in mind that by definition the word *backup* means that you end up with [more than one copy](http://blog.wisefaq.com/2010/01/05/backups-with-the-3-2-1-rule/).

---

### Post by jerome1232 on 2011-05-09
I always get nervous when helping in a thread like this and the OP disappears, I always wonder if they accidentally nuked everything and just have an overlarge paper weight on their desk now....

---

### Post by kaspar_silas on 2011-05-10
Na, if they nuked everything they would be straight back via another or a friends computer. Probably writing angrily in capitals :) 

I'd imagine this silence implies success.

That nod to the moving wubi thread was very interesting, never tried that before.

---

