---
title: "boot into ubuntu automatically"
date: 2010-02-13
forum: General Help
---

### Post by sincerelyydavid on 2010-02-13
when you dual-boot ubuntu with windows installed already, does it ask if you want to boot into either system when you first startup your computer? if so, is there a way to boot into ubuntu automatically without it asking whichever system you want to boot into?

---

### Post by mirosol on 2010-02-13
Yes, there is. Just wait for mandatory 3 seconds for letting grub to decide for you.

Best way to dualboot is install Win before any linux, but while we're at it.. If you don't ever want your computer to boot to windows, why are you keeping it's installation there in the first place?

---

### Post by drs305 on 2010-02-13
> **sincerelyydavid said:**
> when you dual-boot ubuntu with windows installed already, does it ask if you want to boot into either system when you first startup your computer? if so, is there a way to boot into ubuntu automatically without it asking whichever system you want to boot into?

You can get Grub to do what you wish but we need to know whether you are running Grub (Karmic and earlier) or Grub 2 (Karmic w/ updated Grub or Lucid). If you don't know, you can type "grub-install -v" in a terminal and it will tell you 0.97 or 1.96 or later (Grub 2).

If you have Grub 2, you can take a look at the following link. You would set the default OS and the menu timeout to suit your needs.
[Grub 2 - 5 Common Tasks]("http://ubuntuforums.org/showthread.php?t=1302743")

If you are still confused, run meierfra.'s script and post the results between "code" tags, which you get by pressing the # symbol in the menu when composing a post.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by sincerelyydavid on 2010-02-13
> **mirosol said:**
> Yes, there is. Just wait for mandatory 3 seconds for letting grub to decide for you.

Best way to dualboot is install Win before any linux, but while we're at it.. If you don't ever want your computer to boot to windows, why are you keeping it's installation there in the first place?
i'm keeping windows just in case, but if i wanted to delete windows altogether later on, how can i do this?

---

### Post by louieb on 2010-02-13
> **sincerelyydavid said:**
> ... but if i wanted to delete windows altogether...
Depends on how you set up dual booting. Can be as simple a reformatting the Win partition for use as data storage. Gets more complicate if you use the windows boot loader or set up dual booting using WUBI.

---

