---
title: "PHP displays blank pages in any browser."
date: 2011-01-11
forum: General Help
---

### Post by TombKing on 2011-01-11
Writing this from the windows box since my problem is php pages display blank in any web browser on my kids computer running 10.10. and the forums are php based.

All the threads I have seen are from people with a local apache server and php server running. This is just a workstation and nothing server like installed (well not apache or php anyway)so everything I have found tells me to check config files that of course are not there.

Anyway since his favorite web game is php based he is currently a bit upset. It did work when I initially installed 10.10 on a full flatten and reload. It seems within the last month or so is when it stopped working.

---

### Post by cipherboy_loc on 2011-01-11
Check the packages that were installed, removed, and upgraded around the time that it stopped working. Also, what window manager are you using? I run Ubuntu 10.10 with 11.04's kernel, and in both of my browsers (Firefox and Google Chromium), all .php pages load properly.


Cipherboy

---

### Post by TombKing on 2011-01-11
After some more hunting it appears to be Dansguardian that is doing it.

[https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475](https://bugs.launchpad.net/ubuntu/+source/dansguardian/+bug/474475)

Now to find a different filtering package for the 9 year old unless anyone here does have a fix.
edit : Or just let him suffer. Not like he really needs the distraction.

---

