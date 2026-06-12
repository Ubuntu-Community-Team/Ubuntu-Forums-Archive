---
title: "wlan0: no IPv6 router present"
date: 2012-02-09
forum: General Help
---

### Post by madeoforanges on 2012-02-09
Hi,

I tried pressing buttons, restarting, and shutting down my system numerous times... and to the point of re-installing Ubuntu to return to its normal state until the terminal screen shows up again. The only thing that boots properly is using Ubuntu's LiveCD. I tried booting from the USB and CDROM drive, but the computer would skip to Ubuntu's boot to terminal screen (if not using the LiveCD).

[http://imgur.com/YfuLe](http://imgur.com/YfuLe)

PS: When I held F12 accidentally instead of F11 because I wanted to boot to BIOs. After that, everything went downhill from there. In addition, I have an ASUS USB-N13 wireless adapter and I removed it when I restarted my computer and terminal error still came up.

Help a brother out. :)

---

### Post by madeoforanges on 2012-02-09
I am waiting for some 911 support because I can't use my system. Is this a uncommon and difficult problem?

---

### Post by lemming465 on 2012-02-10
"system" and "Ubuntu" are a little unspecific.  Can you give us more information about the maker and model, maybe the motherboard, and especially the video?  Which version of Ubuntu are you running? 

E.g. "lspci" output from a terminal window on the live CD would be quite helpful.
("lsb_release -a" will tell you what version you have.)

Your symptoms seem more like a video chip / driver problem.  If you could include the contents of /var/log/Xorg.0.log that would greatly help us diagnose it too.

"wlan0: no IPv6 routers present" is not necessarily an "error", it just means that your wireless card isn't seeing any IP version 6 ICMP router advertisement messages.  This is normal on an IPv4-only network.  It's not actually related to whatever your real problem is.

Does pressing Ctrl-Alt-F2 get you a virtual terminal window with a text-mode login prompt?   If so, try logging in, and running updates along the lines of
```
sudo -i
apt-get update
apt-get upgrade
dpkg-reconfigure xserver-xorg
```

---

### Post by jonobr on 2012-02-10
I was attracted by the interesting thread title, but cant really suggest anything more from what lemming465 posted.

What I will tell you is that with IPv6 coming , nics are designed to support a dual stack now both IPv4 and IPv6 , so when you look at ifconfig you will see an IPv4 address and an IPv6 address which is calculated from the mac address of the device
The nic will then use something called NDP to find other IPv6 capable devices (specifically the router) If it doesn't get a response from the NDP multicast, then you get the error message you see, however, IPV4 will work, IPV6 will also be on there, and it should still work.

You can disable IPv6, however as lemming465 mentioned, this issue is most likely unrelated to the message your seeing
[Here]("http://www.webupd8.org/2010/05/how-to-disable-ipv6-in-ubuntu-1004.html") is an article on disabling IPv6

---

