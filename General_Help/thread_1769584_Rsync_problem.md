---
title: "Rsync problem"
date: 2011-05-28
forum: General Help
---

### Post by xtheunknown0 on 2011-05-28
Hello,

Here is a screenshot of my problem: [https://sites.google.com/site/xtheunknown0/linux-1](https://sites.google.com/site/xtheunknown0/linux-1)

Here is a snipping of the log:
*** Launching RSYNC command:
rsync -r -t -p -v --progress --delete -u --exclude uniit/2010lectures --delete-excluded uniit/2010lectures /cygdrive/c/Users/user/Documents/ /cygdrive/d/Documents/

sending incremental file list
rsync: change_dir "/cygdrive/c/Program Files/Grsync/bin/uniit" failed: No such file or directory (2)
rsync: opendir "/cygdrive/c/Users/user/Documents/My Music" failed: Permission denied (13)
rsync: opendir "/cygdrive/c/Users/user/Documents/My Pictures" failed: Permission denied (13)
rsync: opendir "/cygdrive/c/Users/user/Documents/My Videos" failed: Permission denied (13)
./
2010/
IO error encountered -- skipping file deletion
Fax/
Fax/Drafts/
Fax/Drafts/desktop.ini
          81 100%    0.00kB/s    0:00:00 (xfer#1, to-check=1043/1098)
Fax/Inbox/
Fax/Inbox/WelcomeFax.tif
       89534 100%   63.68kB/s    0:00:01 (xfer#2, to-check=1042/1098)
Fax/Inbox/desktop.ini
          81 100%   79.10kB/s    0:00:00 (xfer#3, to-check=1041/1098)
[snip]
Scanned Documents/
Scanned Documents/Welcome Scan.jpg
      516424 100%    1.23MB/s    0:00:00 (xfer#4, to-check=1040/1098)
Scanned Documents/desktop.ini
          81 100%    0.21kB/s    0:00:00 (xfer#5, to-check=1039/1098)
Scanned Documents/e3ln3.jpg
      522785 100%  958.98kB/s    0:00:00 (xfer#6, to-check=1038/1098)

[snip]
uniit/Queue of tutorial questions.docx
       11880 100%    0.00kB/s    0:00:00 (xfer#7, to-check=45/1795)
uniit/ln7networking.m4v
    13664256  31%  296.05kB/s    0:01:42

I just want to reach 100% for the top progress bar. Can you help me please?

---

### Post by xtheunknown0 on 2011-05-29
Bump

---

### Post by katykat on 2011-05-29
This looks like a Windoze problem. You are trying to back up from an NTFS drive where there are many things that can go wrong, especially with cygwin being half win, half Linux. 

Chmod everything in cygwin, and maybe i win try:
cacls *.* /C /T /E /P Everyone:F

Which will give full win permissions for those directories (do it in /Documents).

(There is also a GUI way to do it, but I never use it, so perhaps someone else can assist there).

---

### Post by xtheunknown0 on 2011-06-04
I'm not using Cygwin. I'm using the Grsync for Windows.

---

### Post by xtheunknown0 on 2011-06-14
> **xtheunknown0 said:**
> Hello,

Here is a screenshot of my problem: [https://sites.google.com/site/xtheunknown0/linux-1](https://sites.google.com/site/xtheunknown0/linux-1)

<snip>

There is no such problem with cwRsync.

---

