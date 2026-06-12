---
title: "Problem un automount of DVD-roms"
date: 2006-02-12
forum: General Help
---

### Post by aleg on 2006-02-12
Hi all, I just installed kubuntu 5.10 on my laptop Acer Travelmate 803LCi. I have the following problem: as I insert a cd-rom in my drive, it is correctly automatically mounted, but, if I insert a DVD-rom, I get a Konqueror window reporting that an error occurred while mounting  media:/hdc. 

When I manually mount the DVD-rom, with the command "mount -t auto /dev/dvd /media/tmpmountpoint" it works and the disk gets mounted.

How can fix the problem of automatic mount of DVD-roms?

Thanks.
Aleg.

---

### Post by gingermark on 2006-02-12
I think the Konqueror bit is down to ivman - have a look at this thread: [http://ubuntuforums.org/showthread.php?t=90457](http://ubuntuforums.org/showthread.php?t=90457)

Not sure why it wouldn't mount though, but as (I think) ivman is responsible for automounting, maybe sorting out it's config file will sort that problem too...

---

### Post by aleg on 2006-02-12
Hi gingermark, I tried to do what described in the post you linked, but i could'nt fix my problem.
It seems that DVD insertion is not *recognised* by the system.

Any other hint?
Thanks,
aleg.

---

### Post by gingermark on 2006-02-12
To be honest, I don't know.

If it was me, I might have a look at the file fstab in /etc. This controls what is mounted where, what filesystem is used, and so on. I haven't touched it on my system since I set up Hoary a while back, and I'm not sure if anything has superceded it.

Maybe post it's contents here, and see if anything stands out.

---

