---
title: "Video reset by Ubuntu"
date: 2006-04-02
forum: General Help
---

### Post by spidey on 2006-04-02
First, I have to say that I am very impressed by Ubuntu so far!  I've been going between Red Hat, Madriva (back when it was Mandrake), & Slackware; however, I could never settle on one or the other, none of them met my needs.  Ubuntu is the one I'm going to stay with... thank you for putting together such an awesome system!

Now, with that said: I have an integrated Intel 82865G (64MB) card on a Dell Optiplex 270.  I have been running Ubuntu for over a week, and it was perfect; the default settings accounted for all the card's capabilities.  However, just about 30 minutes ago, I was multi-tasking and the screen went blank.  Ubuntu rebooted and came back up in 640x480 with minimal colors & at 60Hz refresh rate (my eyes are hurting now, LOL).

I've checked the xorg.conf file and everything seems to be in order there.  I checked Ubuntu's <<Applications >System Tools>System Information (Hard Info)>> and Ubuntu recognizes the hardware properly.  But, all I have for a choice of screen resolution is 640x480.

Anybody experience this?  Also, what does Ubuntu use for video configuration files?  I'm having a slight learning curve adjusting to the configuration setup of a Debian-based system.

Thank you in advance :)

---

### Post by tseliot on 2006-04-02
That's weird...

Can you try this guide?
[HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution")


Ubuntu uses the xorg.conf as any other distro.

---

### Post by spidey on 2006-04-02
Thanks for the quick reply, I'll give it a shot & be right back, I hope.

---

### Post by spidey on 2006-04-02
Okay, that definitely got me in the right direction.  Thank you!

The problem was that, on auto-detection, Ubuntu allowed for a monitor refresh rate that was outside the manufacter's settings; it probably worked until I loaded it down with enough to cause it to go 'boink.'

After I followed that link, I tried to have my video & monitor auto-detect, which it did, but, the incorrect monitor parameters were passed to the xorg.conf file.  I manually set the parameters, rebooted & it worked!

:mrgreen:

---

