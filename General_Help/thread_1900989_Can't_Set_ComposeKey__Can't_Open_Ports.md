---
title: "Can't Set ComposeKey || Can't Open Ports"
date: 2011-12-27
forum: General Help
---

### Post by kreaven on 2011-12-27
**Read post #3 for current info.**

[COLOR="Silver"]Hey, I've been experimenting with Linux for the past week and a few. I've gone through: Mint 12 (Gnome), Mint 11 (LXDE), Mint 9 (Gnome), Mint Debian (Xfce), MeeGo and don't remember what else. I prefer Ubuntu-based distros (unlike Fedora, for example). They look good on my netbook, but I'm always struggling with some issues and eventually switching back to Windows.

I want to stick to Xubuntu 11 (and Linux in general) for numerous reasons, but I won't dwell on that. Here are my current issues:

1) I'm using Xfce DE now, but I can't handle configuring Compose Key through terminal or similar means. Lack of GUI hurts. Instructions on the net are for old Ubuntu Xfce releases, not up to date any more. I know how to edit files as a root, but the problem is that in /etc/X11/ there's no **Xorg.conf** file, and I'm supposed to edit it as far as I know. I read I have to **create** it somehow. The question is: **how do I do that?**

2) In all Linux distros I used, I had trouble opening ports. It's easy when an application does it for me, like Transmission or Skype. There is a web chat that uses port 8080 and whenever I try to enter it, I get a message that my port 8080 is closed. It's okay on my Windows on the same machine, it runs there even without opening the port on my router. Disabling the firewall in Linux doesn't help either. So... what else is there?[/COLOR]

---

### Post by LewisTM on 2011-12-27
About #1
You can add the xkb-plugin to a Xfce panel to set the Compose key and other options.
Be aware, however, that it is prone to amnesia.
There is a complete bug report [here]("https://bugs.launchpad.net/ubuntu/+source/xfce4-xkb-plugin/+bug/548631/"), with some potential workarounds to force the plugin to remember its settings. 

Good luck!

---

### Post by kreaven on 2011-12-29
Thanks for reply. **I moved on to Lubuntu**, but am still struggling with these two issues. (The latter doesn't bother me that much as it doesn't affect my work.) I made a new thread.

---

