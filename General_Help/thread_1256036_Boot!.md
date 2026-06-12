---
title: "Boot!"
date: 2009-09-02
forum: General Help
---

### Post by BlutBoomer on 2009-09-02
Okay guys, When I go to boot up, it boots up to the login, where I hear the noise that is normally there but my monitor light goes from green to orange and is a black screen, It works fine on XP, I also once got it working by running in repair mode, but hasnt worked since, and have had to re-install 3 times, and keeps happening, is there any way I can fix this?

---

### Post by NoaHall on 2009-09-02
So you can't get into repair mode? What is your graphics card? If you can't get into a terminal, you'll have to reinstall. What do you do everytime to make it do this? Is it after the first reboot after installing?

---

### Post by P4man on 2009-09-02
reinstalling (yet again) is not going to help. Common guys, this is not windows :)  Its almost certainly a resolution/refresh rate problem, your monitor can't handle.

Press control+alt+F1 when you get the black screen and see if you get a full screen terminal. If you do, we can try a few things to resolve the problem. Do tell us though, did you install any videodrivers? If so, ATI or nVidia ?

---

### Post by NoaHall on 2009-09-02
Reinstalling is the only option if he can't get to the terminal - after reinstalling, THEN you fix it ;)

---

### Post by fela on 2009-09-02
> **NoaHall said:**
> If you can't get into a terminal, you'll have to reinstall.

Actually, no. You can use chroot to get into the system from a livecd.

---

### Post by NoaHall on 2009-09-02
Chroot has never worked properly for me, so seeing as he has reinstalled before, if he reinstalls again, then it's easier to fix.

---

### Post by fela on 2009-09-02
> **NoaHall said:**
> Chroot has never worked properly for me, so seeing as he has reinstalled before, if he reinstalls again, then it's easier to fix.

What do you mean by it's never worked properly? I had to chroot into my current system so it could boot, as it's installed on an LVM and Ubuntu 8.10 doesn't include LVM support out of the box. I just chrooted and apt-get install lvm2 did the trick.
[B]
To the OP:[/B]

Is your graphics card nvidia or ati? If it's nvidia, boot the livecd up and mount the partition with ubuntu on it. Then, navigate with nautilus to (if it's mounted at /media/disk) /media/disk/etc/X11. There should be a file called xorg.conf. Open it with gedit and go to the bit in the file where it says 'configured video device' or something, it should have a driver line. Make sure the driver line goes:

```
Option Driver "nv"
```

Then try booting up again.

That will make it use the open source nv driver instead of any proprietary drivers installed on the system, making it easier to resolve the problem. It could always be something to do with the proprietary driver if there is one installed.

---

