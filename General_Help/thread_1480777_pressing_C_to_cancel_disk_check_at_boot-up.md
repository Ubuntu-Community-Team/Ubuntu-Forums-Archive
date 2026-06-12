---
title: "pressing C to cancel disk check at boot-up"
date: 2010-05-11
forum: General Help
---

### Post by Silver_Swords on 2010-05-11
hi all. my comp hangs when disk check reaches 91% and pressing C to cancel does nothing. from irc-#ubuntu i was given this "sudo tune2fs -c 0" to cancel all future disk checking but it did not work. my drive is 2 months old.

---

### Post by GSF1200S on 2010-05-11
> **Silver_Swords said:**
> hi all. my comp hangs when disk check reaches 91% and pressing C to cancel does nothing. from irc-#ubuntu i was given this "sudo tune2fs -c 0" to cancel all future disk checking but it did not work. my drive is 2 months old.

If you cant get the kernel to boot because of the disk check, how (and where) are you running the command? You could chroot in from a live cd and run that command, but if you just run that command from a livecd its not going to change your harddrive install...

Ask for help if you wanna try the chroot route.

---

### Post by Silver_Swords on 2010-05-11
the first time it happened i managed to get to desktop by repeatedly reseting comp and pushing lots of keys together when disk check hangs at 91%  =)

straight after that i went to irc, did the command in terminal and figured it was taken care of. until today when disk check came back at boot-up i had to go through the same messy procedure of lots of keys and reseting comp. i would be happy if pressing C actually worked.

---

### Post by cnbiz850 on 2010-05-12
I have the same problem.  Press C did not work.  I think pressing Esc worked. After logging in, the CPU temperature is very high ~ 70C vs. 45C normally.

---

### Post by londonlad on 2010-05-12
i have this prob too, i may go back to 9.10, 10.4 is too buggy for me atm!

---

### Post by londonlad on 2010-05-14
ive gone back to 9.10, i'll try 10.4 again in about 6 months or so!

---

### Post by cjacek on 2010-05-15
I have that same problem. **Can some please tell me _HOW_ to go back to the previous 9.10 (stable) version of Ubuntu?** Also, if I go back, will there still be automatic updates for it? Thanks guys!:)

---

### Post by jerome1232 on 2010-05-15
> **londonlad said:**
> ive gone back to 9.10, i'll try 10.4 again in about 6 months or so!

fyi, that command was missing a part. The partition you wanted to run it on.

ie

```
sudo tune2fs -c 0 /dev/sda1
```

That's assuming the disk is /dev/sda1, you would adjust accordingly. You could also have ran fsck from a live cd, no nonsense about chrooting which actually defeats the point of using a live cd. Since you need to fsck the disk while it's not mounted, and chrooting will involve mounting it.

---

### Post by sports fan Matt on 2010-05-15
just have a random question.  Except for this instance, since the machine hangs, isn't a canceling of the disk check harmful?

---

### Post by bumanie on 2010-05-15
The slow fsck has been lodged at [launchpad]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/571707") as a a bug and a fix has been committed and I think released - not sure how long it will take to get in the repositories.

---

### Post by jerome1232 on 2010-05-15
Probably. I think it would only be harmful to the filesystem if fsck was finding errors and fixing them atm or replaying the journal when power was cut. Generally those routine fscks are just that routine and not doing much (they will optimize inode's and a few other things though)

It would be best to fsck from a live cd to get some good verbose output so you have a good idea of what's going on.

Another thought would be to check the drives smart data (in 10.04 System-Administration-Disk Utilities) It can warn you if the drive itself is failing in some way.

---

### Post by gwm on 2010-05-27
I have the same problem. C does nothing. Perhaps I should try the escape key as suggested.

Have you ever booted up your laptop 5 minutes before a demo and this disk check thing happens. No problem - press C. Uh oh! "Well you see it's this Ubuntu OS you see ..." Not a good advert! Then they have to reschedule your part to later because you use this "dumb" OS that you were bragging about. Generally they are not impressed.

I hope the fix mentioned earlier comes soon.

---

### Post by Jarppi on 2010-06-14
Same problem here. Thankfully pressing Esc cancelled the check. I waited over an hour for it to complete. There's something seriously wrong with the checking routine. Hope there's a fix for it coming.

---

### Post by karthick87 on 2010-06-14
The same here,Pressing C doesn't work..

---

