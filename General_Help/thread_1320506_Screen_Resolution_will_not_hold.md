---
title: "Screen Resolution will not hold"
date: 2009-11-09
forum: General Help
---

### Post by mincewords on 2009-11-09
New to Linux and Ubuntu 9. After installation the screen resolution only had two choices, low and lower. After two restarts I was able to select from about 12 different resolutions, found one that worked and looked great. After restarting the next day the resolution defaulted back to the original and now I only have the two choices again? #-oAny help would be appreciated.
 
Thanks.

---

### Post by P4man on 2009-11-09
Hi and welcome,

can you give some information please? Which videocard and monitor do you have, which (if any) drivers are you using, what app do you use to change the resolution...? I assume you are using ubuntu 9.10 but it would be nice to know that for sure as well :)

---

### Post by mincewords on 2009-11-10
[FONT=Arial][SIZE=3]Ubuntu 9.10
Monitor: Hyundai Model X224W
Integrated video, no separate card or driver
System/Preferences/Display

Thank you for the help.

After I start the pc I am given 2 selections to choose from, 800x600 and 640x1050. If I select the latter and restart I then have 12 selections. The best is 1680x1050. It looks great until I shut down again. When I shut down again it defaults back to the original 2 selections, forcing me to start the process all over again.[/SIZE][/FONT]

---

### Post by P4man on 2009-11-10
Is that an intel integrated video (or ATI, SiS, nVidia,..) ?
Also can you post  your xorg.conf file? To obtain (and later edit it) press alt F2 and then type (or copy paste):

```
gksudo gedit /etc/[COLOR="Red"]X[/COLOR]11/xorg.conf

```
Please note the red X is upper-case.

---

