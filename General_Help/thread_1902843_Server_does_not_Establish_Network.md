---
title: "Server does not Establish Network"
date: 2011-12-31
forum: General Help
---

### Post by Matchlighter on 2011-12-31
I have a home server that will not connect to my home network. It was working just fine until I tried installing MythTV on it. I have been following [this ]("http://www.havetheknowhow.com/Install-the-software/Install-MythTV.html")guide. I installed the 'ubuntu-desktop' package instead of 'gnome-core' since 'gnome-core' was not working with Oneiric. That installed just fine and I had connection the whole time. I then used Synaptic to install MythTV. I had to restart in order to be put into the 'mythtv' group. After that, it hasn't worked. On the first reboot, it locked up in the Debian boot screen, so I hard-rebooted it. Every time since, it boots up, says something to the effect of "Getting network config", followed by "Will wait 60 more seconds", then "Booting without full network configuration". It then proceeds to do a few more boot operations then tells me apache2 is starting followed by "Checking battery...    [OK]". After that it stops. all it has the blinking underscore and it won't let me do anything. I have tried Recovery mode, but I don't know what to do there as it won't uninstall anything from there.

Any help/suggestions would be appreciated.
Ethan

---

### Post by rsvancara on 2012-01-01
Have you tried booting into single user mode.

[http://www.knowyourlinux.com/content/boot-ubuntu-mint-or-debian-single-user-mode](http://www.knowyourlinux.com/content/boot-ubuntu-mint-or-debian-single-user-mode)

---

### Post by Matchlighter on 2012-01-01
That got me in, but uninstalling the packages did not help. Upon boot, I get a lot of messages about Modem Manager not being able to access the system bus. and to make sure the 'message bus daemon' is running. Is that significant? How do I make it start correctly?

E

---

