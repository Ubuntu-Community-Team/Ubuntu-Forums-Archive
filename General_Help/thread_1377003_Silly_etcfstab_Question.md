---
title: "Silly /etc/fstab Question?"
date: 2010-01-09
forum: General Help
---

### Post by moore.bryan on 2010-01-09
According to a couple of different places, it's not possible for me to put a line in /etc/fstab to mount one of my partitions with owner and group not root; instead, I have to mount it in /etc/fstab, then chown & chgrp to my user.

That seems ridiculously tedious and silly... is it true? I'm sure a short script could be written to get around it, but it seems obtuse for Linux not to allow that to be set in /etc/fstab.

Help?

---

### Post by michy99 on 2010-01-09
Once you set the permissions on your mount point, they should not change. If you are mounting a FAT or NTFS partition, the permissions are set in the fstab line. You should not have to change them every time.

---

### Post by moore.bryan on 2010-01-10
I guess I should have been more specific as to my partition setup... I'm dual-booting Ubuntu Netbook Remix 9.10 and Fedora 12. Based on a lot of advice, I've set it up this way: one partition for each root and home (four total) and a larger, separate partition for "shared" files; all partitions are formatted ext4. I'm trying to mount *that* partition via /etc/fstab with rw permissions for whichever user is logged-in. For example, if my username was "one," I want the shared partition to mount with one's ownership. 

This *seems* like it should be ridiculously simple, but--for some reason--I can't get it to do it. Add to that, it seems by the mount man and other threads/posts it isn't possible on ext4. Really?

---

### Post by bodhi.zazen on 2010-01-10
Perhaps it would help if you were to describe what the problem you are having, teh line in fstab is trivial. Error message ? Permissions ?

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

My guess is permissions as the system recognizes users by ID number and not name.

If Fedora users start with 500, while in Ubuntu they start with 1000.

With eiter system the line in fstab is very straight forward

/dev/sdxy /mount/point ext4 users 0 2

with the partition mounted, simply, as root, run

chown user:group /mount/point
chmod 777 /mount/point

You will need to tweak permissions or use lax permissions on files in the partition to share them.

---

### Post by michy99 on 2010-01-10
If the Group ownership of the mountpoint is set to 'users', then any user should be able to use it with no problem, reguardless of who the "owner" is.

---

### Post by bodhi.zazen on 2010-01-10
> **michy99 said:**
> If the Group ownership of the mountpoint is set to 'users', then any user should be able to use it with no problem, reguardless of who the "owner" is.

Not exactly true. It depends on the gid of the "users" group. If the group id is 500 in Feodra and 1000 it will not work the way you suggest.

---

### Post by moore.bryan on 2010-01-10
bodhi.zazen, I think you nailed my issue. My fstab line
```
/dev/sda9 /Storage ext4 rw,users 0 2
```
won't make me the owner of the directory, so I can't write to it as a "regular" user. From your post, you make it sound as though I'm going to have to write a script, to be called on startup, to reset the ownership on the files. Two things there: (1) isn't that a *ridiculously* convoluted way of mounting things and (2) doesn't that raise a security issue, since chown and chgrp must both be "sudo-ed?"

Thanks for all the help so far!

---

### Post by bodhi.zazen on 2010-01-10
Show the owner by uid rather then name

```
ls -nA 
```

Sharing directories across users is a bit convoluted, and people wither SGID or use scl.

IMO the easiest thing to do is to make change the users gid in both Fedora and Ubuntu to be the same. Otherwise, yes you have to relax your permissions on the shared partition (make it world read/writable).

---

### Post by moore.bryan on 2010-01-11
So, bodhi.zazen, if I understand you correctly, it's your opinion to mount the partition (/dev/sda9) with the "users" option in /etc/fstab and *change* my uid/gid in Fedora12 to match UNR 9.10's or vice-versa?

A problem still arises that whenever I mount via /etc/fstab, including with "users" as an option for my partition, I can't read-write to that partition.

Huh?

---

### Post by bodhi.zazen on 2010-01-11
> **moore.bryan said:**
> So, bodhi.zazen, if I understand you correctly, it's your opinion to mount the partition (/dev/sda9) with the "users" option in /etc/fstab and *change* my uid/gid in Fedora12 to match UNR 9.10's or vice-versa?

A problem still arises that whenever I mount via /etc/fstab, including with "users" as an option for my partition, I can't read-write to that partition.

Huh?

Yes, if that is not working, can you post the relevant lines in /etc/fstab and the output of 

ls -l / | grep Storage

ls -l /Storage

---

### Post by J V on 2010-01-11
hows this for an idea, make the HD itsself 000, but make everything under it 777, then put permissions on the *symlinks*, shoulden't this make it work?

---

