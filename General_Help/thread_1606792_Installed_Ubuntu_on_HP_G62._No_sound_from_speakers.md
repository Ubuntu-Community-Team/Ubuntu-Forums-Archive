---
title: "Installed Ubuntu on HP G62. No sound from speakers, help?"
date: 2010-10-26
forum: General Help
---

### Post by Takkak on 2010-10-26
Installed Ubuntu 10.04 on my HP laptop. I have installed Ubuntu on 2 of my computers with no problems whatsoever, but this laptop is just a problem. I already had to install the driver for my wireless card, and now I noticed there are no sounds coming from the speakers, but if I plug headphones into the headphone jack, there is sound.

Any help would be greatly appreciated.

---

### Post by Takkak on 2010-10-27
Okay, so I fixed it by updating ALSA.

---

### Post by hanciong on 2011-02-02
I have the same problem like you. after updating ALSA, the sound works..... for a while. After some other update (from update manager), the sound doesn't work again. why is this? and then if I run firefox, other video programs seem don't work (for example like VLC or totem). The movie just doesnt play. In order for them to work, I must close firefox first. how to fix this? Thanx a lot

---

### Post by Walpy on 2011-02-28
> **Takkak said:**
> Installed Ubuntu 10.04 on my HP laptop. I have installed Ubuntu on 2 of my computers with no problems whatsoever, but this laptop is just a problem. I already had to install the driver for my wireless card, and now I noticed there are no sounds coming from the speakers, but if I plug headphones into the headphone jack, there is sound.

Any help would be greatly appreciated.

It was the same for me. Had to install wireless card and had problems with my sound.

I installed Ubuntu 10.04 on my HP G62.

This did the thing for me

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

Should be working

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

---

### Post by Skorzen on 2011-03-20
> **Walpy said:**
> It was the same for me. Had to install wireless card and had problems with my sound.

I installed Ubuntu 10.04 on my HP G62.

This did the thing for me

```

~$ sudo aptitude update
~$ sudo aptitude install linux-backports-modules-alsa-lucid-generic

```and reboot!

Should be working

(found the solution here: [http://www.uluga.ubuntuforums.org/showthread.php?t=1570060](http://www.uluga.ubuntuforums.org/showthread.php?t=1570060))

This solution works on a HP G62-G70SP running Ubuntu 10.04 LTS 64-bit.

bruno@g62:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)

Thanks, mate.

---

