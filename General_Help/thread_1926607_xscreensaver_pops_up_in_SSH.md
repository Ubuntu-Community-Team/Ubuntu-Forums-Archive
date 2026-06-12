---
title: "xscreensaver pops up in SSH"
date: 2012-02-16
forum: General Help
---

### Post by netopalis45 on 2012-02-16
After installing xscreensaver the only way I could find to have it load at startup was to place a line in the .profile file. The problem with this is that I also use that computer as an SSH server and when I log into it a line to the order of "xscreesaver has started' and gives me some other information and it stays there as if it is running from the terminal. The only way to get out of this is to us ctrl^C. Is there any way of stopping this only for SSH connections?

---

### Post by Khayyam on 2012-02-16
> **netopalis45 said:**
> After installing xscreensaver the only way I could find to have it load at startup was to place a line in the .profile file. The problem with this is that I also use that computer as an SSH server and when I log into it a line to the order of "xscreesaver has started' and gives me some other information and it stays there as if it is running from the terminal. The only way to get out of this is to us ctrl^C. Is there any way of stopping this only for SSH connections?

The .profile is **only** for bash initialisation. For starting X11 applications you should use .xinitrc or whatever facility your GUI/Desktop provides to 'start at login'. Most Desktops have a control tool for manageing what gets started when you login, and a tool for enabling/disabling screensaver. So, your solution lies with whatever GUI your using, just don't use .profile as this is for bash configuration only.

HTH ... khay

---

### Post by netopalis45 on 2012-03-01
Turns out that didn't work and I didn't realise it until I had to reboot. What other file can control what starts at login like that?

---

### Post by Khayyam on 2012-03-01
It turns out I'm not psychic and so "that" could be anything .. please provide at least some information about what "that" might be.

best ... khay

---

### Post by seppalta on 2012-03-01
Autostart for Lubuntu is at 
/etc/xdg/lxsession/lubuntu/autostart .
For more information, see [http://douwil7.100webspace.net/linux/Tuning.html#16]("http://douwil7.100webspace.net/linux/Tuning.html#16").

---

### Post by netopalis45 on 2012-03-02
What I'm asking is if there is another file that I should be putting "xscreensaver &" into to make it start at login but not come up in SSH.

---

### Post by Khayyam on 2012-03-02
... and? I'm not going to start guessing what GUI you use, or why .xinitrc would be sourced by your shell, or why you don't use whatever facility, of whatever GUI, to enable/disable xscreensaver, or how your calling ssh, or if you enabled X11 forwarding, or use the -X switch in ssh ... I'll just use the usual psychic channels and commune witht the spirits of your computer to solve your problem.

best ... khay

---

### Post by netopalis45 on 2012-03-02
As far as I know .xinitrc is not sourced to the shell but it doesn't do anything at all. I use the Gnome window manager and I use the Nvidia Xserver configuration. I'm not really sure what else you want or if I can find anything else that will help.

---

### Post by Khayyam on 2012-03-02
OK, so Gnome (the last time I used it) provides a "Control Panel" where you can enable/disable and configure the screensaver, gnome will then start it when you login.

As for it starting when you ssh, this is because you set it to start from your .bash_profile ... remove that ... problem solved.

best ... khay

---

