---
title: "Gnome panel issues + autostart..."
date: 2010-08-31
forum: General Help
---

### Post by Landshark on 2010-08-31
Hello,

I have a few what I hope are basic Gnome questions.

I am running 10.04 on a Thinkpad T410. I just use one Gnome panel -- the top one -- and I use e16 as my windows manager. Recently several of the buttons on the Gnome panel vanished.  Network Manager is an example, which is pretty critical. My startup applications are also not starting at log-in.  

I therefore followed the advice provided in the post #4 on this thread: [http://ubuntuforums.org/showthread.php?t=1485088](http://ubuntuforums.org/showthread.php?t=1485088). Some items reappeared, but no Network Manager.

So I created a launcher in order to get nm-applet to run. But the icon for the launcher was blank, so I tried to assign an alternative:

/home/me/.gnome2/panel2.d/default/launchers

edited nm-applet.desktop.

Added Icon=/usr/share/pixmaps/gdm.png.  No luck. Still blank.

So what I have is a panel that fluctuates, autostart apps that don't start, and a limited ability to customize. I suspect this may involve the default user profile for Gnome, but I'm stuck.

Thank you for any insight.

Landshark

---

### Post by juil on 2010-08-31
Well there are a few things you can try. 

Try
> gksudo gedit /etc/NetworkManager/nm-system-settings.conf
And change "managed=false" to "true" (or vice-versa?)

Or you can try deleting the panel and creating a new one:

Code:
> gconftool-2 --shutdown
gconftool --recursive-unset /apps/panel
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

If still not working,
If you search under 'nm-applet --sm-disable' in the forums, it will yield lots of results

---

### Post by Landshark on 2010-09-01
Thank you. As mentioned in my post, I had already created a new panel but had the same issues with the new one.  I tried your other suggestion -- changed it to False -- and rebooted.  No difference.

My issues are: 

Panel changes -- loses icons, etc.

Launcher icon is a blank rectangle.

Autostart apps don't start.

---

