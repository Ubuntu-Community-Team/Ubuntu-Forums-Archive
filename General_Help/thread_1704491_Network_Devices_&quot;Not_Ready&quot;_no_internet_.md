---
title: "Network Devices &quot;Not Ready&quot; no internet broken package catalog"
date: 2011-03-10
forum: General Help
---

### Post by Tenyuu on 2011-03-10
can not connect to internet, nm-applet just tells me interface not ready for both wlan0 and eth0, if i plug eth0 in it will not connect to the internet, I would like to fix this without re-install

networkmanager-gnome is broken but when i try to install the deb from flash drive ubuntu software center tells me i need to fix package catalog, but it cant fix it without internet access.

---

### Post by Zorael on 2011-03-10
The thread is tagged **[color=RoyalBlue][kubuntu][/color]** but you mention nm-applet. Did you mistag it or are you using nm-applet in KDE?

You could try connecting via the terminal. If it doesn't work there either, perhaps it will throw a more meaningful error message at the very least.

Assuming you automatically receive an IP from a DHCP server;
```
$ sudo ifconfig eth0 up
$ sudo dhclient eth0
```

Hopefully you should now have a working net connection.
```
$ host kubuntu.org
kubuntu.org has address 91.189.94.156
kubuntu.org mail is handled by 10 mx.canonical.com.
```

If so;
```
$ sudo apt-get update
$ sudo apt-get install aptitude --no-install-recommends
$ sudo aptitude install -f
$ sudo aptitude full-upgrade
```

---

### Post by Tenyuu on 2011-03-10
mistagged it, i ment to tag it as Ubuntu.

if i left click on nm-applet, it says device not ready under ecah interface, also I disconvered that i did not have dhclient instlled. but when I try to install the deb for dhclient or for networkmanager-gnome ubuntu software center tells me i need to repair the package catalog, but when I click repair it tells me to check my internet connection (but I cant connect to the internet) so I am looking for a way to fix this without internet connection because I don't want to re-install my system....

---

### Post by Zorael on 2011-03-10
I'm really not sure what 'not ready' means in this context. Do any of the following commands make it ready again?
```
$ sudo ifconfig eth0 up
$ sudo ifup eth0
```

The dhclient tool is part of the **dhcp3-client** package, which **ubuntu-minimal** depends on. It should be installed on every normal installation, unless manually removed.

There's lots and lots of stuff you can do to troubleshoot this, but it's hard to know where to begin, and much of it needs to be done in the terminal. There may be error messages listed in the output of **dmesg**, for instance.

---

### Post by Tenyuu on 2011-03-12
Tag: [Solved]

thanks for your help :)

---

