---
title: "Xorg at 100% CPU"
date: 2011-01-18
forum: General Help
---

### Post by mixmaster on 2011-01-18
Since a recent update I have been experiencing complete system locks where the keyboard and mouse buttons become unresponsive and the mouse pointer does not change shape although I can move it around the screen.

Logging in from another system via ssh is possible and if I do this "top" shows Xorg using 95-100% cpu.  Turning off the screensaver seems to have mitigated but not removed the problem - the last couple of occasions it happened seem to be associated with displaying a reasonably large graphic from dropbox.

I've looked in /var/log/messages.  There are a number of lines like 

Jan 17 16:54:06 dominator kernel: [432839.239624] type=1400 audit(1295283246.955:40): apparmor="DENIED" operation="open" parent=30134 profile="/usr/lib/firefox-3.6.13/firefox-*bin" name="/etc/gnashpluginrc" pid=8146 comm="gtk-gnash" requested_mask="r" denied_mask="r" fsuid=287725 ouid=0

which seem to correspond to some, but not all, of the lockups.

Any suggestions would be appreciated.

---

### Post by glendeni on 2011-02-10
What version are you using?  On a new install of 10.04 I am experiencing the same, i.e. occasional lockup with Xorg ~100% CPU and no response from keyboard or mouse, except mouse will move an abnormally large pointer around, requiring a hard reboot.  Both with Gnome & KDE desktops.

---

### Post by flopin on 2011-02-16
Hello, i am using Kubuntu 10.10, very fresh install and i am experiencing similar problems.

After the install, everything worked fine, but after few days (and many applications installed) the system is becoming unusable because of this Xorg issue. Every simple action (open folder, open popup menu, open window, ect.) takes like few seconds with Xorg running 100% cpu during that time. 

Disabling desktop effects helps a bit, but it is still terrible. Tried googling this out, it seems that many users are having these problems, no hints worked for me or were irrelevant or obsolete.

Any ideas?

My config: DELL latitude D630, nvidia quatro 135M, twin view - 1280x800 and 1920x1080 (problem persist even if i turn external off)

---

### Post by roeland on 2011-03-02
I only recently upgraded to 10.10 and started experiencing this very problem; sometimes Xorg stays at 100% CPU for some seconds, and sometimes it seems to get stuck there. I've just discovered that logging in from another machine still works, and managed to solve the problem by killing firefox.

I have FF 3.6.13 running, with two very simple HTML pages open in tabs. The problem starts at seemingly random times, it doesn't seem to have anything to do with me being active in FF; in many cases, I'm even working on another desktop.

---

