---
title: "Login screen on wrong monitor!"
date: 2011-03-06
forum: General Help
---

### Post by chazwoza on 2011-03-06
Hi All,

I've searched through the forums, and seen lots of posts to this, but nothing seems to work.

I have two ubuntu 10.10 x64 running on thinkpad T410 with the intel integrated graphics card. I have a 17 inch dell monitor plugged in and configured on the right hand side. The laptop screen is the primary monitor I believe.

Couple of annoying problems. Notifications (like chat, wifi etc) show up on the secondary monitor.

But the main annoying one is that the GDM login screen always shows up on the secondary monitor. To save power I don't normally always have the secondary monitor on.

Can anyone help with ideas how to fix this? 

Cheers,
Chaz

---

### Post by scouser73 on 2011-03-06
You'll need to do this as root, so follow these instructions.

**1** - Paste this command into terminal: **gksudo nvidia-settings**

**2** - Click on **X Server Display Configuration**

**3** - Click on the monitor that you wish to make the main monitor

**4** - Check the box stating **Make This The Primary Display For The X Screen**

**5** - Click **Apply**

**6** - Click **Save To X Configuration File** & press **Quit**

***You have now set the login screen to appear on your desired monitor, this will be your main monitor, to change it, just follow the instructions again but this time choosing the other monitor.***

---

### Post by chazwoza on 2011-03-06
Hi,

Thanks for the reply. I'm not using a nvidia card, its an intel one, so I dont have that utility (nvidia-settings).

Any ideas for an intel card?

---

### Post by scouser73 on 2011-03-06
> **chazwoza said:**
> Hi,

Thanks for the reply. I'm not using a nvidia card, its an intel one, so I dont have that utility (nvidia-settings).

Any ideas for an intel card?

Ahh sorry mate, I should have looked at the post more carefully.

---

### Post by Krytarik on 2011-03-06
Try following this guide to use "xrandr" with the respective options at startup of GDM:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Greetings.

---

