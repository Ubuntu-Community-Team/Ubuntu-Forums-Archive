---
title: "Messed up /etc/groups"
date: 2011-10-19
forum: General Help
---

### Post by Zxaos on 2011-10-19
Earlier today, I accidentally removed my only user account from admin, and was no longer able to sudo.

I booted into recovery mode, remounted the filesystem as read-write, and moved a backup copy of the groups file, /etc/group- back to being /etc/group.

Unfortunately, now when I am in a console and type 'groups', I get a huge listing of "cannot find the name for group ID XYZ". I've clearly caused this by messing with the groups file, but don't know how to fix it. Can someone point me in the right direction please?

---

### Post by matt_symes on 2011-10-19
Hi

> **Zxaos said:**
> Earlier today, I accidentally removed my only user account from admin, and was no longer able to sudo.

I booted into recovery mode, remounted the filesystem as read-write, and  moved a backup copy of the groups file, /etc/group- back to being  /etc/group.

It would have been easier to chroot into your file system from the  LiveCD and re-add the user that way or just add your user again from recovery mode. It's a shame you did not post  before.

Did you make a backup of the /etc/group file before the mv command ?

> 
Unfortunately, now when I am in a console and type 'groups', I get a  huge listing of "cannot find the name for group ID XYZ". I've clearly  caused this by messing with the groups file, but don't know how to fix  it. Can someone point me in the right direction please?Did you logout and log back in after changing /etc/group. i.e. I assume you are not still in the recovery console.

Can you return the entire output of (from a terminal)

```
id -G
```and

```
id -Gn
```Can you also post the output of

```
for i in $(id -G); do grep ":$i:" /etc/group; done
```Kind regards

---

### Post by Zxaos on 2011-10-20
Thanks for your help - I was able to solve it based on what you said. Running that last grep command showed me that I had incorrectly set the permissions on /etc/group to be readable only by root. I examined the permissions of another (working) linux machine, and changed the permissions to rw-r--r-- and rebooted to resolve the issue.

Thanks for pointing me in the right direction!:D

---

