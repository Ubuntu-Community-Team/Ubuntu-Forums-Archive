---
title: "apt not caching packages after reboot"
date: 2006-02-25
forum: General Help
---

### Post by sour on 2006-02-25
Having an issue with apt in that after a reboot, apt wants to redownload all packages/sources all over again.  I dont remember this being default behaviour, however I used to be on a very high speed connection so I probably wouldnt have noticed/cared!

.. but now Im on dial up :cry: and every time I want to install a package or apt-get update after a reboot it forces me to download 5 megs or so of packages, which makes me quite sad.  If I try to apt-get install or start synaptic it spits out errors about my souces. It works fine ie will only dowload a few updates the next time I apt-get update if I havent rebooted.

Something to note is that I originally mucked around with bringing packages home from my work comp to get my fresh intall up to date, so maybe its likely I overwrote something in /etc/apt that is causing this odd behaviour?

---

