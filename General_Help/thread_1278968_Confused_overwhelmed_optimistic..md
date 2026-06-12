---
title: "Confused overwhelmed optimistic."
date: 2009-09-30
forum: General Help
---

### Post by Ribiero on 2009-09-30
First of all thankyou for reading this post, any help or suggestions will be very gratefully recieved. I have been keen to try ubuntu for quite a while and recently came into possesion of an old omnibook p3, ideal for my purposes. Anyway the omnibook has no built in optical drive and the external drive doesnt appear to work. No worries I thought, just connect the harddrive to my computer and install ubuntu on that. This caused grub failure for my windows laptop (now remedied) but has enabled Ubuntu 8.04 to be installed and running on the omnibook. I am very pleased, it runs so much faster than the paltry spec would suggest. I am struggling with two things, installing programs, and the internet. I would really like to install vlc. I cannot locate it with synaptic and not being able to connect to the internet means I cant get it that way. The omnibook recognises external usb harddrives and flashdrives, though the bios wont boot from them. Is there a way of installing programs from a flashdrive and terminal?. Apologies if this rambling post isnt very clear, any suggestions would be ace. Regards Rob.

---

### Post by 13thSlayer on 2009-09-30
Internet: As to that i have two suggestions:
These 3 packages will allow a VPN-based connection:
pptp-linux
network-manager-pptp
menu
You need only these 3 AFAIK.
To connect via a modem... well, not sure if it can be done any longer, but there is a program for that called gnome-ppp.
All the packages can be found @ [http://packages.ubuntu.com]("http://ubuntuforums.org/packages.ubuntu.com")
There you go, really hope i helped.

---

### Post by P4man on 2009-09-30
I guess what it boils down it is fixing your internet connection first. Are you trying wired or wireless? For either, provide the exact type of network adapter. you can find that by opening a terminal and typing:

```
lspci
```

first character is a lowercase letter L; its short for "List PCI" I guess.

(should it be a usb device, then use "lsusb" instead)

---

### Post by ianmillington on 2009-09-30
Hi Rob and welcome

You could take a look at this

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

I have not used it myself but would envisage that the source machine would have to be running ubuntu for you to set up the CD (or flash drive I imagine). I expect your other machine is running windows? If so apt on CD Probably won't work for you.

The most logical solutions for you enjoy ubuntu will, I think be, either

1. Get the omnibook onto the 'net. You haven't indicated what the problem is here. What networking hardware do you have? Presumably because of its age it only has a built in (win)modem? If so, does the machine have a PCMCIA slot in which case you should be able to get a very cheap card that will work (assuming you have broadband of course)

2. Set up your other machine to dual-boot.

Hope this helps a bit

ian

---

### Post by Commander_Keen on 2009-09-30
since you have USB.
I would try Netgear 111v2 or 3; It should work out of the box More or less

---

### Post by Ribiero on 2009-09-30
Wow what a response. Thanks to all. I have a linksys pcmia wifi card which lights up but isnt recognised in network settings. when I type "lspci" ubuntu responds "02.00.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO wireless card (rev o1). Apologies if i am being a bit newb, or even computer iliterate. i cannot find any form of modem port on the omnibook. I do have another type of pcmia card which came with it, a V34 + fax card which I guess could be useful if i knew what it was and how to use it. Regards Rob.

---

### Post by P4man on 2009-09-30
Bad luck. I cant find anything to get that wireless card working on linux, except using  "ndiswrapper". For wireless cards, you can use windows drivers, but to do that, you have to install "ndiswrapper" first, and doing that without internet connection can be a bit tedious.

So, first question: can you get a (temporarily) wired internet connection, or borrow a USB wifi stick that does work from someone? Would make it easier to fix the wifi.

If not, you'll have to download ndiswrapper package (and dependencies, if any), as well as the windows driver for your card from a different computer, put it on a usb stick and install.

---

