---
title: "Boot problem &amp; testdisk"
date: 2010-06-20
forum: General Help
---

### Post by BadGene on 2010-06-20
Greetings. 
I have a Ubuntu - windows 7 dual boot (in two partitions of the same  HDD) desktop PC for a few months. I was learning terminal commands and,  although I don't think I made such a big mistake, but the fact is that  the a very strange thing happenned: "Preferences" and "Administration"  from System disapeared as it did also "Applications". After rebooting  the same it remained the same. No big deal, I thought, because I haven't  yet saved any important work on Ubuntu. So I reinstalled Ubuntu. Done  that everything was nice until I booted Windows... Since then I  counldn't start windows after GRUB due to:

Status: 0xc000000f
 Info: The boot selection failed because a required device is  inaccessible."

Windows Live DVD Repair is useless. I've tried CHKDSK utilities, no  result. Windows partition in Ubuntu's Disk Utility is OK but I can't  access the files (all "broken links"), just can explore a few  directories after which I find myself entering the same folder endlessly  (?!). 

I wanted to repair windows boot or at least recover some important files  in Documents and I thought I had backup (but turns out that, for some  reason that I'm still trying to understand, they aren't...).
 
In another thread here I was advised to use Testdisk. I've analysed the  disks, I tried to search for the files I wanted to copy as everyone says  they've but couldn't...

Any idea?

(here's the log file [http://dl.dropbox.com/u/788486/testdisk.log](http://dl.dropbox.com/u/788486/testdisk.log) if you wish to take a look of what I've done)

---

### Post by BadGene on 2010-06-21
Well guys, anyone have any ideia about this problem?
I'd really appreciate it...

---

### Post by oldfred on 2010-06-21
Testdisk repairs a lot of things, but maybe it is just a boot issue.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

