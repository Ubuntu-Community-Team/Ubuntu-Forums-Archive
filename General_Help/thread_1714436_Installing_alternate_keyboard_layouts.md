---
title: "Installing alternate keyboard layouts?"
date: 2011-03-25
forum: General Help
---

### Post by jbm222 on 2011-03-25
On a system I did not initially setup, I'm trying to figure out how to switch to Dvorak.  I know how to do it normally through gnome, but it looks like there weren't any alternate keyboard layouts installed.  Does anyone know what package/packages i need?

---

### Post by Krytarik on 2011-03-25
I did some package search and the respective package seems to be "xkb-data". But I'm actually wondering how the xserver is able to run *at all* if it were not installed. Anyway, check if it is installed, and even if so, try re-installing it.

Greetings.

---

### Post by Smart Viking on 2011-03-25
Try keyboards-rg

---

### Post by Krytarik on 2011-03-25
> **Smart Viking said:**
> Try keyboards-rg
Yeah, I did find those also, upon the first look. But since I don't have it installed, I believe it's not necessary for that matter.

---

### Post by jbm222 on 2011-03-25
Tried both packages and neither seemed to do the trick.   

I should probably mention that I am logged in using xrdp from a windows machine.   The windows machine is already setup to use Dvorak, but the remote desktop client apparently sends key codes, not characters.  The only option when I try to add a keyboard layout is "US 105-key keyboard (with windows key)".

The machine is headless so I have no easy way to verify or rule out the possibility that this is an XRDP-only problem.

---

### Post by Krytarik on 2011-03-25
It seems indeed to be confined to the XRDP connection, I did a quick web search about it.

You may check its *real* options with x11vnc, but like I said, I don't believe that the xserver would run at all if there were a general issue with the keyboard layouts:
[https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)

---

### Post by Daniel Garcia on 2011-09-23
Did you have any luck with this issue?

---

### Post by chascon on 2011-11-04
I've reported the issue as a bug at
[https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/881222](https://bugs.launchpad.net/ubuntu/+source/console-setup/+bug/881222)
but it hasn't gotten any attention. 

Your input on the bug report would be appreciated, if only to confirm that it is a valid issue. Hopefully, this bug can get the attention it needs to get fixed.

---

