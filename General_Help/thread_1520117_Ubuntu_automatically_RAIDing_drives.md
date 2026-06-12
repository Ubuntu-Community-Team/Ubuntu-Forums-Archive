---
title: "Ubuntu automatically RAIDing drives"
date: 2010-06-29
forum: General Help
---

### Post by PPoppinfresh on 2010-06-29
Hi Everyone

After much procrastination and fustration i have finally got around to installing Ubuntu, Windows XP and Windows 7 on a 3 way boot on my main system.

I have 4 hard drives 1x1000gb, 1x1500gb, 2x320gb.

All operating systems are installed on a single physical 320gb drive in 4 partitions (xp, 7, ubuntu and swap drive). To protect all my data, i moved everything onto the other 3 drives and unplugged them during installation of the 3 operating systems. Everything boots and works fine when 1x320, the 1000gb and the 1500gb are plugged in. BUT

When i plug the 2nd 320gb in, windows 7 and xp still boot fine, but upon booting into ubuntu the system just freezes at the ubuntu loading screen. Booting into the live version of ubuntu of the install disk shows that ubuntu is recognising these 2 drives as 1x320, 1x320, and 1x598gb drive. This leads me to belive that when ubuntu is loading of the single 320 drive its fine, but when the other one is plugged in its trying to do some automatic raid Spassiness which it cant do cause the other 320 has nothing on it.

I hope this makes my problem clear, any help you can give would be great! Ive tried doing a bit of a search but cant find anything obvious, this is the first time ive installed linux so try and make it easy!

Thanks

---

### Post by ronparent on 2010-06-29
If for some reason the drive had been used as a raid (fakeraid), meta data was left on a drive. That should be erased. Meanwhile you should be able to boot by editing the boot line and adding the parameter 'nodmraid' to the end of the boot line.

---

