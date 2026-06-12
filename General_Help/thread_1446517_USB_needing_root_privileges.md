---
title: "USB needing root privileges"
date: 2010-04-04
forum: General Help
---

### Post by Colo2 on 2010-04-04
Hey

We formatted a USB stick to EXT3 for use on a linux formatted device.
Now, when we try and transfer files from this ubuntu laptop onto the USB stick, it says permission denied.

It works, however, if we used nautilus in root. (sudo)

Why is this?

Thanks

- Tom

---

### Post by Colo2 on 2010-04-04
We worked it out
thanks

changed the permissions in the folder properties whilst using nautilus as root.

Thannkks

---

### Post by 3rdalbum on 2010-04-04
Yeah if I'd been here 45 minutes ago I would have said "Change the permissions of the mount point" :-)  Glad you solved it anyway, and congratulations for figuring it out so quickly too!

---

### Post by rbwilliams on 2010-04-09
G'day mate.

I don't know anything about linux and I don't know how to change the permissions from root to user.

I amade a screenshot of what I typed into terminal.

[http://preview.tinyurl.com/y6gp3em](http://preview.tinyurl.com/y6gp3em)

I would like to create a Slax USB drive. I am using Ubuntu because Vista sucks. But, I would like to put XP on it and boot into Slax whenever I want.

But, I can't seem to do it. So many roadblocks.

Thanks.

---

### Post by rbwilliams on 2010-04-09
Found another thread or forum.

It listed this command line:

chown -R "username" /media/"drivename"

That did it for me!

---

