---
title: "can i reformat only the xp partition on my dual booted system?"
date: 2012-04-13
forum: General Help
---

### Post by jinjin on 2012-04-13
i have a computer that is dual booted with ubuntu and windows xp.  i recently caught a nasty virus/spyware on my windows xp. here are my questions.
1) can this virus on my xp partition somehow spread to my ubuntu?
2) can i reformat only the xp partition and keep the ubuntu partition alone because i really don't want to have to re-install drivers, settings and etc on both the xp and ubuntu.
3) if number is possible, would i have to do anything special to get the xp or ubuntu to boot if i only reformatted the xp partition? i read somewhere that i needed to fix grub or something that like, or would it work automatically?


thanks alot!

---

### Post by bodhi.zazen on 2012-04-13
See this question , and answers

[http://ubuntuforums.org/showthread.php?t=1958273](http://ubuntuforums.org/showthread.php?t=1958273)

---

### Post by callmemahavir on 2012-04-14
Answer to 1) Linux is a secure and virus free system.
Answer to 2) In win xp if you reinstall the OS reinstall of drivers required.


Format is a task which deletes all the data. Before doing anything you have to know the effect of it. First in WIN XP keep all the data safe by writing to CD or DVD and keep it safe. Because the CD or DVD is a read-only media, backup to it may not infected by virus. It is very important that boot record of ubuntu should be safe while reinstalling the win xp. And while installing the win xp ensure that ubuntu partition is not touched and not formatted. Also create a bootable disc for ubuntu partition (in CD-ROM) and keep it safe. If you cannot boot into ubuntu it is useful.

Also note that installing the win XP may boot only windows xp. So make a bootable disc of ubuntu before install win xp.

---

### Post by bodhi.zazen on 2012-04-14
> **callmemahavir said:**
> Format is a task which deletes all the data. 

Formatting alone will not delete data, the data is "easily" recovered.

To delete data you have to over write it, dd (all zeros), scrub, etc.

---

### Post by xyzzyman on 2012-04-14
> **callmemahavir said:**
> Answer to 1) Linux is a secure and virus free system.
Answer to 2) In win xp if you reinstall the OS reinstall of drivers required.


Format is a task which deletes all the data. Before doing anything you have to know the effect of it. First in WIN XP keep all the data safe by writing to CD or DVD and keep it safe. Because the CD or DVD is a read-only media, backup to it may not infected by virus. It is very important that boot record of ubuntu should be safe while reinstalling the win xp. And while installing the win xp ensure that ubuntu partition is not touched and not formatted. Also create a bootable disc for ubuntu partition (in CD-ROM) and keep it safe. If you cannot boot into ubuntu it is useful.

Also note that installing the win XP may boot only windows xp. So make a bootable disc of ubuntu before install win xp.

The data backup should be done on the linux install also. Even if you're working with just the windows partitions, you should never assume something could happen.

Also, it is not a good idea to have the mindset that "Linux is a secure and virus free system." You can say that Linux can be "more secure" than Windows XP, and no one will argue that, especially if XP hasn't had all it's service packs applied and updates done, but to always assume it's secure and virus free is as bad as having a "can't happen to me attitude" on something. Instead of repeating, I'll just link to the relevant wikipedia that summarizes: [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)

---

### Post by Jerry N on 2012-04-14
> **xyzzyman said:**
> Also, it is not a good idea to have the mindset that "Linux is a secure and virus free system." You can say that Linux can be "more secure" than Windows XP, and no one will argue that, especially if XP hasn't had all it's service packs applied and updates done, but to always assume it's secure and virus free is as bad as having a "can't happen to me attitude" on something. 

The Mac folks thought they were safe and secure too!  An estimated 600,000 Macs have been hit with the "Flashback" trojan.

Jerry

---

