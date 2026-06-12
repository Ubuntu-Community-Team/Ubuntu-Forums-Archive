---
title: "Rockboxed iPod 4G suddenly won't mount"
date: 2010-03-13
forum: General Help
---

### Post by l3lackEyedAngels on 2010-03-13
I've been a happy Rockbox and Ubuntu 9.10 user for some time now, but two days ago something weird happened. While trying to upgrade to Rockbox 3.5.1, I accidentally installed a current build on my fourth generation iPod Photo. I did this using the installer on a Windows machine. When I tried to connect the iPod to my Ubuntu laptop by USB later on, it would not mount, not even if I manually switched to Apple's firmware. In either case, it would show up in the Palimpsest disk utility, but with the mount option disabled. So I went to my wife's MacBook Pro, where the iPod mounted properly, and installed the latest stable version of Rockbox, 3.5.1. I tried connecting to my Ubuntu laptop again and the iPod still does not mount. It still shows up in Palimpsest with no option to mount.

I keep all of my music on my Ubuntu laptop so having proper iPod connectivity here is pretty important. Hopefully someone can help. I went to the Rockbox forums first. [Here's the link to that thread]("http://forums.rockbox.org/index.php?topic=24031.0"). I am also l3lackEyedAngels over there.

Concurrently, another issue popped up and I do not know if it's related. I started a thread for that issue [here]("http://ubuntuforums.org/showthread.php?t=1429312").

EDIT: Per a suggestion in the other forum, I added the following line to /etc/fstab.```
/dev/sdc2 	/media/ipod	vfat	rw,user,noauto,exec		0	0
```Now I can mount the iPod manually with [code]mount /media/ipod[/quote], but I can't safely disconnect the device unless I go through Palipmsest. So, my situation has improved, but I miss the way things used to be. How do I make everything work automatically again?

---

