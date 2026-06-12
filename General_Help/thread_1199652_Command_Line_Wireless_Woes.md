---
title: "Command Line Wireless Woes"
date: 2009-06-29
forum: General Help
---

### Post by Vyizis on 2009-06-29
I have an eee box that i am trying to set up as a server, so far i have installed 9.04 server and i am trying to get the wireless network to work. I know that wireless is not good for a server but i dont have any other options unfortunatly.

I have had the wireless working before using the gui tools but i dont want to install a gui on to the box as a server.

I have followed most of the instructions on this page [http://www.eeextra.com/linux/installing-ubuntu-810-on-the-eeebox.html]("http://www.eeextra.com/linux/installing-ubuntu-810-on-the-eeebox.html")

When i do iwconfig the interfaces shows up as ra0 but nothing on ifconfig and /etc/network/interfaces has no listing for the adaptor at all, i know i need to set it up in here but i dont know how!

How do i do it?

---

### Post by t4thfavor on 2009-06-30
For starters try sudo dhclient ra0 and see if you are getting an address. If not you need to associate with the AP try something like this::
```

sudo iwconfig ra0 essid "InDaHouse" key yournetworkencryptionkey

```
then try to get another dhcp lease. If you still can't you may have other issues.

---

