---
title: "network and soundcard not working"
date: 2009-10-28
forum: General Help
---

### Post by faqwad on 2009-10-28
Recently, trying to get Firefox' scrolling to work a bit better in jaunty (running on a Dell 700m laptop, on the board Intel graphics, Broadcom wireless), I tried Rado's solution from this thread:

[http://ubuntuforums.org/showthread.php?t=295898](http://ubuntuforums.org/showthread.php?t=295898)

Into terminal write: uname -r to know your kernel version
than: 
[HTML]sudo apt-get update
sudo apt-get install linux-restricted-modules-(behind last dash write number of your kernel version)
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv[/HTML]

than restart in terminal with:
[HTML]sudo shutdown -r now[/HTML]

- Bad idea, it turned out... When I rebooted my graphics were no good - funny vertical lines. 

I managed to get the graphics going again by doing 

[HTML]sudo apt-get remove xorg-driver-fglrx[/HTML]

but now my networking won't work, neither wireless nor ethernet connected directly to my router, and the volume control says that there is no hardware connected. 

I've been through part of the Ubuntu wireless troubleshooting doc, and the wireless interface is appearing, but it won't connect. 

Can anyone save me from a reinstall?

---

