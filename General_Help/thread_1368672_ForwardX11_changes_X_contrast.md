---
title: "ForwardX11 changes X contrast"
date: 2009-12-30
forum: General Help
---

### Post by duane-tech on 2009-12-30
When I run ssh, the contract on my laptop goes way high (everything gets very light, changing the brightness only darkens everything equally).
Commenting out ForwardX11 yes in ~/.ssh/config stops this behaviour, but then I can't run X apps.

Stopping the ssh program doesn't fix the problem, Only logging out and restarting X will restore the contrast.

Does anyone know what's happening?

I have Kubuntu Hardy:
ssh            1:4.7p1-8ubunt
x11-common     1:7.3+10ubuntu

---

### Post by duane-tech on 2010-02-13
To answer my own question and anybody else who had this problem:
The problem was caused by the monica utility on the remote computer. This program is a frontend to xgamma (part of xorg). It uses the familiar grey box with lines to adjust gamma correction for X. 

How it screws me up:
It adds a .monicarc command to .bash_profile which in turn has a command similar to :
xgamma -quiet -rgamma 2.2 -ggamma 2.2 -bgamma 2.2
which is called during ssh login. X11Forward allows the change to happen. 

Fix:
Temporarily, I just executed "xgamma -gamma 1"
Permanently, I removed the .monicarc reference from .bash_profile, deleted .monicarc, and removed the monica utility. I don't need it if it can screw me up.

---

