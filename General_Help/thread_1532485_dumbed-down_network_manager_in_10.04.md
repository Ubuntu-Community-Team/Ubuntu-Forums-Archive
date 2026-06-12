---
title: "dumbed-down network manager in 10.04?"
date: 2010-07-16
forum: General Help
---

### Post by z61P on 2010-07-16
I'm new here, so this may be a dumb question, but: 

The Network Manager "applet" shows up in my panel, and it seems to work after a fashion. However, the interface/GUI that it provides does not resemble the one I've seen on the Network Manager website ([http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)). It seems to me that I should at least have a "Disconnect" function, but I don't. 

Is the applet different from the application, or am I getting a dumbed-down GUI due to permission settings, or...??? 

Thanks,
Z

---

### Post by betlog on 2010-07-16
it's just not very good imo

---

### Post by prodigy_ on 2010-07-16
I usually remove network manager completely and then use /etc/network/interfaces file to configure my connections and scripts to manage them. Might be a bit tricky in the beginning (a lot of command line tinkering) but works like a charm once everything is set.

---

### Post by bodhi.zazen on 2010-07-16
> **z61P said:**
> I'm new here, so this may be a dumb question, but: 

The Network Manager "applet" shows up in my panel, and it seems to work after a fashion. However, the interface/GUI that it provides does not resemble the one I've seen on the Network Manager website ([http://projects.gnome.org/NetworkManager/](http://projects.gnome.org/NetworkManager/)). It seems to me that I should at least have a "Disconnect" function, but I don't. 

Is the applet different from the application, or am I getting a dumbed-down GUI due to permission settings, or...??? 

Thanks,
Z

Disconnect is an option, look harder (hint right click the applet).

---

### Post by betlog on 2010-07-16
> **prodigy_ said:**
> I usually remove network manager completely and then use /etc/network/interfaces
I was under the impression that /etc/network/interfaces was being used/read by knetworkmanager?
Is it? surely it is.... if not then I may need to strike my fist against the table a few times and swear a bit.

---

### Post by z61P on 2010-07-16
> **bodhi.zazen said:**
> Disconnect is an option, look harder (hint right click the applet).

tried that days ago... rtclk gives following options: 

Enable Networking
Enable Wireless
Enable Notifications
Connection Information
Edit Connections...
About

The Edit Connections dialogs do not offer a disconnect option.

---

### Post by bodhi.zazen on 2010-07-16
> **z61P said:**
> tried that days ago... rtclk gives following options: 

Enable Networking
Enable Wireless
Enable Notifications
Connection Information
Edit Connections...
About

The Edit Connections dialogs do not offer a disconnect option.

network manager will allow you to disconnect, I do not run gnome and do not recall all the mouse clicks.

Keep trying, left click, right click, click the connection.

---

### Post by prodigy_ on 2010-07-16
> **betlog said:**
> I was under the impression that /etc/network/interfaces was being used/read by knetworkmanager?
I don't want to start listing my complaints about NetworkManager here. Suffice it to say that RedHat (the authors) hardly even use it in RHEL, their commercial distro, anymore. And no wonder. They want to keep their paying customers.

---

### Post by betlog on 2010-07-17
so is there no gui based alternative?

---

### Post by dcstar on 2010-07-17
> **z61P said:**
> tried that days ago... rtclk gives following options: 

Enable Networking
Enable Wireless
Enable Notifications
Connection Information
Edit Connections...
About

The Edit Connections dialogs do not offer a disconnect option.

Left-click certainly does - if you actually have a working connection to disconnect.

---

### Post by bodhi.zazen on 2010-07-17
> **betlog said:**
> so is there no gui based alternative?

If you do not like NetworkManager and you want a gui, try wicd.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by z61P on 2010-07-17
> **bodhi.zazen said:**
> network manager will allow you to disconnect, I do not run gnome and do not recall all the mouse clicks.

Keep trying, left click, right click, click the connection.


Oh, good grief! That was it! ... LEFT CLICK!!   (but it still doesn't look likr the gui on the Network Mgr website)

Apologies - I did not mean to stir up the Network Manager flame-fest.

---

### Post by bodhi.zazen on 2010-07-17
> **z61P said:**
> Oh, good grief! That was it! ... LEFT CLICK!!   (but it still doesn't look likr the gui on the Network Mgr website)

Apologies - I did not mean to stir up the Network Manager flame-fest.

Glad you got it =)

Don't worry about the flame fest, lol

---

### Post by betlog on 2010-07-17
Flame-fests are usually longer than 2 pages, and eventually result in us attacking each other :]
Don't get me wrong, I kind of like the way networkmanager does things for the most part, but the fact that it does some of the things it does, the way it does them is really annoying.. and the "Other" section for "Configure the Network Management tool" ... is just weird.

---

### Post by betlog on 2010-07-17
Oh yeah [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"), wicd is pretty nice.
The way it allows a default connection to be specified is fairly essential... thats one of the thngs that  bothered me about knetworkmanager; it would try to connect 'Auto eth0' first every time.. which in my case failed due to lack of DHCP... and when I specified IP/subnet etc in /etc/network/interfaces it always seemed wrong and would somehow corrupt knetworkmanager so it's interface kludged up... even somehting as simple as specifying nameservers in /etc/resolv.conf didnt work at all.... but hey presto, remove knetworkmanager, install wicd, and everythng works precisely as specified...and all withouut trying to autoconnect to a profile that I know fails (DHCP Auto eth0).
Yay

---

### Post by bodhi.zazen on 2010-07-17
> **betlog said:**
> Oh yeah [[COLOR=#980101]**bodhi.zazen**[/COLOR]]("http://ubuntuforums.org/member.php?u=89054"), wicd is pretty nice.
The way it allows a default connection to be specified is fairly essential... thats one of the thngs that  bothered me about knetworkmanager; it would try to connect 'Auto eth0' first every time.. which in my case failed due to lack of DHCP... and when I specified IP/subnet etc in /etc/network/interfaces it always seemed wrong and would somehow corrupt knetworkmanager so it's interface kludged up... even somehting as simple as specifying nameservers in /etc/resolv.conf didnt work at all.... but hey presto, remove knetworkmanager, install wicd, and everythng works precisely as specified...and all withouut trying to autoconnect to a profile that I know fails (DHCP Auto eth0).
Yay

Glad it worked for you. Wicd is common on "light weight" installations. It works well and has minimal dependencies (as you can see).

In NM even so much as hiccups, I go with wicd.

---

