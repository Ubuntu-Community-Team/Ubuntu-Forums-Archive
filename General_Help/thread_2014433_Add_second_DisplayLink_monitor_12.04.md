---
title: "Add second DisplayLink monitor 12.04"
date: 2012-07-01
forum: General Help
---

### Post by vpak on 2012-07-01
I installed 12.04 using wubi on an Acer notebook.

With the laptop lid closed my main external monitor works fine via HDMI; the second monitor shows only a bright green color.

After some googling I installed the DisplayLink drivers but this caused no changes. Next I created a file as described [here]("http://ubuntuforums.org/showthread.php?t=1870620")...after a reboot I now have a terminal in the HDMI screen and still a bright green screen on the DisplayLink monitor.

I've used Ubuntu on and off many times over the years and I'm surprised to find that this doesn't work out of the box. I read somewhere that Fedora 17 handles DisplayLink well - I don't mind switching distros (or going back to Windows) if necessary but I'd sure like to think there's a not-too-difficult fix for this in Ubuntu. Thanks.

---

### Post by DorianX on 2012-10-18
I'm having the same issue, but I did discover one thing: if I run mplayer with "-vo fbdev:/dev/fb1", mplayer's output does display on the displaylink screen. So linux can definately talk to the device, it's just that for wehatever reason, X isn;t playing with it.

ETA: 
Actually, I was able to get it working by adding some config info in /usr/share/X11/xorg.conf.d, but then it became the *only* monitor that worked. I tried writing a full Xorg.conf that described both my primary monitor and the displaylink device, but it just ignored the section describing the displaylink.

---

### Post by maino on 2012-12-14
I am having the same issues with a green screen, and Googling away without concrete answers.
Anyone have more information?

[Edit] I am using 12.04, not 8.04 - I can't edit my profile at this time because of my bean count.

---

