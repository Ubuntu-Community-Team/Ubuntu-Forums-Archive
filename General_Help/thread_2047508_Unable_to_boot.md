---
title: "Unable to boot"
date: 2012-08-25
forum: General Help
---

### Post by jeree on 2012-08-25
Hi,

I have a dual boot computer (Ubuntu 11.10 or 11.04 / Win7). Everything was working fine until yesterday when it froze while I was under Win7, after that I can't boot the computer anymore and it keeps restarting. The restart occurs right before the when the grub should start (I can't see the grub at all).

I've tried to boot from Ubuntu live CD, but that doesn't also work. I got this alert from 9.04, when I tried to choose "try ubuntu without installing it" from the menu.
```
Boot loader
/casper/vmlinz
```
This one from 10.4
```
boot loader
live: file not found
```
And 11.10 doesn't even get me to the menu, instead shows some cryptic table with titles data and prog.

I can however access the text terminal which is prefixed by ```
boot:
```

I tried to google the issue, but what I only managed to find terminal commands (which I can't from the boot terminal, I think).

---

### Post by beboylips on 2012-08-25
Seems to me like a hardware issue, most likely faulty RAM (Win7 freezing being the clue). Usually, the computer would not boot or give out noise signals if the CPU or the motherboard was at fault which leads me back to the RAM. 

If you have more than one stick, try removing each one individually and booting with only one.

---

### Post by jeree on 2012-08-25
> **beboylips said:**
> Seems to me like a hardware issue, most likely faulty RAM (Win7 freezing being the clue). Usually, the computer would not boot or give out noise signals if the CPU or the motherboard was at fault which leads me back to the RAM. 

If you have more than one stick, try removing each one individually and booting with only one.

The problem was indeed faulty RAM stick, thank you very much.

---

### Post by beboylips on 2012-08-25
You're welcome and don't forget to mark the post as solved.

---

