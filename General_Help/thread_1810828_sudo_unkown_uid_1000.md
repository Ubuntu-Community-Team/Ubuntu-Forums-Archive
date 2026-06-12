---
title: "sudo: unkown uid: 1000?"
date: 2011-07-23
forum: General Help
---

### Post by boy18nj on 2011-07-23
I deleted /etc/passwd.lock and /etc/gshadow.lock.

Now when I run normal command installation, I receive this following error-

rocky@ubuntu:~/Downloads/Modified Oracle$ sudo apt-get install bc
**sudo: unknown uid: 1000**
rocky@ubuntu:~/Downloads/Modified Oracle$ 


I'm unable to use sudo, please let me know what did I messed up. And how I correct this mistake?

Why unknown uid:1000 is coming?

---

### Post by boy18nj on 2011-07-23
Even when I looked under Users and Groups, I do not even see my own user id.



[IMG]http://ubuntuforums.org/home/rocky/Desktop/User%20lost%20under%20Users%20And%20Groups.png[/IMG]

---

### Post by papibe on 2011-07-23
10000 is usually your UID. I have a few guesses:
[LIST]
[*]You let yourself out of sudoers.
[*]Your user is no longer on /etc/passwd (or/and shadow).
[*]Root is no longer on /etc/passwd (or/and shadow).
[/LIST]
All of them very difficult to solve. I would first try to correct them on recovery mode, and if that doesn't work... you are left with the LiveCD option.

Regards.

---

### Post by boy18nj on 2011-07-23
Since I installed ubuntu thru windows. How would I boot ubuntu from live usb?

---

### Post by papibe on 2011-07-23
Wubi install?

---

### Post by boy18nj on 2011-07-23
yes, its wubi install. I can boot from live usb.

I am thinking of mounting the root.disk file and inside that replace passwd with file from backup file.

But the problem is, I am unable to mount existing root.disk. I tried following options mentioned on this forum-

[http://nixcraft.com/ubuntu-debian/15295-ubuntu-mount-root-disk-image-loop-device-using-offset.html](http://nixcraft.com/ubuntu-debian/15295-ubuntu-mount-root-disk-image-loop-device-using-offset.html)

mkdir /vdisk mount -o loop -t ext4 /media/media/root.disk /vdisk
But the problem is mount do often, but nowhere I can see contents of mounted root disk.

Any suggestions here.

---

### Post by boy18nj on 2011-07-24
Suggestion in my last post worked for me.

---

### Post by papibe on 2011-07-24
Glad you solved it, also thanks for linking that useful guide   :D. I myself didn't know the specifics for a Wubi install.

Kind Regards.

---

