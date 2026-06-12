---
title: "Lubuntu as guest in VMWare - screen resolution"
date: 2010-09-26
forum: General Help
---

### Post by ridz on 2010-09-26
I am trying Lubuntu 10.04 as a guest in VMWare Workstation 6.5.4. My host is a Windows XP SP3 PC (soon to move to Ubuntu 10.04). The installation went fine and the vm seems to be working perfectly - all latest updates were applied and all the supplied software works.

However, the only item that is annoying is that Lubuntu always start up with 800x600 screen resolution. I can set the resolution to the one I want (1152x864) using Preference -> Monitor Setting but when I restart the vm again, Lubuntu always defaults to 800x600. BTW, my LCD monitor has a native resolution of 1920x1080 - a screen resolution of 800x600 is simply too small for my needs.

I note that there is no xorg.conf in the /etc/X11 directory and after researching the internet, I also found out that this is normal for the version of X that Lubuntu uses. I also tried out the 'xrandr' command on a console - this also works in setting the screen resolution to 1152x864 but it also is NOT persistent across restarts.

My question is - how do I make the vm always start up in the resolution I want - 1152x864? I don't want to fiddle around in xorg.conf if this can be avoided. Help please.

---

### Post by chessplayer on 2010-10-30
I have the same problem on a Kubuntu host and would also appreciate help ...

---

### Post by chessplayer on 2010-10-31
> **ridz said:**
> I am trying Lubuntu 10.04 as a guest in VMWare Workstation 6.5.4. My host is a Windows XP SP3 PC (soon to move to Ubuntu 10.04). The installation went fine and the vm seems to be working perfectly - all latest updates were applied and all the supplied software works.

However, the only item that is annoying is that Lubuntu always start up with 800x600 screen resolution. I can set the resolution to the one I want (1152x864) using Preference -> Monitor Setting but when I restart the vm again, Lubuntu always defaults to 800x600. BTW, my LCD monitor has a native resolution of 1920x1080 - a screen resolution of 800x600 is simply too small for my needs.

I note that there is no xorg.conf in the /etc/X11 directory and after researching the internet, I also found out that this is normal for the version of X that Lubuntu uses. I also tried out the 'xrandr' command on a console - this also works in setting the screen resolution to 1152x864 but it also is NOT persistent across restarts.

My question is - how do I make the vm always start up in the resolution I want - 1152x864? I don't want to fiddle around in xorg.conf if this can be avoided. Help please.

Well, I helped myself now and it turned out that using an xorg.conf is just the ticket. In fact, the solution can be found in the German ubuntuusers Wiki at [http://wiki.ubuntuusers.de/Bildschirmauflösung]("http://wiki.ubuntuusers.de/Bildschirmaufl%C3%B6sung") in the section headed **PCs ohne Monitor**. Copying the xorg.conf provided there and adapting the resolution to suit your needs (1440x900 in my case) and putting that in /etc/X11/xorg.conf did the job for me.

Moreover, other than with using the menu entry "Monitor Settings" the fonts are not scaled and everything is fine. So I recommend doing just that.

For convenience, I attached my xorg.conf.

Enjoy!

chessplayer:)

---

### Post by dcstar on 2010-11-01
> **ridz said:**
> I am trying Lubuntu 10.04 as a guest in VMWare Workstation 6.5.4. My host is a Windows XP SP3 PC (soon to move to Ubuntu 10.04). The installation went fine and the vm seems to be working perfectly - all latest updates were applied and all the supplied software works.

However, the only item that is annoying is that Lubuntu always start up with 800x600 screen resolution. I can set the resolution to the one I want (1152x864) using Preference -> Monitor Setting but when I restart the vm again, Lubuntu always defaults to 800x600. BTW, my LCD monitor has a native resolution of 1920x1080 - a screen resolution of 800x600 is simply too small for my needs.

I note that there is no xorg.conf in the /etc/X11 directory and after researching the internet, I also found out that this is normal for the version of X that Lubuntu uses. I also tried out the 'xrandr' command on a console - this also works in setting the screen resolution to 1152x864 but it also is NOT persistent across restarts.

My question is - how do I make the vm always start up in the resolution I want - 1152x864? I don't want to fiddle around in xorg.conf if this can be avoided. Help please.

[LIST=1]
[*]All VM issues should be in the Virtualization forum
[*]VMware Tools installation allows the setting of screen resolutions.
[/LIST]

---

