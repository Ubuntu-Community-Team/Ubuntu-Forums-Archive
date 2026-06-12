---
title: "Trying to get access to hard drive with Ubuntu"
date: 2011-12-29
forum: General Help
---

### Post by BaconJ on 2011-12-29
Hello!

Today my computer wouldn't boot Windows XP, so I booted Ubuntu from an USB to try to get access to the hard drive and retrieve some files that way. Unfortunately I am a total Ubuntu noob and haven't been able to do this yet.

I have tried GParted and am able to find the hard drive, also through the home folder:

[[IMG]http://img838.imageshack.us/img838/6131/screenshotat20111229173.png[/IMG]]("http://imageshack.us/photo/my-images/838/screenshotat20111229173.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")


But when I click on it or right click > Mount, nothing happens for a minute and then this show up:

[[IMG]http://img850.imageshack.us/img850/6131/screenshotat20111229173.png[/IMG]]("http://imageshack.us/photo/my-images/850/screenshotat20111229173.png/")

Uploaded with [ImageShack.us]("http://imageshack.us")
(inception screenshot)

I've tried to use some terminal guides I found online too, but no luck so far...

Any ideas? I would really appreciate it :)

---

### Post by CharlesA on 2011-12-29
You need to run chkdsk on the drive (from Windows, or the Windows recovery console) before you can mount it.

---

### Post by BaconJ on 2011-12-29
Ah.. So I need to do that from Windows, which I can't boot? :(

---

### Post by CharlesA on 2011-12-29
If you have an xp cd around, you can run chkdsk from the recovery console.

[http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/](http://www.geekstogo.com/forum/topic/231709-how-to-run-chkdsk-on-ntfs-drive-when-i-cannot-boot-windows/)

---

