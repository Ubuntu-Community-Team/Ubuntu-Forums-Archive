---
title: "Ubuntu boots into fall-back due to fatal error"
date: 2011-12-22
forum: General Help
---

### Post by greenblob on 2011-12-22
Hi all,
I installed Ubuntu 11.04 32 bit to my Dell Dimension 5100 on my primary (C) drive alongside my Windows 7 64 bit install. 

Both Ubuntu and Windows 7 worked fine, but then I was asked to upgrade Ubuntu to 11.10, so I did. everything was going perfectly, and my PC was in the stage of installing the upgrade which has been downloaded, when I lost power to my PC.

Windows still works fine, as it obviously wasn't affected by the failed Ubuntu upgrade, but Ubuntu didn't go so well...

I select standard Ubuntu boot in Grub 2 boot screen, and the Ubuntu loading screen appears for a few seconds, followed by a blank screen with a dialogue box with no graphical styling telling me it has booted  into a low-end mode or something of that nature because it couldn't configure my hardware correctly.

I have a few options, but only one actually has an affect (all the others select fine, I click OK, and nothing happens, I'm instantly back at the dialogue box), but the first option, saying something along the lines of "Boot into Ubuntu low-end this session only, and do standard Ubuntu next time" - I click it, and the Ubuntu loading screen appears with the message "Please wait a minute while Ubuntu restarts your display". This has been here about 10 minutes with no signs of progress, just my HDD whirring away.


[COLOR="Red"]Does anybody know roughly what the problem is, and how I could go about fixing it please?[/COLOR]

Thanks for any help,
Luke

**I can give exact errors if needed, and I can probably bring up and emergency terminal in recovery mode to do some commands if needed.**

---

### Post by davethewave83 on 2011-12-22
> **greenblob said:**
> Hi all,
I installed Ubuntu 11.04 32 bit to my Dell Dimension 5100 on my primary (C) drive alongside my Windows 7 64 bit install. 

Both Ubuntu and Windows 7 worked fine, but then I was asked to upgrade Ubuntu to 11.10, so I did. everything was going perfectly, and my PC was in the stage of installing the upgrade which has been downloaded, when I lost power to my PC.

Windows still works fine, as it obviously wasn't affected by the failed Ubuntu upgrade, but Ubuntu didn't go so well...

I select standard Ubuntu boot in Grub 2 boot screen, and the Ubuntu loading screen appears for a few seconds, followed by a blank screen with a dialogue box with no graphical styling telling me it has booted  into a low-end mode or something of that nature because it couldn't configure my hardware correctly.

I have a few options, but only one actually has an affect (all the others select fine, I click OK, and nothing happens, I'm instantly back at the dialogue box), but the first option, saying something along the lines of "Boot into Ubuntu low-end this session only, and do standard Ubuntu next time" - I click it, and the Ubuntu loading screen appears with the message "Please wait a minute while Ubuntu restarts your display". This has been here about 10 minutes with no signs of progress, just my HDD whirring away.


[COLOR="Red"]Does anybody know roughly what the problem is, and how I could go about fixing it please?[/COLOR]

Thanks for any help,
Luke

**I can give exact errors if needed, and I can probably bring up and emergency terminal in recovery mode to do some commands if needed.**

I think the Ubuntu install disc gives you the option to install over your current installation but retain your /home folder and personal files. you could try a clean "upgrade" from a disc to see if that fixes it. I've noticed in the past GNU/Linux does not like power-loss or improper shut downs, even worse than Windows. It really makes it angry, so it's good to have a battery backup for things like this. (As well as a system backup)

---

### Post by BC59 on 2011-12-22
Why don't you boot using older kernels?

---

### Post by greenblob on 2011-12-22
An upgrade from 11.04 to 11.04 from the disk worked magic, and now I FINALLY have a working Ubuntu / Windows 7 Dual Boot - THANKS ALL :KS

---

### Post by davethewave83 on 2011-12-22
> **greenblob said:**
> An upgrade from 11.04 to 11.04 from the disk worked magic, and now I FINALLY have a working Ubuntu / Windows 7 Dual Boot - THANKS ALL :KS

Good to hear! ;)

---

