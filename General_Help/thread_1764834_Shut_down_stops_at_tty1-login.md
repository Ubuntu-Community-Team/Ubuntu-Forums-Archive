---
title: "Shut down stops at tty1-login"
date: 2011-05-22
forum: General Help
---

### Post by wonko on 2011-05-22
As the title says - when I try to shut down from the kde or gnome menu, the desktop exits but the computer won't shut completely down - it just gives me the login-prompt for the first virtual-terminal. Running "sudo shutdown -h now" from terminal (either Konsole, gnome-terminal or tty1) works fine. Same story when I try to reboot.

I recently upgraded my Kubuntu install to 11.04 and also installed gnome-desktop, so probably one of these actions have caused this problem, but I don't know which one of them. My first guess is the problem lies in my kdm-config but I can't figure out where or what to look for in the logs. Anyone got any ideas what I can check?

---

