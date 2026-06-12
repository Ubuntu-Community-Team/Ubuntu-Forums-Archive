---
title: "Wireless network not recognized"
date: 2010-08-29
forum: General Help
---

### Post by matthatesspam on 2010-08-29
I'm having an issue with my wireless router not being recognized in Ubuntu Netbook Remix. When I boot into it, it won't display my network. The funny thing is that my neighbor's network is recognized just fine.

Also, I can discover and connect perfectly fine in Windows 7, just not in Ubuntu. This is the only thing holding me back from installing it and diving in.

Any help will be appreciated. :)

Edit: My netbook is a Lenovo Thinkpad X100e, if that makes any difference.

---

### Post by ubun_two on 2010-08-29
A couple of notes:

1, If there are a lot of wireless network in the area, some of the network may be under "More networks" in the menu (left click on the network icon in the indicator).

2, What happens if you manually enter the information about your rounter?  You can enter SSID, security type, and encryption key (if needed) by doing "Create New Wireless Network..."

---

### Post by matthatesspam on 2010-08-30
I looked for the "More networks" menu you mentioned, but it wasn't there. The only network being displayed is my neighbor's. As for manually entering my wireless network info, I tried that too and failed.

---

### Post by ubun_two on 2010-08-30
Is the router working properly?  Can you connect to it wirelessly using another PC?  What about when you connect to it using ethernet cable?

---

### Post by matthatesspam on 2010-08-30
The router is working properly and I can connect to it through my computer when I boot into Windows 7.

I went out on a limb and installed the live CD of desktop 10.04 on my thumb drive to see if it would make any difference, and when I booted into the desktop 10.04 it discovered and connected to my wireless network without any trouble.

I would stick with the desktop edition, but I have a netbook and I'd like to stick with the netbook remix.

---

### Post by ubun_two on 2010-08-31
I am surprised that desktop or netbook edition matters with networking.

You could install the desktop edition and install netbook packages through synaptic...

---

### Post by matthatesspam on 2010-08-31
How would I go about installing the netbook interface once I've installed desktop edition?

Edit: Solved the problem by following [these instructions]("http://justinsomnia.org/2010/02/ubuntu-on-a-lenovo-thinkpad-x100e/").

---

