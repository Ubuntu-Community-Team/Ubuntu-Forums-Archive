---
title: "'loading hardware drivers' freeze"
date: 2006-06-13
forum: General Help
---

### Post by jamesford on 2006-06-13
theres a big thread about this on the closed dapper devel forum. anyway the problem still exists, and i belive the problem is related to my soundblaster audigy2 card. 
wondering if anyone else with this problem also own a similar soundcard.

---

### Post by caserio on 2006-06-13
Hi,
My SB Audigy 2 ZS works fine.

---

### Post by bluevoodoo1 on 2006-06-17
[QUOTE=jamesford]theres a big thread about this on the closed dapper devel forum. anyway the problem still exists, and i belive the problem is related to my soundblaster audigy2 card. 
wondering if anyone else with this problem also own a similar soundcard.[/QUOTE]

I had created a thread about it here... [http://ubuntuforums.org/showthread.php?t=167722](http://ubuntuforums.org/showthread.php?t=167722)

For me, it had seemed to have been fixed with 2.6.15-23, but the problem seems to be back with the 2.6.15-25 kernel. (I have onboard sound)

---

### Post by cronholio on 2006-06-18
Is it possible to point the developers' attention to this once again? The last post in the bug report on Launchpad is 7 weeks old: 

[https://launchpad.net/malone/bugs/32597](https://launchpad.net/malone/bugs/32597)

I can't understand why this hasn't been fixed in the final release. It seems a lot of users are affected by this and it's a dead serious problem especially if you can't Ctrl-C out of it (like in my case). I am willing to give any kind of helpful hardware information and participate in testing and whatnot. I'll even throw in some $$$ if needed but please solve this somebody.

People that try out Dapper will never have a look at it again when this error appears and people that rely on Dapper as their only Desktop system (like me) get seriously pissed off.

---

### Post by bluevoodoo1 on 2006-06-18
I reinstalled "udev" and after 2 reboots it has started up without hanging.

---

### Post by cronholio on 2006-06-20
I reinstalled udev and it hasn't improved. I rebooted 8 times this morning, it always freezed. I'm talking about hard reboot, the button thingy. Nothing else works. Finally I booted into safe mode which always seems to work.

If I boot into safe mode and then continue with Ctrl-D, it is basically the same boot process as a normal boot, am I right? Because that's what I did. Loading hardware drivers always succeeds in this case. Maybe it really has to do with the graphical boot screen vs the text mode one, as someone suggested earlier.

---

