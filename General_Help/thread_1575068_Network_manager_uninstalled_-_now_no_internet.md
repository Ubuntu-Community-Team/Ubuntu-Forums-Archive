---
title: "Network manager uninstalled - now no internet"
date: 2010-09-15
forum: General Help
---

### Post by Paul4763 on 2010-09-15
I was trying to setup a static IP and the first stage was to uninstall Network Manager. Done. Great, now I have no internet to see what the next stage is.

For about 3 hours now I've been farting about trying to install Wicd without an internet connection but has proved fruitless.

Basically, how do I install Wicd without a connection? Or reinstall Network Manager?

I'm running 10.04. Thank you.

---

### Post by Gunman1982 on 2010-09-15
Why did you uninstall Network Manager to set a static IP? 

Some more information would be good:
Do you want to set a static IP on a wireless connection or a wired one?
Are there other reasons for you to change to wicd?

For the reinstall issue:
Do you have a wired connection or can you temporarely connect your laptop/pc through wire?
Do you have a router with dhcp?

---

### Post by HereInOz on 2010-09-15
First up, open a terminal and type:

sudo gedit, and enter your password

Assuming you want to have a static IP of 192.168.0.1, with a Gateway address of 192.168.0.254, navigate to /etc/network and open the interfaces file.

Make it look like this:

   # This file describes the network interfaces available on your system
   # and how to activate them. For more information, see interfaces(5).

   # The loopback network interface
   auto lo
   iface lo inet loopback

   # The primary network interface
   auto eth0
   iface eth0 inet static
           address 192.168.0.1
           netmask 255.255.255.0
           network 192.168.0.0
           broadcast 192.168.0.255
           gateway 192.168.0.254


Please understand that you need to select these values to suit your own local area network IP range

Save that file then navigate to /etc and open resolv.conf

Enter your DNS servers in this file, then save it.  For example

   nameserver   203.87.45.234
   nameserver   203.87.45.235

Then restart your network interface:

/etc/init.d/networking restart

This should now give you a network and internet connection.

---

### Post by Paul4763 on 2010-09-15
[[IMG]http://img440.imageshack.us/img440/727/26409008.th.jpg[/IMG]]("http://img440.imageshack.us/i/26409008.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")
[[IMG]http://img709.imageshack.us/img709/2460/95724585.th.jpg[/IMG]]("http://img709.imageshack.us/i/95724585.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")


I did what you said but it didn't work. Can you see any errors?

---

### Post by Paul4763 on 2010-09-15
Bump

---

### Post by Iowan on 2010-09-15
**network** and **broadcast** addresses are optional, but when used, the network is usually the lowest address in the subnet (192.168.1.0) and the broadcast is the highest (192.168.1.255). The gateway is ordinarily your router.

You may need to restart using **sudo**.

---

