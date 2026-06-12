---
title: "Upgraded 2.6.35-28 doesn't boot"
date: 2011-04-27
forum: General Help
---

### Post by l07 on 2011-04-27
When "sudo apt-get upgrade" said packages have been kept back, used "sudo aptitude dist-upgrade."

Obtained grub prompt on restart; purged and reinstalled grub using [the chroot method]("http://ubuntuforums.org/showthread.php?t=1581099"). This has become customarily necessary after certain system-wide changes (see my other threads) but I still don't know why. But it's not the main subject of this thread.

On restart obtained message saying kernel and fallback failed to load.
 Restarted and used shift to select 2.6.35-25 (3rd on the list) to load.

I inferred that 2.6.35-28 is at fault since the recent upgrade mentioned kernel generic.

Why does 2.6.35-28 fail to load? Should I set 2.6.35-25 as default?

---

### Post by garvinrick4 on 2011-04-27
> I inferred that 2.6.35-28 is at fault since the recent upgrade mentioned kernel generic.

Why does 2.6.35-28 fail to load? Should I set 2.6.35-25 as default? 	
If you get a kernel that will not boot just use another one. I cannot remember when
I had a bad one but to try and find what is at fault would be a waste of time.

> Obtained grub prompt on restart; purged and reinstalled grub using [the chroot method]("http://ubuntuforums.org/showthread.php?t=1581099").  This has become customarily necessary after certain system-wide changes  (see my other threads) but I still don't know why. But it's not the  main subject of this thread.

Do you have multiple installs of Ubuntu? Unusual to have to use chroot method unless you
have become unbootable for an unknown reason?

---

### Post by l07 on 2011-04-27
> **garvinrick4 said:**
> 
Do you have multiple installs of Ubuntu? Unusual to have to use chroot method unless you
have become unbootable for an unknown reason?

No, just the one. Those system-wide changes do make it unbootable (i.e., they result in a grub prompt on restart). By the way, without chroot method, it does boot fine on another computer (if I put the hard drive there).

---

