---
title: "help with ext3grep"
date: 2009-11-09
forum: General Help
---

### Post by acerunner on 2009-11-09
i am trying to recover some deleted files from /dev/md4. After trying foremost and photorec with no results, i found ext3grep. However the man page for it isn't very clear.

I ran "ext3grep --dump-names /dev/md4", and I can see the directory which the deleted files were in.
Then I ran "ext3grep --restore-file *directory */dev/md4", where *directory *is the directory where the files were found in dump-names. However that didn't recover anything.

Am I using this correctly? If not, what are the correct steps to take to recover the files?

Also, ext3grep creates a directory "RESTORED_FILES" where recovered files are placed. Is it possible to change that to a different directory?

---

### Post by tonywhelan on 2009-11-13
I'm just now learning how to use this tool and hope I can undo the damage I did with a delete button earlier this morning. So I still have my Learner plates on at this stage.

But I can answer your second question; the RESTORED_FILES folder is created in the current directory. I want to create mine on a USB flash drive, which I plugged in. When I ran the 'mount' command in a terminal it told me the USB drive's mount point - for example, this drive was /media/54F0-BF20 so by typing the cd command with the drive mount point: 
```
tony@HERC:~$ cd /media/54B0-39BC
tony@HERC:/media/54B0-39BC$
```
my current directory became the USB drive and when I ran a test restore it wrote to that USB drive ok.

---

