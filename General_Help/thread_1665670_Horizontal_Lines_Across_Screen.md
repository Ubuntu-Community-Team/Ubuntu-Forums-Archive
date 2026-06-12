---
title: "Horizontal Lines Across Screen"
date: 2011-01-12
forum: General Help
---

### Post by Serendipitous Dinosaur on 2011-01-12
Hi, I have recently bought a new computer, having used Ubuntu in dual boot with XP on my last one. When I tried to install Ubuntu (10.10) on my new computer however, the screen became covered with horizontal lines. Whenever something changed on the screen (like the mouse moving), more lines appeared. I could make certain controls appear above the lines by clicking them.

[IMG]http://omgwac.com/uploads/screenshotsmaller.png[/IMG]

I managed to install Ubuntu, hoping that I might find a fix after it was on my computer. I can login in Failsafe Graphics mode, but I get the message 'Your screen graphics card and input device settings could not be detected correctly'.

My graphics card seems to be rather old, and there's only an old driver on the manufacturer's website (Matrox). When I try to install it, it says:
```
ERROR: The X server drivers included in this installation package do not support the current version of your X server.

```

The release notes for the driver ([link]("ftp://ftp.matrox.com/pub/mga/archive/linux/2006/readme-mga-4.4.0.txt")) says it will only support X.org versions 6.7.0, 6.8.0, 6.8.1, 6.8.2, 6.9.0 and 7.0.0.

What can I do?

```
sam@Pythagoras:~$ lspci -nn | grep VGA
11:00.0 VGA compatible controller [0300]: Matrox Graphics, Inc. MGA G200 AGP [102b:0521] (rev 03)
```

Thanks for your help.

---

### Post by Serendipitous Dinosaur on 2011-01-15
So what should I do?

---

