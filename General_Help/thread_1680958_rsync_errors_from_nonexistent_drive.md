---
title: "rsync errors from nonexistent drive?"
date: 2011-02-03
forum: General Help
---

### Post by noleks on 2011-02-03
Hi:
I am trying to backup my ~ directory to a portable drive.  In the meantime rsync is giving me all kinds of messages like this:

rm: cannot remove `/media/Portable2/documents and settings laptop/noleks/Desktop/lsi_eco_noleks.pdf': No such file or directory
rm: cannot remove `/media/Portable2/documents and settings laptop/noleks/Desktop/Syn. ptSI/lsi_eco.pdf': No such file or directory
rm: cannot remove `/media/Portable2/documents and settings laptop/noleks/Desktop/lsi_eco.pdf': No such file or directory
rm: cannot remove `/media/Portable2/documents and settings laptop/noleks/Desktop/LSI/askk_int/common/Technology/DB/gflxc_DB/internalbuffrs.pdf': No such file or directory

This drive is neither plugged into my computer nor is it involved with my backup script:

rsync $base_options -narv /home/noleks /media/Personal1/Linux_bak

I think the question is, does rsync have a queue somewhere of operations it did not complete?  If so is there a way to rest this?

It is possible something went awry with a previous sync on this drive but I cannot remember right now.

Either way why is it trying to complete that sync when I'm asking it to do something else?

I am using Ubuntu 10.04.

Thanks!

---

### Post by vanadium on 2011-02-03
What are your base_options? By default, rsync will not remove files.

---

### Post by noleks on 2011-02-03
Here they are:

$base_options = "--exclude=*.mp4 --exclude=*.wmv --exclude=*.flv --exclude=*.vob --exclude=*.avi --exclude=*.TiVo --exclude=*.iso --exclude=*.mpg --exclude=*.mpeg --delete-before --delete-excluded";

Again, this drive is not targeted in the rsync command, nor is it even plugged into the machine.

---

