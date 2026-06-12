---
title: "Can't get NetworkManager applet to appear in Gnome Panel"
date: 2011-01-09
forum: General Help
---

### Post by natereed on 2011-01-09
Running Ubuntu 10.04.  I am trying to connect to my VPN using the NetworkManager applet, but it doesn't appear in the panel.  I know there have been threads for this problem (some of them too long so I decided to start a new one) but none of the suggestions have worked for me.

I added the Notification Area to the panel.  I also updated my network manager configuration in /etc/NetworkManager/nm-system-settings.conf and changed managed=false to managed=true.

As suggested, I tried to restart the NetworkManager:
nate@nate-desktop:~$ killall nm-system-settings
nm-system-settings: no process found

I'm guessing that command is no longer available in this release so I just restarted the Network Manager:

nate@nate-desktop:~$ sudo service network-manager restart
sudo service network-manager restart
network-manager start/running, process 2217

I rebooted but still the NetworkManager applet doesn't appear.

I'm not sure what else to try.  This has been a pretty frustrating problem.  Any ideas?

---

### Post by natereed on 2011-01-09
I found the issue.  This was working on my laptop, which has the familiar wireless signal icon.  The machine in question has no wireless card, so the NetworkManager applet was represented by the up/down arrows.  I didn't know that was for the NetworkManager.  It's working fine; I am able to connect using the applet.

---

### Post by windofkeltia on 2011-02-28
I wish for more on this, so, I'm not exactly hijacking this thread. I just don't think the question was copiously answered.

I have an HP notebook running Maverick. I am working from a wired doc right now. I'm going to go mobile here soon (for the first time since I got the computer) and so think I'll need this.

My "two arrows" icon disappeared a couple of weeks ago. I've now got a "radio tower" icon I dragged from System -> Preferences -> Startup Applications -> Network Manager, but clicking it does nothing.

Any comment would be appreciated.

---

