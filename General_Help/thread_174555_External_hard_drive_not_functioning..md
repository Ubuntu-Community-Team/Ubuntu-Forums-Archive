---
title: "External hard drive not functioning."
date: 2006-05-12
forum: General Help
---

### Post by goomba on 2006-05-12
I have a 40gb Seagate external hard drive... Today I got it to work for the first time under Windows XP (I had to buy a hub because it needed more power to run), and I uninstalled XP today and am now running Kubuntu.

When I plug the hard drive into the USB, a Konqueror window pops up media:/sdb1 and all it says is the following error message:

An error occurred while loading media:/sdb1:
The file or folder media:/sdb1 does not exist.

The drive doesn't show up in media:/, only the primary drive does. I refresh it, and still... doesn't show up.

Thank you!

---

### Post by goomba on 2006-05-12
Please? The flash drives are doing the same thing... this has never happened before.

---

### Post by goomba on 2006-05-12
Nevermind, problem solved. Looks like I've made a mess of this thread :-#

---

### Post by jeremy on 2006-05-13
Perhaps you could add your solution to this thread, it may help others.

---

### Post by Peacepunk on 2006-05-13
Yes indeed - as i'm having JUST the same issue, same warning, I'd appreciate greatly.

Please notice that the error message doesn't mean pmount to fail; this is a KDE issue, where your device is not in 
> media:/*device* but is present (& mounted) if you look in > /media/*device*

the consequence is the inability to find your equipment in the Storage Media shortcut, and this annoying error message...

---

### Post by nejode on 2006-05-13
Upgrading to KDE 3.5.x should fix the problem.  It did it for me with Breezy.  Dapper already comes with 3.5.2 so the bug didn't show up.

---

