---
title: "Creating a backup"
date: 2010-07-24
forum: General Help
---

### Post by Lost-Found on 2010-07-24
Hi there,

Sorry if there's an anwser to this already - but I've searched(and tried).

I'm on ubuntu 10.04, and pretty new to it - over the last 2 weeks I've done probably 10+ fresh installs due to me not knowing the system, trying things.

I looked for a way to back it up and found this guide - [http://ubuntuforums.org/showthread.php?t=81311]("http://ubuntuforums.org/showthread.php?t=81311")

When I use the feature as listet, it doesn't exclude the folders, and the system is "almost" the same as pre-recovery - and I'm copy/pasting.

Is there a way to make a COMPLETE replica of my system, that I can launch when failed, so that - it's back to when I was "ok".. like all programs install post-copy to be gone..

---

### Post by rubylaser on 2010-07-24
If you have a drive of equal or greater size to your current drive, you could use dd or clonezilla.  dd is pretty easy, but dangerous if you get the order backwards.  Here's brief description of using dd...
[http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd]("http://www.linuxweblog.com/blogs/sandip/20050211/image-your-hard-drive-using-dd")

What you're doing with tar is basically making a filesystem backup rather than a block level backup like dd.  What's probably easier to do if you want to learn is install virtualbox, and install ubuntu in a virtual machine.  That way you can take snapshots and test things out. If something breaks, you just roll back the snapshot.

Hope that helps.

---

### Post by Mark Phelps on 2010-07-24
Recommend you use Clonezilla.  It provides the ability to backup individual partitions or entire drives.  You can also restore using the Clonezilla LiveCD from a stored backup.  I use this and it's only about 10 minutes to create an image backup.  Same amount of time to restore.  A LOT less time than reinstalling from scratch, reupdating all the packages, and reapplying all the configuration settings!

---

