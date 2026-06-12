---
title: "ubuntu just won't login anymore"
date: 2010-07-21
forum: General Help
---

### Post by bolenjx1 on 2010-07-21
I've been using ubuntu for months now and it was really frustrating dealing with hardware issues. Just when I thought everything's going ok, today, when I boot up, I am greeted by the following error:

"Ubuntu is running in low-graphics mode your screen, graphics card, and input device settings could not be detected correctly, you will need to configure these yourself."

Selecting "run in low graphics mode for one session" doesn't work. It looks like it's loading something but nothing. I tried various options like "reconfigure X" and none of them works.

I can login the console find though.

Anyone have any idea on how to fix this? I have a backup from a month ago but I've changed a lot since then.

Ubuntu 10.04
HP G61 laptop
ATI Radeon HD 4200

---

### Post by robsoles on 2010-07-22
IMHO you want to pull your existing /etc/X11/xorg.conf file out of the way and try booting into GUI with nothing in place for it - if you make it to graphical desktop then you can use your graphics controller's configuration utility under 'System'->'Administration' to create a new one - I'm on a nvidia based machine right now and I can't refer to an ATI for about another 12 hours but it is best to start the configuration applet/program with gksudo so that it has admin privileges with which to write a new xorg.conf file.

To try this login to your console and type into terminal prompt:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf-failed-20100722
```
(I reverse note today's date where I am onto the end of files I do this sort of thing to so as to have an indicator what I did when)

Then restart and see if you can get a GUI/desktop session after that (I expect you will) - open terminal in it and type in
```
gksudo gnome-display-properties
```
and if your video card has a proprietary driver or other reason to offer you a different configuration program then it will be offered to you - if you are asked a question before being offered controls for your graphics then select 'yes'.

Find option to save settings/xorg.conf and select it - restart, post back how good or bad that went for you at any step.

---

