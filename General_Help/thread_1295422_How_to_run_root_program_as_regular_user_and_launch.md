---
title: "How to run root program as regular user and launch by click?"
date: 2009-10-19
forum: General Help
---

### Post by PerfectReign on 2009-10-19
Sorry if this has been posted. I searched and could not find anything.


Pretty much every day I come to work, plug in my laptop (Ubuntu 9.04 GNOME) and start it up.

In order to get on the network, I have to launch the terminal and run sudo dhclient, followed by my password.

I'd like to simply double-click on some script and have dhclient run and also not type in a password.

How do I do this?

---

### Post by -Zeus- on 2009-10-19
It's a security measure, there is a way to disable password authentication once logged in if you want to try it.

```
sudo visudo
```

This should open up a text editor.

Then, go to the last line and copy this in. (replace your_username with yours)

```
%your_username ALL=(ALL) NOPASSWD: ALL
```

Then, press Ctrl-X, y, enter.

I think you have to logout.

---

### Post by aysiu on 2009-10-19
That's a bit extreme, isn't it?

How about just making it so *dhclient* (and not every single application) doesn't prompt for a password? ```
perfectreign ALL= NOPASSWD: /sbin/dhclient
```

---

### Post by PerfectReign on 2009-10-19
thanks, all!

i just read up on it - I see the following

[http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/](http://ubuntu-tutorials.com/2007/03/01/allowing-limited-sudo-access-with-visudo/)

This is perfect. For the occasional command which I deem not-quite-as-perilous I can run without a password.

I can then just create a sh command on the desktop and click when needed. :)

---

### Post by PerfectReign on 2009-10-21
Well that didn't work.  :(


Here's what I get now running dhclient without typing sudo first...


[B][FONT=System][COLOR=Blue]kai@r2d2:~$ dhclient
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
can't create /var/lib/dhcp3/dhclient.leases: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.pan0: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.vboxnet0: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.wlan0: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.wmaster0: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.vmnet8: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.vmnet1: Permission denied
SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
SIOCSIFFLAGS: Permission denied
/etc/dhcp3/dhclient-exit-hooks.d/whereami: line 24: /var/lib/whereami/dhclient3.eth0: Permission denied
wmaster0: unknown hardware address type 801
Open a socket for LPF: Operation not permitted[/COLOR][/FONT][/B]

---

### Post by Raiju on 2009-10-21
Edit: wrong link :x
[ ]("http://ubuntuforums.org/showthread.php?t=490690")

---

### Post by aysiu on 2009-10-21
> **PerfectReign said:**
> Well that didn't work.  :(


Here's what I get now running dhclient without typing sudo first... After you edit the /etc/sudoers file with *sudo visudo* and change the line, you still need to launch the command with *sudo*: ```
sudo dhclient
``` it just won't prompt you for a password.

---

### Post by PerfectReign on 2009-10-21
Okay, thanks.

I'll try that tomorrow when I come into work again. (I have to  run dhclient every time I plug my laptop in at work for some reason.)

---

### Post by aysiu on 2009-10-21
> **PerfectReign said:**
> Okay, thanks.

I'll try that tomorrow when I come into work again. (I have to  run dhclient every time I plug my laptop in at work for some reason.)
Then maybe we're going about this the wrong way. How about linking it to the initial startup processes? All of those get run as root anyway and *automatically* at boot: ```
sudo ln -s /sbin/dhclient /etc/init.d/dhclient
```

---

### Post by The Cog on 2009-10-21
Why not just install wicd and configure it to use DHCP there?

---

### Post by PerfectReign on 2009-10-22
wicd was instaled. I tried it several months ago, but never got any results, and network manager got uninstalled for some reason.


I did create a quick launch icon in my task pane (kicker?) and it works. Goes out to the CLI, launches dhlclient without me needing a password and I'm given a proper IP addy.

---

### Post by The Cog on 2009-10-22
Yes, wicd conflicts with network manager so you can only have one installed at a time.I don't understand why wicd isn't configuring the interface though. It does on my work laptop which I normally use wired.

---

