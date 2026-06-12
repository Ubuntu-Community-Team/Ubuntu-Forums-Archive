---
title: "Computer Maintenance"
date: 2010-01-03
forum: General Help
---

### Post by Silvertones on 2010-01-03
I'm so used to Windows having to run multiple malware scans with multiple tools. Running registry cleaners and running CCleaner to remove all of the old temp files, cookies etc.. Derfagging

Ok with Ubuntu no more malware scans. No more registry scans.
It appears that there isn't a defrag tool?
And what about the other things that tend to clog up the works, Temp files , cookies etc.
Is that what the disc janitor is all about?
Thanks

---

### Post by chewearn on 2010-01-03
Unless you run Ubuntu constantly with low disk space, the ext filesystem will never need to be defragged.  One of the "perks" is that the system never clogged up and get slower as months or years go by.  I have the same Intrepid install since Oct 2008; it's as snappy as the first day I installed it.

Temp files are created in /tmp, but are deleted on every reboot.

Cookies, well you could periodically clear it thru the browser itself.  Myself, I ran Firefox to delete everything on close, so it's never a problem.

Janitor is a good app to clear everything else, but you have to be careful not to delete things that might be needed as well (I'm not sure about the recent incarnation of the Janitor, but the version I have in Intrepid is not very selective about the things it wanted to delete).  But it's the simplest method to clear old kernels.

Probably most effective in regaining some disk space is clearing up archived packages, and unused dependencies; i.e. occasionally run:

```

sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean

```

---

### Post by Soul-Sing on 2010-01-03
indeed no register on linux.
there were experiments with defragmentation of ext2/3, but with
no real success, and therefore no implementation.
(i am not known/fam. with defrag experiments with ext4)
to clean your browser: cookies, etc etc. is more or less the same as on windows computers.
you can clean your linux system: "orphaned" packages, clean -apt, etc.

---

### Post by northrup on 2010-01-03
Ext3 and ext4 both have anti-fragmentation preventative measures in the way they operate.  Supposedly, there will *eventually* be a defragmentation tool for ext4, since realistically, files will still be fragmented.  Ext3 doesn't have any truly effective defragmentation program.  The ones that exist require the volume to be basically empty.

---

### Post by Silvertones on 2010-01-03
What am I gonna do now? Most of my day was spent keeping Windoze running right!:lolflag:

Oh maybe I'll spend more time putting songs together for my show. :guitar:


Thanks!

---

### Post by freeediver on 2010-04-11
Cookies, well you could periodically clear it thru the browser itself. Myself, I ran Firefox to delete everything on close, so it's never a problem.

How do you set Firefox to delete everything on close?

Thanks

---

### Post by mpjbrennan on 2010-04-11
Edit > Preferences > Privacy 

On History drop-down select "Use custom settings for history"

The display will change giving you the option to "Clear history when Firefox closes"

If you click the "Settings" button adjacent you can choose which elements of history you want to clear.

Patrick

---

