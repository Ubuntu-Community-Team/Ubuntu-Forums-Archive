---
title: "Radeon Mobility 7500 - Thinkpad T42"
date: 2006-05-19
forum: General Help
---

### Post by reckless2k2 on 2006-05-19
Has anyone had success getting 3d acceleration working with the Radeon Mobility 7500? I'd like to take advantage of XGL.

---

### Post by theraven1982 on 2006-05-31
This is also something i'd like to know; but it doesn't need to be the live-cd. 

With the upcoming release, i also want to take this one for a spin, but i'd like to have the compiz/xgl effects ... So is there anyone who tried it?
I'm not unfamiliar with linux (but mostly a freebsd person), but i'd like to get it working without too much hassle.

Anyone?

---

### Post by gborzi on 2006-06-06
I was able to get xgl working on my compaq evo n610c which has a Radeon mobility 7500. The main problem is in finding the right configuration for xorg. Once you have found this, you can follow the [wiki guide]("https://wiki.ubuntu.com/CompositeManager/Xgl?highlight=%28xgl%29") to get xgl working. I have found the right configuration booting the laptop with kororaa 0.2 and copying the xorg.conf of the live distribution. Later I changed only the fonts. My xorg configuration is in attachment.

---

