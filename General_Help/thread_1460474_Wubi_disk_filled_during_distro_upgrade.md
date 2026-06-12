---
title: "Wubi disk filled during distro upgrade?"
date: 2010-04-22
forum: General Help
---

### Post by Redundant Username on 2010-04-22
I have 0MB left on my Wubi disk.:( How do I enlarge the virtual partition for Wubi if I don't have enough space to install anything?

---

### Post by Redundant Username on 2010-04-22
If no one's responding, I might as well go head and back up my /home directory so I can reinstall. edit: I don't think I'll be able to see what's on the screen, since Ubuntu doesn't have ATI drivers by defualt.

---

### Post by wilee-nilee on 2010-04-22
I am not sure if wubi was designed to be a long term use with upgrades. The problems probably are when you upgrade a ubuntu installation it doesn't know that your running it inside of another OS.

You might consider running Ubuntu in the Sun Virtual puel, if you don't want to dual-boot outside of a wubi install. Ther are several virtuals available. It can be nice at times to be able to run multiple OS at once.

---

### Post by Redundant Username on 2010-04-22
I absolutely detest Virtualbox, I'd rather use Wubi to natively run Ubuntu and take full advantage of my hardware. Also, Wubi isn't run inside of another OS, it's a full os that's run from a virtual partion. I would just back up the entire partition and reinstall with a larger partition, but I don't know if that'd work. edit: Wubi is fine for long term use as long as the partition is big enough, it's the same for any OS.

---

### Post by wilee-nilee on 2010-04-22
> **Redundant Username said:**
> I absolutely detest Virtualbox, I'd rather use Wubi to natively run Ubuntu and take full advantage of my hardware. Also, Wubi isn't run inside of another OS, it's a full os that's run from a virtual partion. I would just back up the entire partition and reinstall with a larger partition, but I don't know if that'd work. edit: Wubi is fine for long term use as long as the partition is big enough, it's the same for any OS.

There are inherent problems with wubi, for example if the MS crashes and you can't even get it to bootup, I believe the wubi install is gone. A dual boot would really be your best choice if that works for you. Wubi installs also run slower then a regular install, and it is in a psuedo virtual partition inside of windows.

I am going to turn off the notification of this thread in that I feel a bit of tension in your post and a unwillingness to really investigate the inherent problems with wubi. It is designed to try out Ubuntu, not as a long term solution. There are better ways to run a OS. on a big thumb drive, a external hard drive, a dualboot, a virtual.

---

### Post by Redundant Username on 2010-04-22
Sorry, I'm stressed right now. I found out how to resize my partition with LVPM, it's just that there's no space on my partition to install LVPM. I do have a second drive with 2nd drive with 2 NTFS partions on them, but I don't know how to dual boot with multiple drives. I would also have to transfer all of the files to one partition and resize it, risking file corruption.

---

### Post by Redundant Username on 2010-04-23
*legal bump*

---

### Post by StuartN on 2010-04-23
> **Redundant Username said:**
> *legal bump*

The safest approach is probably to back up your personal data and then re-install. You might restore some function immediately by clearing the apt cache (sudo apt-get clean) and - carefully - deleting anything else useless.

---

