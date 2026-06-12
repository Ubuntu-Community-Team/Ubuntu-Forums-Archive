---
title: "Vino and TightVNC only work once?"
date: 2010-10-31
forum: General Help
---

### Post by drmccoy on 2010-10-31
Hey folks,

I have a ubuntu machine setup at my other place and wanted to get be able to work at it at the weekend. So I checked out the Remote Desktop feature which also is in my System->Start category. I enabled and configured it and was perfectly able to access my machine via TightVNC from a remote windows pc. Did it over and over again until I was forced to do a reboot of the machine (sshing a sudo reboot). Now, after the machine did reboot, my webserver and FTP server are running and i'm able to ssh via putty. I also set the login setup of the server to automaticly login my user without asking for his password. I'm simply NOT able to connect via TightVNC. It connects, asks for my password and then it stays like this: 
[IMG]http://img834.imageshack.us/img834/936/proofh.png[/IMG]

If I close that window and open up TightVNC again, it doesn't ask me for the Password again, but simply prompts this, which will stay there forever aswell:

[IMG]http://img521.imageshack.us/img521/1316/proof2r.png[/IMG]

no matter what i do. So far I also tried

[I]gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true[/I]

That didn't change anything. And:

*/usr/lib/vino/vino-server --display=0*

says it cannot open up the display.

What the hell am I doing wrong?

---

### Post by drmccoy on 2010-10-31
No idea? Anyobdy? :confused:

---

### Post by drmccoy on 2010-11-01
bump

---

