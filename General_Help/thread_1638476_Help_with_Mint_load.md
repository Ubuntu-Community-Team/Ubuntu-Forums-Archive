---
title: "Help with Mint load"
date: 2010-12-05
forum: General Help
---

### Post by aeronutt on 2010-12-05
I know this is the Ubuntu forum, but I hate to have to join the Mint forum to ask one question...

I'm trying to load Mint 10 without loading the boot loader. But I don't see a way to do that with in the install menu. I can't find an 'advanced' tab like there is in the ubuntu install menu, for example. And, seems there was an advanced tab in previous version of Mint, but not in Mint 10.


I've googled and searched various forums to no avail.

Any one with Mint experience have ideas?

---

### Post by davidmohammed on 2010-12-05
do you mean "how to start ubuntu/mint without grub2"?  

Doubt if you can - why what is the issue?  If you dont like to see grub then just adjust its settings to delay boot to 1 second and stay hidden.

---

### Post by aeronutt on 2010-12-05
No, sorry I wasn't clear. I already have multiple OS's (Ubuntu, XP, etc) AND grub2 loaded. So, I mean I don't want to (re)load a boot loader when I load Mint. As far as I can find, the Mint 10 install GUI does not give me an option to not load a boot loader.  I'm happy with grub2 as I currently have it configured on my system, and don't want to risk reloading another.

---

### Post by gordintoronto on 2010-12-05
However, your grub2 does not know about a future installation of Mint, so if you install (not "load") Mint, you need to update the grub.

---

### Post by aeronutt on 2010-12-05
> **gordintoronto said:**
> However, your grub2 does not know about a future installation of Mint, so if you install (not "load") Mint, you need to update the grub.

Yes, I know I have to run update grub after installing another OS.

---

