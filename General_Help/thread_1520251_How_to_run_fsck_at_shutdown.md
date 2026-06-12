---
title: "How to run fsck at shutdown"
date: 2010-06-29
forum: General Help
---

### Post by meazz1 on 2010-06-29
Every 32 boot ups, the fsck runs automaticall on my drives.
I would like it to run at shutdown and was looking for a solution.
I saw an app call autofsck but could not find it in synaptic.

Can someone help me find a solution to this. 
I am running a laptop with 9.10 and a desktop with 8.10.

---

### Post by dino99 on 2010-06-29
sudo shutdown -r now

will run fsck on next boot

---

### Post by meazz1 on 2010-06-29
> **dino99 said:**
> sudo shutdown -r now

will run fsck on next boot

I am trying to automatically run it at shutdown time, not boot up time.

When it runs at boot up, sometimes it can go on for 5 to 10  mins and I want to change it. Running at shutdown time is preferable because I am not waiting for it any more, after it is done running, the pc can than be automatically shutdown.

---

### Post by philinux on 2010-06-29
[AutoFsck]("https://wiki.ubuntu.com/AutoFsck")

I've never used this at all and I dont know how up to date the package is. It certainly is not in lucid repos. The reason for that maybe is lucid uses ext4 by default on install. Ext4 fsck times are now very fast. Like a few seconds.

---

