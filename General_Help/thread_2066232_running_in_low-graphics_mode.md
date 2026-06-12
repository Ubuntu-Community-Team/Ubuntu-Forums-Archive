---
title: "running in low-graphics mode"
date: 2012-10-04
forum: General Help
---

### Post by ndhertubu on 2012-10-04
I did a completely new install of Ubuntu 12.04.1 on 2 computers
- laptop Dell Latitude E6400 (2 years old)
- desktop Dell Optiplex 210L (somewhat old)
 
same operations on both (laptop 4 weeks ago, desktop 2 days ago):
- Installed from a 12.04.1 (kernel-3.0.29) CD (downloaded begin sep 2012)
- added gnome desktop (sudo apt-get install gnome-session-fallback)
- added few icons in top and bottom taskbars
- specified a ntp server
- installed newest updates from Update manager (now kernel-3.2.0.30-generic-pae on laptop, and kernel 3.2.0.31-generic-pae on desktop)
- installed synaptic package manager
- gave root user a password and made it possible to enter "root" and its password via adding  a line  greeter-show-manual-login=true
in /etc/lightdm/lightdm.conf
- enabled SSH server
- change the date format in the top bar (needed to do that in Unity desktop, in GNOME allows you to change, but doesn't acutally do it, workarround: change it in Unity, then it is also changed in GNOME)
 
during all these configurations, several reboots where done. No problem.
 
After the last change, at reboot, I don't get a desktop anymore:
After the ubuntu logo (with the 5 red dots under it), I get a screen "The system is running in low-graphics mode. Your screen, graphics card, and input device could not be detected correctly. You will ne to configure these yourself."
Mouse doesn't work! 
Hitting the enter key, moves to a different screen with 4 options
but now neither mouse nor keyboard is working...
(I can do Ctrl-Alt-F1 to get an ASCII screen and log in with username/password)
 
I have this problem on the laptop (a few weeks ago it still worked, haven't changed anything yet since, now at first boot, have that same  problem.
 
However, just now (while writing the mail) I once more (brutally) powered off the laptop, powered it on again and now I get the login screen, 
 
But on my desktop after several power-off/power-on still no luck ...
 
I already wiped out the desktop disk and did a complete reinstall (as described above), but I still get the problem again ...
 
All this is particularly frustating: sometimes it works, sometimes it doesn't !
 
The hardware is not exotic al all (standard graphics cards from Dell systems, standard keyboards and mouse), so it should work ...
 
What's going on here ? 
How to make this STABLE and/or WORKING in the first place ?

---

