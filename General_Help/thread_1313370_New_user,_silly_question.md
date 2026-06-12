---
title: "New user, silly question"
date: 2009-11-03
forum: General Help
---

### Post by Dadof4 on 2009-11-03
Was running 9.04 for about a month when 9.10 was released. Did a fresh in stall and absolutely love it, it went flawlessly. My only gripe right now is that my Num Lock key keeps showing that it is on when I'm at the log in screen but it isn't. How on earth do I get it to come on after boot and in the log on screen? I know I can turn it on manually but I'm so used to it coming on at boot that this is becoming an annoyance, albeit a very, very small one. :oops:

---

### Post by Joe of loath on 2009-11-03
Might be a BIOS issue? Try changing the 'num lock on power on' setting from on to off or vice versa.

---

### Post by harry_i_c on 2009-11-03
To enable the NumLock key on startup, follow the instructions for 'Enabling NumLock in GDM' on the link below.

[https://help.ubuntu.com/community/NumLock]("https://help.ubuntu.com/community/NumLock")

For it to be on after login, go to System > Preferences > Keyboard.
That will open your Keyboard Preferences, then click the Layouts tab then the Layout Options button.
Next in the window that pops up, click 'Miscellaneous compatibility options' & select the 'Default numeric keypad keys' option.

---

### Post by dcstar on 2009-11-03
> **Dadof4 said:**
> Was running 9.04 for about a month when 9.10 was released. Did a fresh in stall and absolutely love it, it went flawlessly. My only gripe right now is that my Num Lock key keeps showing that it is on when I'm at the log in screen but it isn't. How on earth do I get it to come on after boot and in the log on screen? I know I can turn it on manually but I'm so used to it coming on at boot that this is becoming an annoyance, albeit a very, very small one. :oops:

There is a package called **numlockx** which you may want to install, but AFAIK your system should already "remember" what state the key was left in when the system was last shut down.

---

