---
title: "ddcprobe gives edidfail on 64 bit, working on 32 bit"
date: 2010-01-18
forum: General Help
---

### Post by XeroXer on 2010-01-18
Hi there!

I have been running the [COLOR="Gray"]32 bit[/COLOR] version of [COLOR="Gray"]9.10[/COLOR] since it made stable release.
I have a [COLOR="Gray"]Dell Vostro 1710[/COLOR] and while on [COLOR="Gray"]9.04[/COLOR] I tried running [COLOR="Gray"]64 bit[/COLOR].
Found it to be much to "buggy" to be used in my work and went back to [COLOR="Gray"]32 bit[/COLOR].

This weekend I read a few threads saying that the [COLOR="Gray"]64 bit[/COLOR] version of [COLOR="Gray"]9.10[/COLOR] was great.
Tried installing it and all the problems I had with the [COLOR="Gray"]9.04[/COLOR] version are gone and it works great.
Apart from one irritating problem.

I use three different mouse, keyboard and monitor setups. One at work, one at home and one when out and about.
In my [COLOR="Gray"]32 bit 9.10[/COLOR] I used [COLOR="Gray"]ddcprobe[/COLOR] [COLOR="Silver"](xresprobe)[/COLOR] during bootup to sense which (if any) monitor was connected based on [COLOR="Gray"]edid[/COLOR], then the script copied one of the files [COLOR="Gray"]xorg-home.conf[/COLOR], [COLOR="Gray"]xorg-work.conf[/COLOR] or [COLOR="Gray"]xorg-no.conf[/COLOR] onto the [COLOR="Gray"]xorg.conf[/COLOR] so that setup was used.

My problem now is that every time I run [COLOR="Gray"]ddcprobe[/COLOR] I get an [COLOR="Gray"]edidfail[/COLOR] error, so the [COLOR="Gray"]-no[/COLOR] file is moved.
Does anyone know of a solution, or maybe another way to detect the monitor and fix my setups.

---

### Post by chichilalescu on 2010-02-25
I'd also like to have a similar setup, and I have the same problem. So bump.
In this thread [http://ubuntuforums.org/showthread.php?p=2510689](http://ubuntuforums.org/showthread.php?p=2510689) there's someone saying that they can use dmesg for detecting a monitor. I didn't succeed in finding anything relevant to grep in my dmesg...

---

