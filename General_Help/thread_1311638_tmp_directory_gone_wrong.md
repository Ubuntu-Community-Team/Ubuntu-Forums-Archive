---
title: "tmp directory gone wrong"
date: 2009-11-02
forum: General Help
---

### Post by TristanSt on 2009-11-02
I seem to have a problem with my tmp directory that is preventing me from booting into Intrepid.

It seems that the tmp directory has become unusable somehow. An ls  -l / shows:

total 256
drwxr-xr-x   2 root root 4096 2009-07-19 17:09 bin
drwxr-xr-x   4 root root 4096 2009-10-28 17:09 boot
...
...
drwxr-xr-x   2 root root 4096 2008-10-14 13:02 sys
d?????????   ? ?    ?       ?                ? tmp
drwxr-xr-x  12 root root 4096 2008-12-05 18:13 usr
...

This tmp directory seems impossible to do anything with:

$ cd tmp
cd: no such file or directory: tmp
$ rm tmp
rm: cannot remove 'tmp': No such file or directory
$ rmdir tmp
rmdir: cannot remove 'tmp': No such file or directory
$ mkdir tmp
mkdir: cannot create directory 'tmp': No such file or directory
$ touch tmp
touch: cannot touch 'tmp': No such file or directory

Note: the above commands were run using a SystemRescueCD. If I do it using the ubuntu console I get errors along the lines of stale NFS handle.

Which leaves me with a massive problem because I can't boot into ubuntu because X wont start.

HELP!!

I should note that it's an ext3 partition.

---

### Post by dcstar on 2009-11-02
> **TristanSt said:**
> I seem to have a problem with my tmp directory that is preventing me from booting into Intrepid.

It seems that the tmp directory has become unusable somehow. 
..........
Note: the above commands were run using a SystemRescueCD. If I do it using the ubuntu console I get errors along the lines of stale NFS handle.

Which leaves me with a massive problem because I can't boot into ubuntu because X wont start.

HELP!!

I should note that it's an ext3 partition.

fsck the partition using the rescue disk/live CD.

---

### Post by pastalavista on 2009-11-02
> **TristanSt said:**
> I seem to have a problem with my tmp directory that is preventing me from booting into Intrepid.

It seems that the tmp directory has become unusable somehow. An ls  -l / shows:

total 256
drwxr-xr-x   2 root root 4096 2009-07-19 17:09 bin
drwxr-xr-x   4 root root 4096 2009-10-28 17:09 boot
...
...
drwxr-xr-x   2 root root 4096 2008-10-14 13:02 sys
d?????????   ? ?    ?       ?                ? tmp
drwxr-xr-x  12 root root 4096 2008-12-05 18:13 usr
...

This tmp directory seems impossible to do anything with:

$ cd tmp
cd: no such file or directory: tmp
$ rm tmp
rm: cannot remove 'tmp': No such file or directory
$ rmdir tmp
rmdir: cannot remove 'tmp': No such file or directory
$ mkdir tmp
mkdir: cannot create directory 'tmp': No such file or directory
$ touch tmp
touch: cannot touch 'tmp': No such file or directory

Note: the above commands were run using a SystemRescueCD. If I do it using the ubuntu console I get errors along the lines of stale NFS handle.

Which leaves me with a massive problem because I can't boot into ubuntu because X wont start.

HELP!!

I should note that it's an ext3 partition.

The tmp directory is actually designated /tmp. Without the / it isn't even a directory. Try your commands with '/tmp' instead of just 'tmp'.

---

### Post by TristanSt on 2009-11-03
fsck from the recovery image worked, various stuff wrong, consistent with an unclean shutdown. Oddly, I couldn't get fsck working by hand (fsck -v /dev/sda6), but using the pre-canned option from the recovery image worked fine.

tmp got recreated, although oddly only with 744 permissions - this caused me to be unable to log into X, but chmod 1777 sorted.

Thanks for the help.

Now just need to work out if I can convince OpenOffice to recover an autobackup of my corrupt calc workbook...

---

