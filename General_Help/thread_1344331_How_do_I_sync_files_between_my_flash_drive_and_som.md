---
title: "How do I sync files between my flash drive and some /home folders?"
date: 2009-12-02
forum: General Help
---

### Post by TheOnlyMrK on 2009-12-02
I have a 7.5GiB flash drive that I use to hold a copy of my Documents, Music, and Pictures folders but the entire time I did this on Windows and even now that I'm on Ubuntu I never had software to keep the files in sync automatically, so I ended up having to do it manually every month or so when I was bored enough to do it.
Now I'm wondering if their is a program that I can use that every time I plug in my flash drive it will synchronize the folders automatically for me so that way I know when I take my flash drive to a friends house it will have everything up to date?

---

### Post by Jive Turkey on 2009-12-02
I'm not sure if you can make it run automatically when you plug it in but you could use rsync.

It's a command line application so you could put it into a script and run it with all of the options etc that you want.

There is a gui frontend to it if you prefer called grsync.

---

### Post by TheOnlyMrK on 2009-12-02
> **Jive Turkey said:**
> I'm not sure if you can make it run automatically when you plug it in but you could use rsync.

It's a command line application so you could put it into a script and run it with all of the options etc that you want.

There is a gui frontend to it if you prefer called grsync.
Thanks, I'm trying out the Grsync now, it's not exactly what I'm looking for but it's definitely a lot better then trying to do it myself.

---

### Post by pawnrocket on 2009-12-02
You can also use Back In Time and set it to run after you get home, at what ever time you normally use your computer. I believe it is using rsync.

---

### Post by kjohri on 2009-12-02
Try Unison.

[http://www.softprayog.in/tutorials/synchronize-files-primer.shtml]("http://www.softprayog.in/tutorials/synchronize-files-primer.shtml")

---

### Post by Aearenda on 2009-12-02
I too would try Unison-gtk for that, except that it doesn't start automatically - but it does everything rsync would do, with a nice GUI and with conflict resolution. It's in the repos, you can install with Synaptic etc.

---

### Post by dcstar on 2009-12-02
> **Aearenda said:**
> I too would try Unison-gtk for that, except that it doesn't start automatically - but it does everything rsync would do, with a nice GUI and with conflict resolution. It's in the repos, you can install with Synaptic etc.

+3

The Unison help file says you can start it from the command line.

---

### Post by TheOnlyMrK on 2009-12-02
I tried Unison but it keeps giving me an error about file permissions (probably because the flash drive is FAT32) and I have yet to figure out how to fix it. I'd love to just format it to Ext2 but *sigh* I have Windows users as friends. Lol.

---

### Post by shaggy999 on 2009-12-03
Your error is caused by the fact that fat32 filesystems do not have the same permissions support as ext2/3 so the mounting program mounts it with owner=root and restrictive permissions. You can change this in fstab. I think you need to set umask/dmask/fmask and maybe uid/gid.

---

### Post by dcstar on 2009-12-03
> **TheOnlyMrK said:**
> I tried Unison but it keeps giving me an error about file permissions (probably because the flash drive is FAT32) and I have yet to figure out how to fix it. I'd love to just format it to Ext2 but *sigh* I have Windows users as friends. Lol.

Then format it as NTFS.

---

### Post by TheOnlyMrK on 2009-12-03
> **dcstar said:**
> Then format it as NTFS.
NTFS shortens the life of flash memory, plus uses more space then FAT, and isn't as widely compatible. I have yet to find an operating system that doesn't understand FAT32.

---

### Post by dcstar on 2009-12-03
> **TheOnlyMrK said:**
> NTFS shortens the life of flash memory, plus uses more space then FAT, and isn't as widely compatible. I have yet to find an operating system that doesn't understand FAT32.

Gimme a break, using a Journaling file system for just sharing files does little to shorten the life of SSDs because the writes are infrequent. It is only when they are used inappropriately in live systems that the issue becomes significant.

NTFS supports enough permissions to allow Linux applications to function correctly, ancient (crap) filesystems like FAT do not.

---

### Post by TheOnlyMrK on 2009-12-04
> **dcstar said:**
> Gimme a break, using a Journaling file system for just sharing files does little to shorten the life of SSDs because the writes are infrequent. It is only when they are used inappropriately in live systems that the issue becomes significant.

NTFS supports enough permissions to allow Linux applications to function correctly, ancient (crap) filesystems like FAT do not.
Okay... Then (2.) NTFS uses more space then FAT and (3.) NTFS isn't as widely accepted as FAT.
You may think the FAT file system is "crap" but I do not, it is simple, fast, well known, and gets the job done. Which to me a file system for a flash drive should have all of those qualities.

---

### Post by paxmark1 on 2010-01-08
in ~.unison  whatever.prf    add 

owner=false
perms=0

---

