---
title: "Ubuntu 12.04 in VirtualBox - access chrome web store in chromium"
date: 2012-05-06
forum: General Help
---

### Post by TE7 on 2012-05-06
I can't search the chrome web store in Chromium or Chrome. When I try to click in the search field nothing happens. I can't search the extensions. Using Ubuntu 12.04 (Unity) in VirtualBox 4.14. Any help appreciated.

---

### Post by KJ KJ KJ on 2012-05-06
Annoying isn't it? I'm evaluating 12.04 under VirtualBox 4.14 prior to upgrading from 10.10. I've got 4CPUs and 128M video memory configuration on a Thinkpad x121e.

Disable 3D acceleration in VirtualBox and you can get into the Web Store and install extensions.

---

### Post by TE7 on 2012-05-06
Disabling 3D acceleration did work. Thanks. I was also having the same problem in Linux Mint 12 and Linux Mint 12 LXDE (both 32 bit) in VirtualBox. Will try those next. Will report back.

Edit: Disabling 3D acceleration worked for both Linux Mint guests, although I can't get the Cinnamon desktop in Linux Mint 12 without 3D acceleration.

---

### Post by KJ KJ KJ on 2012-05-07
[http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/)

```
google-chrome --blacklist-accelerated-compositing
```

seems to do the trick with VirtualBox 3D acceleration re-enabled.

I've bound the command to a keyboard shortcut until I can figure out an elegant way to tweak the launcher icons.

---

### Post by TE7 on 2012-05-07
Have you tried the following:

Create desktop launchers (for those who like desktop icons, in the Gnome Classic desktop, for example):

[http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html](http://www.ubuntugeek.com/how-to-create-desktop-launchers-in-ubuntu-11-10oneiric.html)

To make things quicker,

- You can open gedit, enter your command, and save it to the Desktop.

- Then right click on the saved file, choose Properties, then Permissions,and check "Allow executing file as program".

- Then just double click, and choose Run In Terminal, and enter your password.

Tom

---

