---
title: "How to remove Linux?"
date: 2010-10-15
forum: General Help
---

### Post by DavidFelix on 2010-10-15
Well, I can't say I didn't try it haha. But I want to reinstall Windows. I have the disk, and put it in but I guess its not bootable. How can I switch back?

---

### Post by tekkidd on 2010-10-15
Just install windows like normal and tell it to overwrite the linux partition

---

### Post by DavidFelix on 2010-10-15
But when I boot with the disk nothing happens.

---

### Post by CoolJohnB on 2010-10-15
Probably not a bootable disk

---

### Post by trisemigistus on 2010-10-15
I'm having the same problem. And my disk IS BOOTABLE before you say it isn't. I'm getting down to the point where I'm going to write a new disk containing a hard drive killer and just wipe it that way, as I see no other alternative.

---

### Post by bobcollard on 2010-10-15
Change your bios to boot cd/dvd first

---

### Post by trisemigistus on 2010-10-15
I don't know about the OP, but my BIOS is currently inaccessible due to Ubuntu restrictions. It doesn't even give me the option to open the BIOS.

---

### Post by hrickh on 2010-10-15
> **trisemigistus said:**
> I don't know about the OP, but my BIOS is currently inaccessible due to Ubuntu restrictions. It doesn't even give me the option to open the BIOS.
That just doesn't make sense. The BIOS is activated WAY before anything Ubuntu-related happens.

What likely is happening is whatever key-combination to get to the BIOS doesn't get a chance to display on the screen and Ubuntu begins to boot.

Do you know what the key combination is to get to the BIOS?

R.
==

---

### Post by roggenschrotbrot on 2010-10-15
> **trisemigistus said:**
> I don't know about the OP, but my BIOS is currently inaccessible due to Ubuntu restrictions. It doesn't even give me the option to open the BIOS.

how should it do this?

---

### Post by realzippy on 2010-10-15
Ubuntu can not restrict your BIOS access.
You have to press "del" or whatever *before* GRUB loads...

---

### Post by cholericfun on 2010-10-15
> **trisemigistus said:**
> I don't know about the OP, but my BIOS is currently inaccessible due to Ubuntu restrictions. It doesn't even give me the option to open the BIOS.

what?

how would that work?
BIOS is running before the OS. You may need to press some secret vendor-specific key on booting to even see the BIOS.

edit: haha this "issue" got a rush of replies...
all the same though, you not seeing the bios must be more of a visualization decision by the vendor.

---

### Post by realzippy on 2010-10-15
Nice quadshot from the bush behind...Ubuntu is **Not** guilty! :)

---

### Post by trisemigistus on 2010-10-15
Lol, thanks guys, and I didn't mean to hijack OP's thread. 

So, I'm running on a Dell. It's maybe 5-6 years old. And I was used to seeing some button options, but I guess they just don't show. I am able to press F12 and it allows me to choose from where I wish to boot, and I've chosen the disk drive many times for it to simply go to grub. So, any other buttons I should try other than F12?

---

### Post by cholericfun on 2010-10-15
well then why not use F12 and select CD/DVD?

edit : sorry i'm tired...
F2, esc, remove are classics to enter BIOS, just hack away at boottime

---

### Post by plucky on 2010-10-15
My Dell F12 goes to the boot menu,the bottom of which has access to the Setup menu.

Or F2 goes to the Setup menu.

Good Luck

---

### Post by DavidFelix on 2010-10-15
Hey, I just burned a bootable Windows XP disk but Ubuntu still loads and not the disk...

---

### Post by trisemigistus on 2010-10-15
Mraw, I had to press Delete to enter the Bios.

But it didn't matter, I was using the wrong disk. I found my old red dell operating system disk I had totally forgotten about. Coming to you now from the weakest form of XP, just installed Firefox and about to get service pack 2 installed and some anti-virus software my uncle gave me on a disk. 

Once XP is running full-potential, I'll be sliding in Ubuntu Lucid right next to it for dual-boot.

Thanks everyone. Oh, and this ain't my thread, so don't change it to "Solved". I'm not sure where OP is, but he's still workin on it, I think.

---

### Post by DavidFelix on 2010-10-15
Well, I booted from my XP disc and got some error.

---

### Post by cholericfun on 2010-10-15
what error?

maybe you want to try booting up a Linux liveCD and format your drive in some useful way (and in ntfs/or fat32) before booting to the windows cd although it should also allow you to format the drive while installing.

---

### Post by DavidFelix on 2010-10-15
It was like "0x00000654156" and said to restart and check for viruses. I retried like 6x :/

---

### Post by junapp on 2010-10-15
> **DavidFelix said:**
> It was like "0x00000654156" and said to restart and check for viruses. I retried like 6x :/

Looks like a Windows stop error. Take note of the actual number and look it up here:

[http://www.aumha.org/a/stop.php](http://www.aumha.org/a/stop.php)

---

