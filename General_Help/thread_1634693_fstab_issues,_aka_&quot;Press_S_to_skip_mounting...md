---
title: "fstab issues, aka &quot;Press S to skip mounting...&quot;"
date: 2010-11-30
forum: General Help
---

### Post by djbrettb on 2010-11-30
Hi all,

I have a file server running freshly-installed Ubuntu Server 10.10, with swappable bays on the front. I configured fstab to auto-mount any drive that's plugged in, via the UUID of each drive. The problem is, I purposely leave my backup drives unplugged until I want to actually perform backups, and because of this, every time I boot, I am notified that the drives can't be found, and I have to press 'S' to skip mounting for each of them. That's fine if I'm physically here next to the server, but if I'm away and need to reboot via an SSH session, I won't be able to manually skip the mounting.

I've done this previously with the exact same configuration (quite a while ago, using 9.04) and never had this issue.

I'd greatly appreciate any help in resolving this issue. :)

Brett

---

### Post by dcstar on 2010-11-30
> **djbrettb said:**
> Hi all,

I have a file server running freshly-installed Ubuntu Server 10.10, with swappable bays on the front. I configured fstab to auto-mount any drive that's plugged in, via the UUID of each drive. The problem is, I purposely leave my backup drives unplugged until I want to actually perform backups, and because of this, every time I boot, I am notified that the drives can't be found, and I have to press 'S' to skip mounting for each of them. That's fine if I'm physically here next to the server, but if I'm away and need to reboot via an SSH session, I won't be able to manually skip the mounting.

I've done this previously with the exact same configuration (quite a while ago, using 9.04) and never had this issue.

I'd greatly appreciate any help in resolving this issue. :)

Brett

Add the **noauto** option to the fstab line.

---

### Post by djbrettb on 2010-12-01
> **dcstar said:**
> Add the **noauto** option to the fstab line.

Wouldn't that mean, then, that the drive won't auto-mount even when it's plugged in?

---

### Post by monkeyking on 2010-12-10
I also have this annoying problem, of the boot process hanging.

We have an whole bunch of disk we could earlier hotswap depending on what we needed. It actually didnt mount it automaticly we had to do a 'mount -a'.

At boot it would pose no problem, it would simply skip the mount if it couldnt see the UUID.


Now we have added the noauto, instead of auto, in fstab.
Then we cd into the folder where drives would be mounted an do 'ls |xargs -n1 mount'

Then it will try to mount every UUID entry in the fstab.

Its not optimal, but it works.

---

