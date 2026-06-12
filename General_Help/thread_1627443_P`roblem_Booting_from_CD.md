---
title: "P`roblem Booting from CD"
date: 2010-11-21
forum: General Help
---

### Post by danmoreno on 2010-11-21
Hey,

Im a Windows user, trying Ubuntu. Downloaded it from the site, burn the iso to CD and tried booting. But thats when the problem appeared: it shows the ubuntu logo and the loading thing (balls). It does that a few times, then stops and the lights on my keyboard start blinking (caps lock and such). And it stays that way. So that was a unsuccessful try. Can someone tell me why? Is my system not supported? This is a rather old system I´m trying it on (P4, 2.33mhz Intel Board, Nvidia display). Thanks,

Daniel Moreno

---

### Post by sikander3786 on 2010-11-21
Hi. Welcome to the forums :popcorn:

First of all check the disc for defects. You'll need to press any key as soon as the computer starts booting from the disc and a menu will be presented. There is an entry for checking the disc.

You might also need to put in some boot options like nomodest or acpi=off by pressing F6 on the same page.

Please see here.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by danmoreno on 2010-11-21
Hi!

Tried what you said, this is what I get:

Busy Box ----
(initramfs) mounting /dev/loop0  on //filesystem failed: Input / output error
can not mount  /dev/loop0 (/cdrom/casper/filesystem.squashfs)  on  //filesystem.squashfs


Could it be Linux does not support NTFS? Or does it? thanks!

Dan

---

### Post by sikander3786 on 2010-11-21
> Could it be Linux does not support NTFS? Or does it? thanks!


Linux supports NTFS but it doesn't matter if it does or doesn't as you are booting from a Live CD and it has nothing to do with NTFS.

Did you check the disc for defects? Is it ok?

And which one of the parameters did you try? All of them are worth trying one-by-one. Before that make sure that you don't have a bad burnt disc.

---

### Post by danmoreno on 2010-11-21
Ok, tried both, they didnt work. Im burning a CD again to see if the problem is the disc. I will post results here. thanks,

Dan

---

### Post by danmoreno on 2010-11-21
No, it didn´t work. Fresh new CD, tried the options and even the EDD the page mentioned. It all gives the same error on mounting. what to do?

Dan

---

### Post by danmoreno on 2010-11-21
Ok I get it. giving up then. bye.

---

