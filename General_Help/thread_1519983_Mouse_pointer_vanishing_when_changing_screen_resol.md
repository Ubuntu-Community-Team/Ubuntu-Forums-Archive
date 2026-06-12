---
title: "Mouse pointer vanishing when changing screen resolution"
date: 2010-06-28
forum: General Help
---

### Post by Velvet Ghost on 2010-06-28
I've installed Ubuntu 10.04 on an old PC with an Intel 845 series motherboard, using an onboard graphics solution. By default, it boots with an 800x600 screen resolution. When I change the resolution to 1024x768, the resolution switches perfectly, but the mouse pointer disappears. The mouse can still be USED, but I have to 'guess' where the pointer is. The only way I have found to rectify the situation is to reboot, upon which the resolution returns to 800x600 again as well. Kubuntu 10.04 suffers from the same problem, only in Kubuntu the mouse pointer reappears when the resolution switches back to 800x600, so I don't need to reboot. Does anyone know what's wrong? Thanks.

---

### Post by Velvet Ghost on 2010-06-29
Does nobody know of a solution to this? :(

---

### Post by Velvet Ghost on 2010-06-30
Well, thanks for the help everyone. :) I just discovered that the problem does not occur in Xubuntu. I'll stick to that for now.

---

### Post by Ixtao on 2010-08-09
Strange problem. I get it when I want to change to external screen on my Toshiba Libretto U100 with intel 855GM graphic chip. I have this at least since Karmic. Now I'm using kernel  2.6.35-v9patch1-generic because of stability issues with normal kernel + KMS and the problem persisted even on internal screen after a reboot! I tried putting in the line 'Option        "Simultaneous"        "false"' I found [here]("http://www.hpminiguide.com/forum/other-linux-distributions/2164-invisible-mouse-cursor-external-monitor-ubuntu-9-04-a.html") into an xorg.conf file but I'm not sure how to apply graphic driver options when using KMS..

---

### Post by TGCLEAR on 2011-04-23
Ya I've been having the same problem for months now I updated to 11.04 beta the other day and it still does the same thing, if anyone has a fix I'd love to hear it too. Thanks guys.

Oh ya I don't know if this works for you but if i type a command in the terminal It usually starts up so i just do that every time I log in.

---

