---
title: "Resume from Suspend"
date: 2010-02-02
forum: General Help
---

### Post by code850 on 2010-02-02
Hi,

I have this suspend issue with my laptop, the problem as follow:

I can perfectly resume the system when I activate suspend to ram by clicking the logout icon in gnome panel.

In my gnome power-management i have 'suspend' selected if lid is closed.

Now if i close the lid the system suspend to ram perfectly. But I can not resume it. The screen is black/dead. If i press ctl+alt+f1  i can blindly log in to tty1 and reboot the system. 

I compared pm-suspend.log for both situations, and there is no difference at all. Any help will be appreciated. 

thnx,

---

### Post by keturidu on 2010-02-02
The same is here for me. I get black/blank screen on startup and when system enters black screen mode (i turned off all screensavers and suspends and hibernates but computer still is getting sleep after some time of doing nothing with it). I could go to console mode. Also, i'm sure it's something with gnome settings and particular this computer (acer 3002, SiS VGA) because i didn't notice such a problem with Linux Mint, also i got this "black screen" even while installing Ubuntu, i didn't get such a problem on my other computers with pretty much same install either.

additional info:

computer works again only after turn off/ turn on. Neither sudo reboot from terminal, neither ctrl+alt+del works (after restart blank screen again)

---

### Post by code850 on 2010-02-03
Ibidem suggested elsewere to take a look at  man pm-suspend. It seems to have interesting info.

---

