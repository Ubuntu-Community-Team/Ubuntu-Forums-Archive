---
title: "Ubuntu 9-10/XP dual boot"
date: 2010-01-12
forum: General Help
---

### Post by james.wilde on 2010-01-12
I've just done a search for hints on dual booting and not come up with what I want.

I have an old Dell laptop with both Dell's wireless adapter and a d-link pcmcia wireless card.  Unfortunately I haven't been able to get either card to work properly under Ubuntu 9-10, to my surprise.  This machine also has XP, which uses the d-link card with no problem.  Most of the time I'm happy to use this machine under XP, since I have a couple of other machines running different operating systems which I use more often.  Consequently I've removed grub and reinstalled the XP mbr.

Now there was a method of using the XP mbr for dual boot which involved copying the ubuntu boot sector to a file, placing that file on the XP c: drive, and placing a reference to that file as a second line in boot.ini.

This apparently worked fine on ubuntu distros prior to, I think, 8, after which grub was replaced with grub 2, which is apparently somewhat different.  I tried using the method with my ubuntu 9-10 installation on this laptop, without success and it appears that a dd of the ubuntu boot sector is empty.

XP is the first partition on the hard disk, ubuntu root is the second and swap is the third.

Grub is overkill, and has disadvantages given the frequency of my running ubuntu on this machine so I wonder - has anyone succeeded in using the XP mbr to start ubuntu after the introduction of grub 2, and if so, how?

TIA

//James

---

### Post by james.wilde on 2010-01-21
I take it this is a no-go - the only way is to let grub take over?

---

### Post by KyleFx on 2010-01-21
[Edit]  You have XP, and EasyBCD is for the vista/7 bootloader.  Sorry.  :(

I'm not sure if your primary goal is the elimination of grub, or being able to boot linux from the windows bootloader.  As far as I know, you cannot boot linux directly from the windows bootloader.  But, you can chainload grub from the windows bootloader, and set grubs timeout to zero, so it appears to boot directly.

If you want to boot grub from windows, EasyBCD is the way to go in my opinion.  It's a nice little program to help you set that up.  It also includes something called neogrub, which essentially installs grub on your windows partition from what I understand.  But I've never gone that route, so I can't speak intelligently about it.

---

### Post by Leppie on 2010-01-21
> **james.wilde said:**
> Grub is overkill, and has disadvantages given the frequency of my running ubuntu on this machine so I wonder - has anyone succeeded in using the XP mbr to start ubuntu after the introduction of grub 2, and if so, how?
grub2 is indeed very advanced and powerful. after reading 2 documents you most probably will be able to customize it to your own likings.
furthermore, there are soooooooo many threads about booting ubuntu with the xp boot manager on this forum. you may not have noticed the search box, but it's a handy dandy little tool on this forum. you may want to try it ;)

---

