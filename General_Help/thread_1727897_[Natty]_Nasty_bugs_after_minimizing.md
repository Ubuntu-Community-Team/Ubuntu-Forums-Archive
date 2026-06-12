---
title: "[Natty] Nasty bugs after minimizing"
date: 2011-04-13
forum: General Help
---

### Post by GTMoraes on 2011-04-13
Hey, I'm on the Ubuntu Natty Narwhal and on a netbook. Hardware details are given on the signature.

Well, I'm trying to learn how to use Unity, but this bug is freaking me out. When I minimize any window, the menus are kept on the top bar 'till I click on anything else (or on the desktop), also I can't recover the window till I click on anything else (It's like it haven't been minimized, just hidden).
After restoring the window, if I try to maximize, the window borders will be maximized, but the actual window won't. I'll be attaching pictures for better understanding.
Also, if I try to un-maximize, the Close-Minimize-Maximize and the menus will be unavailable (Visible, but like they didn't exist, cant even move the window around)

If I maximize and THEN minimize, then it goes crazy. When I recover the screen, it will look ok, but if I un-maximize, there'll be a huge ugly black border around the window that follows it, no matter where I push it around.

Couldn't find anything related. I'm using the Natty Beta 1 (installed yesterday thru updates). I'm also using the latest Intel drivers (from intellinuxgraphics.org). Everything else works fine.

Hope there's a fix out there. Should I fill a bug report?
Thanks

EDIT: Forgot the pictures. There are legends built-in.

[Print 1]("http://i54.tinypic.com/34eum43.png")
[Print 2]("http://i53.tinypic.com/rku5pw.png")
[Print 3]("http://i52.tinypic.com/34g5zs3.png")
[Print4]("http://i54.tinypic.com/13zqqus.png")

1366x768 resolution pictures. Please take a look

Thanks
[LEFT]__________________________
[/LEFT]

[CENTER]**Media Center PC**: AMD Athlon 64 X2 5000 | 2GB DDR2 800 | ATi Radeon HD3200 | 320GB HDD SATA II | Realtek ALC889A | Sony Bravia 46" 120Hz | Ubuntu Maverick
**Netbook**: Acer Aspire 1410-2287 ~ Intel Celeron ULV 723 1.2GHz | 2GB DDR2 800 | 250GB HDD | Intel 4500mHD | 11,3" HD LED | 6:30hrs Battery | Ubuntu Natty
[IMG]http://i53.tinypic.com/2d6se9l.png[/IMG]
[SIZE="1"]**Ubuntu Powered.**[/SIZE][/CENTER]

---

### Post by GTMoraes on 2011-04-13
I discovered what was it.

the "Keep previews of minimized windows" on "Workaround" plugin on CompizConfig was bugging everything up. Disabling it fixes it like magic.

Problem solved. Thank god Ubuntu is easy.

---

