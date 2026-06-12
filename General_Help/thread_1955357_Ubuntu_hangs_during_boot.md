---
title: "Ubuntu hangs during boot"
date: 2012-04-09
forum: General Help
---

### Post by bleakcabal on 2012-04-09
Hello, 

I have Ubuntu 11.04 Natty Narwhal, (upgraded from a LTS installation) with a dual-boot configuration. 

When I start my computer and grub shows up and I select Ubuntu, I get a purple screen without any text showing up. Almost every time the boot fails and I must physically reset the computer. Sometimes I can get it to work by pressing enter at the right time but this seldom happens. 

When my computer restarts from this crash, on the next boot, Ubuntu will show a black screen instead of a purple screen and boot text will show up. During this process the boot will normally stop at several occasions (between 1-3 times, mostly at the same places, the first stop is always at the same spot). 

When Ubuntu stops I must then press a key like enter to get the boot to work again. This works and I can get into Ubuntu. On very rare occasions (less then 5%), this has also failed and I needed to restart a third time. 

My questions are:

1- How can I have the boot process boot by itself without me needing to press keys ?

2- How do I try to fix this boot problem so that it works all the time ?

3- How can I have boot information during boot ?

I tried changing my config for my third myself, here are what I think are the relevant lines from my /etc/default/grub file :

```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="rootdelay=90 splash" 
```

In fact if I look at my grub file everything is commented out except this:

```
GRUB_DEFAULT=4
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=4
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="rootdelay=90 splash"
```

I have also check my /var/log/boot.log file and I can see this error:

```
 * Stopping automatic crash report generation[74G[[31mfail[39;49m]
```

I searched on the web for this message and while I found a thread I couldn't fix my problems with the answers in this thread.

---

### Post by oldfred on 2012-04-09
If you have to force shutdown:

Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

If you remove quiet & splash at the grub menu when you boot you will see the loading of every driver.

You see the same info in the messages log file. Look for long times between an entry or a repeated entry trying to load and then failing.

Is your default of 4 the one with the boot issue?

---

### Post by bleakcabal on 2012-04-09
> **oldfred said:**
> 

Is your default of 4 the one with the boot issue?

No it's the first entry.

---

