---
title: "killed gnome-screensaver, now no mouse/keyboard input"
date: 2009-08-28
forum: General Help
---

### Post by Victor Liu on 2009-08-28
I was upgrading 8.10 to 9.04 when the screensaver kicked in, and wouldn't go away. I SSH'd into the machine and did a ```
killall gnome-screensaver
``` which worked, so now I can see what's on screen (It's a dialog that asks "Replace the customized configuration file '/etc/vim/vimrc.tiny'?"). However, there is no cursor and there is no keyboard input. I should have google'd how to kill the screensaver gracefully before doing the killall, but now that I've done it, is there any way to recover from the situation? I really just want to restore user input, or somehow press the buttons on the foreground window through the command line. I tried VNC but, alas, the server was not set up, and I cannot use apt-get because the upgrade process holds the apt lock.

---

### Post by P4man on 2009-08-28
its not killing the screensaver that killed your input, I bet the input was killed and therefore the screensaver didnt stop when you tried.


If all else fails, reboot and run  "sudo dpkg --configure -a". May need to do that in a recovery terminal.

---

