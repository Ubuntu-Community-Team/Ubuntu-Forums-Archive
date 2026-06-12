---
title: "Weird soundcard init problems"
date: 2009-12-04
forum: General Help
---

### Post by deathbyswiftwind on 2009-12-04
I was wondering if someone could please help me out. The other day after I did some updates(kernel and a few others) now my soundcard will sometimes work sometimes not. I tried running the old kernel but that doesnt have any effect so it must be something other than the kernel. Any help would be appreciated.

Sorry forgot to add the output of lspci

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

while it shows up here under the system test it only displays "dummy output" with no other selections available

---

### Post by deathbyswiftwind on 2009-12-04
Nevermind solved this problem due to 


michaelzap
	
Re: No sound after upgrade to Karmic Koala 9.10
I what may be the same problem on my Lenovo Y530 (no sound device reported in the Sound Control Panel, no sound input or output, and random crashes). I removed the proprietary driver for my internal modem (which it turns out is a sub-element of my Intel sound card) and suddenly I had sound and the device is visible in the Sound Control Panel (and so far I've had no more crashes). It's too early for me to be sure that the issue is resolved, but I'm happy not to use my modem if my system will be stable and have sound.

---

