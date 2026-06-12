---
title: "Want to connect to router at boot (not login)"
date: 2010-01-08
forum: General Help
---

### Post by irishbreakfast on 2010-01-08
My laptop is a server for the family calendar and it works great (and thanks to the folks at #ubuntu), when I am logged in. But I want it to work when the machine is simply booted. According to syslog the network is enabled at boot but doesn't make a connection to the router until I log in (I am the only user on the machine). I have been reading docs and forums but have been unable to find out how to make the connection to our router at boot.

Cheers

---

### Post by Iowan on 2010-01-08
I presume the laptop has a desktop version installed. Network Manager activates network connections at login. If you configure the interface(s) in */etc/network/interfaces*, they *should* activate at boot (but Network Manager will complain).

---

### Post by tommynz1975 on 2010-01-08
May I please jump in here? for the purpose of learning and teaching.

When one downloads a copy of ubuntu they can choose a laptop version?

How is the  Laptop version named?

---

### Post by irishbreakfast on 2010-01-09
Iowan,
I have tried some changes there and it doesn't work. I also followed some threads with advice for starting up via the cli, thinking I would use that in a script. No connection that way.

I finally looked at syslog and found problems with dhclient. But I don't know how to fix it. I went to the router to see what the error logs, but no luck as it will send the errors to a syslog and I am the only machine running a syslog.  Ideas anyone?

Listening on LPF/wlan0/00:1f:3c:54:17:1f
Sending on   LPF/wlan0/00:1f:3c:54:17:1f
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
 * Reloading /etc/samba/smb.conf smbd only

---

### Post by lisati on 2010-01-09
<aside>
> **tommynz1975 said:**
> May I please jump in here? for the purpose of learning and teaching.

When one downloads a copy of ubuntu they can choose a laptop version?

How is the  Laptop version named?

The "Desktop edition" can be run on a laptop. The term "desktop" comes in part from the inspiration for early graphic user interfaces coming from a hypothetical desk.
</aside>

---

### Post by jkounis on 2010-01-09
> **tommynz1975 said:**
> May I please jump in here? for the purpose of learning and teaching.

When one downloads a copy of ubuntu they can choose a laptop version?

How is the  Laptop version named?

Maybe I can add just a bit of clarification. I was really confused about this when I first downloaded Ubuntu years ago.

There are only 2 editions of Ubuntu: the "server" edition and the "desktop" edition (there's no "laptop" edition). 

With Microsoft or Apple, when you buy a "server" version of something it's really expensive and has a lot of complicated stuff that makes money for for the company and people who are maintaining it.

This is backwards in Ubuntu. The server edition is the basic version. It doesn't have a Graphical User Interface (GUI), so it looks pretty ugly when you boot it: just a black screen with a login prompt and a blinking white cursor.

The desktop edition is the server edition with a desktop environment added to it, so you don't have to log in and run everything from the command line. (e.g. instead of typing "sudo apt-get upgrade", you can click "System" -> "Administration" -> "Upgrade Manager"). The windows environment also allows you to use cool stuff like OpenOffice, Web Browsers, and Games (among other things). Since most people use desktop computers for things like word processing, the version of Ubuntu that lets you use all these programs is called the "desktop edition".

There are a few different desktop environments available (basically a program that runs on top of the "server" edition to give you a graphical interface). Ubuntu has a program called GNOME as its desktop environment ([www.gnome.org](www.gnome.org)). Kubuntu uses KDE (see [www.kde.org](www.kde.org)). Xubuntu uses XFCE (you guessed it... [www.xfce.org](www.xfce.org))

I was very confused until I realized that, even though I had a "desktop" edition, I could still install MySQL server, Apache server, and all those other neat "server" packages that Microsoft charges all that money for onto my computer (Actually it's even a little bit easier on a desktop than on a server, since I have a graphical interface to install everything and a web browser to administer many functions).

In addition to the GUI, the Desktop edition has all the programs like network-manager that you would use on a laptop to connect to a wireless network, as well as features for hibernation and suspend, so it is most commonly installed on laptops.

---

### Post by irishbreakfast on 2010-01-09
Iowan,
Finally had success. I changed /etc/network/interfaces as well as setting up wpa_supplicant. This was the most difficult as I didn't find (but didn't look very well) for documentation on wpa_supplicant.conf. And you were correct, NetworkManager is complaining when I log in. Plus the applet doesn't recognize that the connection is active, which is something I like. 

NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))

---

