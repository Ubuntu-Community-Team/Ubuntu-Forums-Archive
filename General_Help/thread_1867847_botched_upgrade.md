---
title: "botched upgrade"
date: 2011-10-23
forum: General Help
---

### Post by isecore on 2011-10-23
So, how do you redo an upgrade? I had a perfectly running Natty system, I attempted to upgrade to Oneiric. Halfway in it gives me some noise about gnome-dropbox, and with about 6 minutes left the updater simply dies. Now my system is half-functional. It boots, but no sound, and there are numerous glitches in the desktop indicating that some packages are either missing or weren't upgraded properly.

So, how to resolve this? 

Each upgrade I grow more and more tired of the increasingly more unstable way of upgrading. Now I need to resolve this, and reinstalling is not an option.

It would also seem that having dropbox installed while attempting to upgrade is VERY DANGEROUS.

---

### Post by cryptotheslow on 2011-10-23
I guess you can try working out which packages are corrupt and use
```
sudo apt-get install --reinstall *<packagename>*
``` 

to reinstall them, maybe with the --force  option as well.

Why is reinstalling not an option? It would probably be the quickest route if multiple things are messed up.

---

### Post by isecore on 2011-10-23
> **cryptotheslow said:**
> Why is reinstalling not an option? It would probably be the quickest route if multiple things are messed up.

The more I look at this, the more I am going to be forced to reinstall. I was hoping to avoid it since it's a BIG hassle moving 1.5TB of data around, especially when you have nothing to move it to. But I'll have to find a solution tomorrow somehow.

Thanks for your input.

---

### Post by cryptotheslow on 2011-10-23
Ouch that is going to be time consuming :(

Is most of the data in a separate /home or other partition - or is it contained in the main filesystem? If the former then you should be able to use the advanced partition option in the installer to mount the partitions back where they need to be without having to backup / restore them. Just be really careful not to format them!

Still not sure I'd want to attempt it without a backup though, just in case.

---

### Post by isecore on 2011-10-23
> **cryptotheslow said:**
> Ouch that is going to be time consuming :(

Is most of the data in a separate /home or other partition - or is it contained in the main filesystem? If the former then you should be able to use the advanced partition option in the installer to mount the partitions back where they need to be without having to backup / restore them. Just be really careful not to format them!

Still not sure I'd want to attempt it without a backup though, just in case.

Unfortunately it's all in one partition. That's how I set it up two years ago when I first installed it, and it's not how it will be setup after I reinstall this time. It's on a LVM-stripe over three drives, so it will be somewhat time consuming moving stuff in and out.

Oh well.

---

### Post by cryptotheslow on 2011-10-23
Good luck with that. I've never messed with LVM - always used classical partitioning, so I will bow out gracefully :D

---

