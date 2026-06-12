---
title: "Optimize"
date: 2010-11-13
forum: General Help
---

### Post by ScottG89 on 2010-11-13
I recently installed Ubuntu on my computer and I'm trying to find any ways I can speed up boot up time and just overall performance. Also, do I have to do anything to take advantage of the 4 cores on an i7 processor. I saw something on a website about concurrency, but there were some risks with that so I didn't do it. 

Thank you,
Scott

---

### Post by lisati on 2010-11-13
*Thread moved to **General Help**.*

---

### Post by Frogs Hair on 2010-11-13
You could begin with Preferences> Startup Applications and remove what you don't use , but be sure it is not needed for normal operation of the computer. Welcome to the forums.

---

### Post by ScottG89 on 2010-11-16
Thank you, but I already did that. I'm just trying to find any other things I can do.

Thank you,
Scott

---

### Post by oldos2er on 2010-11-16
Hopefully you installed 64-bit Ubuntu. Are you using ext4 partitions? What kind of boot times are you experiencing?

---

### Post by windowsh8r on 2010-11-16
> **oldos2er said:**
> Hopefully you installed 64-bit Ubuntu. Are you using ext4 partitions? What kind of boot times are you experiencing?

Is there a noticeable difference between 64 bit and 32 bit Ubuntu?

---

### Post by davidvandoren on 2010-11-16
Your pc should boot under 20 seconds.
Why do you need it any faster? Are you rebooting your system all the time?

You can disable some bios settings such as on boot memory test. 
If you have grub you can change the grub option at boot from displaying instead 10 seconds only one second.

However if I were you I'd not temper too much with my system only to gain another second at boot. What's the use of that?

---

### Post by a-user on 2010-11-16
> **davidvandoren said:**
> Your pc should boot under 20 seconds.

ha, not even with my ssd. it did booted under 9 sec on first installation. but after switching from nuvou driver to the proprietary ones i know see text login shell after the battery checking messages, that holds for over 6 sec till gdm starts. and also the time for this login shell and after is slower.

in fact, my boot time is now 35 sec. remember, i am having a ssd and had under 9 sec boot time on vanilla fresh install.

p.s. i have no clue what exactly causes this long pause during boot.
p.p.s. the more or less the same thing happend with lucid before.

---

