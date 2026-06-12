---
title: "Fast boot with Karmic, what's the secret?"
date: 2009-11-03
forum: General Help
---

### Post by BarisBlaq on 2009-11-03
Hiyas all,

I'm having worse boot up times with Karmic compared to Jaunty. As far as I can see from the forums, there are others like me, and there are also who have improved times with the 9.10

I'm still new to linux, so I have a series of questions. Some of them are just wild guesses, so they might be funny, be warned =P

1. I have a laptop. From the posts it seems boot times mostly improved for desktops (Karmic vs Jaunty) and went worse for laptops. Do you feel/experience the same? Is there some explanation if that is true?

2. I have a core 2 duo. Does that perform worse than a single core cpu during boot? Also, I had read changing "CONCURRENCY=none" in /etc/init.d/rc to "CONCURRENCY=shell" makes use of the dual core, is it true?

3. Profiling the kernel, does it still work? It had made Jaunty boot faster, but with Karmic doesn't seem to improve anything. Due to Grub2 maybe?

(btw, those last 2 points were from here: [http://www.linuxlinks.com/article/20090927065957648/UbuntuTips-Booting-Part3.html](http://www.linuxlinks.com/article/20090927065957648/UbuntuTips-Booting-Part3.html))

4. I have a data partition and the OS partition (and swap), and no other OS. My data were ext3, and it's kind of hard to back them up and upgrade to ext4 right now, and I thought having data ext3 and OS ext4 would slow things down, so I installed Karmic with ext3. Would going ext4 speed boot (keeping data partition ext3)? Would chossing both as ext4 improve things?

5. Is there a detailed bootchart tutorial you can point me to? I couldn't find any detailed documentation, and the graph is kind of confusing for me.

6. I could not get rid of the Grub2 menu, I read it's some bug, and also that it's related to $recordfail not resetting. So I changed the $recordfail loop in the bottom of /etc/grub.d/00_header (a suggestion from a launchpad thread I can't find now), and the hidden menu works now. Is it safe? Are there any other (better) fixes you can give?

7. In general, are there any tips you would recommend for a better boot time?

Thanks for any feedback in advance. I hope I didn't sound too lame =))

---

### Post by bostonaholic on 2009-11-03
I have a Core 2 Duo as well and I noticed an increase in boot time when upgrading from 9.04 to 9.10.  I'd like to know some of these tips as well.

---

### Post by BarisBlaq on 2009-11-03
Shameless self bump.. Anyone?

---

