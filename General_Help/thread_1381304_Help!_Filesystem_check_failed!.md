---
title: "Help! Filesystem check failed!"
date: 2010-01-14
forum: General Help
---

### Post by hamstermoon on 2010-01-14
I have had Karmic running since October with no bother, and today it started checking files at the black screen with the Ubuntu logo. Now its opened a maintenance shell. What do I do next??

---

### Post by llama320 on 2010-01-14
Try looking at/sending over the output of dmesg. That's generally the first place to look. You might also look at /var/log/Xorg.0.log

---

### Post by hamstermoon on 2010-01-14
> **llama320 said:**
> Try looking at/sending over the output of dmesg. That's generally the first place to look. You might also look at /var/log/Xorg.0.log

Umm - what is that in simple non-geekspeak terms? I am very much a newbie here  :oops:  ](*,)

---

### Post by vishnumrao on 2010-01-14
Check out this thread: Looks like same problem as you@

[http://ubuntuforums.org/showthread.php?t=1379239&highlight=Filesystem+check+failed](http://ubuntuforums.org/showthread.php?t=1379239&highlight=Filesystem+check+failed)

Vishnu

---

### Post by llama320 on 2010-01-14
No worries -- so you've got a shell open. Just type
```
dmesg |less
```
To get some useful output. Go to the bottom (press END) and start reading from the bottom up. Look for anything that looks obviously out of place (something FAILED, or the like). Rereading your first post, it probably doesn't have anything to do with Xorg, so don't worry about that part. 

If dmesg doesn't turn up anything useful, there's probably a hard-drive check in your BIOS, so you can try running that and see what happens.

If you updated the kernel recently (as in the last time you had the computer working) you should try choosing a different kernel version from GRUB

---

### Post by hamstermoon on 2010-01-14
> **vishnumrao said:**
> Check out this thread: Looks like same problem as you@

[http://ubuntuforums.org/showthread.php?t=1379239&highlight=Filesystem+check+failed](http://ubuntuforums.org/showthread.php?t=1379239&highlight=Filesystem+check+failed)

Vishnu
Brilliant. That seems to have allowed me to fix something and get back in. It said something about Orphan files or something and cleaned them up for me.

---

### Post by realGaurab on 2010-01-15
I tried fsck and it didn't work. So I rebooted, selected to boot with header 2.6.31.17 instead of 18. Fsck didn't resolve the problem. So rebooted with 17, ran sudo aptitude autoclean. Now boot with 17 went fine but still have the same problem with 18.

---

### Post by vishnumrao on 2010-01-15
> **realGaurab said:**
> I tried fsck and it didn't work. So I rebooted, selected to boot with header 2.6.31.17 instead of 18. Fsck didn't resolve the problem. So rebooted with 17, ran sudo aptitude autoclean. Now boot with 17 went fine but still have the same problem with 18.

Your problem does not seem to be the same as hamstermoon, as you are able to boot into atleast one kernel (2.6.31.17). 

Or did you mean to say you were never able to boot into any kernel and after fsck you were able to boot into 2.6.31.17?

Do you get the filesystem checked failed message when you boot into 2.6.31.18? and does it happen during a filesystem check? 

My moms computer running karmic too failed for the filesystem check failed error. She is yet to try fsck. Will update this thread soon!

Vishnu.

---

