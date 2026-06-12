---
title: "Wifi in Kubuntu- can't get an IP"
date: 2006-04-04
forum: General Help
---

### Post by koolguynet on 2006-04-04
I have been using Ubuntu for a couple of months now and I love it.  I like gnome, but I have used KDE in the past (RedHat and Fedora Core) so I would like to give it a try on my laptop.  I installed the Kubuntu desktop the other day on my stable IBM T41 running Ubuntu.  Everything on the KDE side seems to work, but the wifi.  On the gnome side, I have found that gtkwifi works great.  On KDE Kwifi, just doesn't seem to work.  I have went into my connections, added my SSID and put in my WEP key.  When I go to Kwifi, I can see my access point...I can see its signal strength, but it won't acquire an IP.  Am I missing something?  [http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)
](*,)

---

### Post by Randomskk on 2006-04-04
I'd guess you need to enable DHCP on the wireless.
If you know the wireless device (eth0 maybe, or wifi0 or whatever) try:
```
sudo dhclient eth0
```

---

### Post by koolguynet on 2006-04-04
I just tried that.  It was a good idea, but didn't work.  It said there was already another dhclient pid running so it killed the old one and started running the new one.  It didn't find an IP.

---

### Post by mexlinux on 2006-04-04
I have kubuntu 5.10 and I'm always on wireless... wifi in kubuntu is just crappy.

The only ways I found to properly work almos every time:

1)For Static Address
-Modify your /etc/network/interfaces and /etc/resolv.conf by hand...
-sudo ifdown eth1
-sudo /etc/init.d/networking stop
-wait a couple of seconds
-sudo /etc/init.d/networking start

2)For dynamic address
-Install wifi-radar
-Stop the wifi-radar daemon, and set it to NOT start at boot.
-sudo wifi-radar

Regards,
Miguel

---

### Post by groggyboy on 2006-04-05
i'm jumping in, i know.  but i also think kwifi is crappy.  i was recently forced to migrate to kubuntu. (gnome just up and stopped on me, and i've been too busy to fix it - thankfully i had installed kde a while back out of curiosity!)

i switch a lot between my home and my school wireless networks.  in gnome, gtkwifi worked fine for me.  kwifi, on the other hand, won't connect to the school's network - ever.  and if any network should drop or i should hibernate my laptop, kwifi is too stupid to get things running again.  i end up having to run gtkwifi - i have to use the command "gtkwifi run-in-window", and the little icon from the gnome panel appears in a floating window.

i'm sure kwifi, with time, could be set to work the way i need it.  but i just don't like kwifi enough.  does anyone know of alternative wifi managers for kde, or (better yet) of a way to get gtkwifi to run in kde's system tray?

cheers!
groggyboy

---

### Post by koolguynet on 2006-04-06
Does anyone know if Dapper plans to make Kubuntu wifi better (read: work)?  I appreciate the feedback I have received, but I don't have the patience or the time for CLI everytime I switch networks.  I am very mobile, so for now I will stick with gnome and gtkwifi (which rocks).  Thanks everyone!

---

### Post by tokyovigilante on 2006-04-07
What about KNetworkManager? 0.6 has just hit Dapper, seems to offer what you need (ie wireless roaming).
[https://wiki.ubuntu.com/DapperKNetworkmanager](https://wiki.ubuntu.com/DapperKNetworkmanager)

---

### Post by groggyboy on 2006-04-07
cool.  thanks tokyovigilante.  only problem: i'm still running breezy - the latest networkmanager in the repos is v0.4.1 - and no knetworkmanager.  as soon as dapper hits beta i intend to upgrade, and then i'll for sure install it.  in the mean time, am I stuck with my current workaround?

---

### Post by incubus on 2006-04-07
Will good ol' terminal work there?

How about something like:
$ sudo iwconfig <ethN> essid <ssid name>
$ sudo dhclient <ethN>

If you use wpasupplicant, there's wpa_gui which I found to work very well (and uses QT).

best,
incubus

---

### Post by tokyovigilante on 2006-04-07
[quote=tokyovigilante]What about KNetworkManager? 0.6 has just hit Dapper, seems to offer what you need (ie wireless roaming).
[https://wiki.ubuntu.com/DapperKNetworkmanager]("https://wiki.ubuntu.com/DapperKNetworkmanager")[/quote]
Sorry about that, forgot which forum I was in. I've been using Dapper since the fork from Sid, and it's been pretty good, and is really stable at the moment.

Yeah, it's a pity the wireless in Breezy wasn't very good, I think hacks are the only way to get it to run well, unless someone has packaged NetworkManager for Breezy, which I don't think is very likely considering the reasonable ABI shifts from Breezy->Dapper. 

Do you have a spare partition to try Flight 6 on?

---

### Post by groggyboy on 2006-04-09
I'm repartitioning my harddrive this weekend (for a number of reasons).  i guess i could throw in an extra partition for dapper.   :-k  the thought had never even occured to me!

---

### Post by koolguynet on 2006-05-07
KNetworkManager works very well in Dapper Kubuntu!  Thank for the suggestion!

---

### Post by SirPecanGum on 2007-01-27
> **Randomskk said:**
> I'd guess you need to enable DHCP on the wireless.
If you know the wireless device (eth0 maybe, or wifi0 or whatever) try:
```
sudo dhclient eth0
```


Thanks, that fixed it for me!

---

