---
title: "Shutdown, Restart, and Logout buttons will not do anything"
date: 2010-11-05
forum: General Help
---

### Post by tak1150 on 2010-11-05
On two of my machines that have Ubuntu 10.10 on them, I cannot shut down, restart or log out by pressing the "power button" on Gnome panel.
I can not even do "Alt + Ctl + Backspace" either.
However, I can shutdown or restart by:
> sudo shutdown -h now
sudo shutdown -r now

---

### Post by pricetech on 2010-11-05
System - Preferences - Keyboard
Layouts Tab
Look for "Key sequence to kill the X server" to turn on Ctrl + Alt + backspace.

Any chance your connected remotely when the buttons don't work ??

---

### Post by tak1150 on 2010-11-05
Thanks, Pricetech.
Now at least I have "Ctl+Alt+Bcksps"
No, even when I am not logged into the machine remotely, I can't log out or shutdown.
I've actually confirmed this behavior on a 3rd machine too now :(

---

### Post by Zurd on 2010-11-10
Same problems here, I click either Shutdown, restart or log out then I have a dialog box opening saying "Are you sure you want to close all programs and restart the computer?" and I click Restart and nothing happens.

I just installed Ubuntu 10.10, it's a clean install and sudo reboot in console works fine.

---

### Post by Zurd on 2010-11-10
Well I already found the problem, it's the openoffice quickstarter.

[https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027]("https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/562027")

---

