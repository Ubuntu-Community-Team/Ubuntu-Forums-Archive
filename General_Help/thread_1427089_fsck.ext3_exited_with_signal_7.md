---
title: "fsck.ext3 exited with signal 7"
date: 2010-03-11
forum: General Help
---

### Post by acrocephalus on 2010-03-11
Hello,
Yesterday my Ubuntu Jaunty 9.04 64 started a routine file system check on boot. At a certain point, it said that the /dev/sdb3 had some errors, opened a maintenance shell and suggested to carry out an fsck. I run
```
sudo fsck -y /dev/sdb3
```
Finally, it said that the fsck.ext3 exited with signal 7 because of an inconsistency (or something similar). What can I do to solve it? I don't think it is a HDD physical problem, as if I run a LiveCD I can mount the drives and check all the files. Just a last think (just in case it matters), I have the OS running from a USB HDD.
Cheers,

Dani

---

### Post by sisco311 on 2010-03-11
That's a weird exit code. :)

According to the man page, the exit code is the sum of the following conditions:
```


            0    - No errors
[B]            1    - File system errors corrected
            2    - File system errors corrected, system should
                   be rebooted
            4    - File system errors left uncorrected
[/B]            8    - Operational error
            16   - Usage or syntax error
            32   - E2fsck canceled by user request
            128  - Shared library error

```
(7=1+2+4)

Try to run e2fsck without the -y option and in verbose mode:
```
sudo e2fsck -C0 -f -v /dev/sdb3
```
it's a 0 (zero) after the -C option, **NOT** an uppercase o.

---

### Post by rnerwein on 2010-03-11
hi
the guy wrote: exit with "**signal 7"** may be the fsck got a SIGBUS !?
**** can happen.
ciao
oh - exit code 7 even can mean: Argument list too long - this fits to sigbus ( i know that sigbus is different ).
got a SIGBUS long, long ago on a sparc solaris - there was a monster path name on the partition.

---

### Post by Cristina Amazonas on 2012-06-11
i've got the same signal 7 message ...
any hints to fix it ?

---

### Post by nothingspecial on 2012-06-11
Rather than bumping a very old thread to the top, please start a new one.

Thanks :)

---

