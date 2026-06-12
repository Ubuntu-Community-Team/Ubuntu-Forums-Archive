---
title: "nm-applet not visible in xfce"
date: 2010-06-08
forum: General Help
---

### Post by mad_ady on 2010-06-08
Hello,

I'm trying to switch from my legacy network configuration scripts (/etc/network/interfaces) to NetworkManager, but I haven't been able to start the nm-applet in Xfce.
I'm running 10.04 with the latest updates. I have purged and reinstalled all NetworkManager related packages and still nothing.

If I start nm-applet from a console, I get the following output:
```

adrianp@frost:~$ nm-applet 
Xlib:  extension "RANDR" missing on display ":0.0".
/home/adrianp/.themes/Murrina-Forsaken64/gtk-2.0/gtkrc:50: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
** (nm-applet:3655): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3655): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:3655): DEBUG: old state indicates that this was not a disconnect 0


```

The process keeps running, but I don't get any icon (not even an empty spot) in the notification area from my panel. I've checked the notification area plugin and it isn't set to hide NetworkManager. Pidgin displays just fine in it.

So - any tips on how I can enable the nm-applet in my XFCE? Or, how can I configure NetworkManager without the nm-applet?

Regards,
Adrian

---

### Post by mad_ady on 2010-06-09
I didn't manage to fix this issue, but I found a suitable workaround of it. I configured my connections with nm-connection-editor (since I have only wired connectivity) and so far, NetworkManager seems to work fine, without the applet.

There's also another tool (nm-tool) that shows the current status.

---

### Post by tommcd on 2010-06-09
If network-manager is giving you trouble, you could just uninstall it and install **wicd** instead. Wicd is very easy to use and works very well.

---

### Post by mad_ady on 2010-06-09
Yes, I've tried wicd, but it doesn't seem to allow me to configure multiple simultaneous wired interfaces (I have 3 which are always on) - maybe I didn't know how to configure it...

Anyway, I did my my configuration with nm-connection-editor and at the next restart - presto - my applet appeared where it was supposed to be.

To clarify things - before the restart I had removed the entries in /etc/network/interfaces for my NetworkManager managed interfaces. Then I configured those interfaces in NetworkManager, and I did a reboot. Now, everything seems to work just fine.

In conclusion - perhaps the applet just doesn't show an icon if it doesn't have any managed interfaces...

Hope this helps others in the same situation.

---

### Post by zbyszek on 2010-06-10
Synaptic install gnome-netstatus-applet

---

### Post by eev2 on 2010-06-10
You need to remove the line 
iface eth0 inet dhcp
from /etc/network/interfaces in order to show the nm-applet

---

### Post by u1106 on 2010-09-21
> **eev2 said:**
> You need to remove the line 
iface eth0 inet dhcp
from /etc/network/interfaces in order to show the nm-applet

Yes, that works. But it is not a solution. I want to to use eth0 for Internet Connection Sharing, so I actually have the line

```
iface eth0 inet static
```(and additional specifications) in /etc/network/interfaces.

I use wlan0 to connect to the internet using network manager.

As long as a previously defined WLAN is detected everything is fine. Network manager connects automatically and  nm-applet is visible.

However, if no previously defined WLAN is detected (e.g. when travelling to a new location) nm-applet, i. e. the "No connection" icon is not visible. Without nm-applet being visible I don't know how I could connect.

Ironically enough the "No connection" icon gets visible when I disconnect from a network (which was previously defined and now automatically connected). But that doesn't really solve the problem.

---

### Post by Nightslay on 2010-10-19
that is right.
you should check the NetworkManager conf

sudo nano /etc/NetworkManager/nm-system-settings.conf

check that the ifupdown statement is true or else there will be nothing to administrate.

[ifupdown]
managed=true

that should get the applet running after a logout

best regards
Claus

---

