---
title: "Distorted login screen after driver upgrade"
date: 2006-02-16
forum: General Help
---

### Post by Momo88 on 2006-02-16
Hi,

I need help with the following problem: I just upgraded the graphic drivers for my (Elsa Erazer II) Riva TNT graphics card (with nvidia legacy drivers). Everything works fine after I get passed the login screen. 

My problem is the login screen which is displayed triple and completely distorted. I can hardly make out where I have to enter my name and password. After that everything works fine.

What I found out is that the login screen is displayed with a resolution of 640 x 400, which is kind of odd. Unfortunately I have no idea where I could change that to 640 x 480. What could be the problem? Any ideas?

My xorg.conf file seems ok, at least it doesn't include any reference to a resolution of 640x400.

Hope someone can point me in the right direction...

Thanxs,
Momo88

---

### Post by Momo88 on 2006-02-17
Hi,

I tried reconfiguring my xserver using

sudo dpkg-reconfigure xserver-xorg

to no avail. When I start my computer and get to the login screen it is displayed with a screen resolution of 640 x 400(!), the display is flickering and I see the screen three times with thick black bars in between.

Are there any config files that tell the OS what resolution / settings to use before I log in? After login everything works fine.

Any ideas?

Thanx,
Momo88

---

