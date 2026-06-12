---
title: "change Wireless interface name, ra0 --&gt; wlan0"
date: 2006-01-20
forum: General Help
---

### Post by W04tah on 2006-01-20
Hi,

I am experimenting a bit with iptraf, version 2.7 supports wireless interfaces.

However, it only supports wlanx interfaces(x is the number)

My rt2500, with a recent cvs daily driver, is known as ra0. I want to keep this driver because of packet injection with aireplay, so i want to change the interface name from ra0 to wlan0.

How to do this? I already tryed to modify /etc/modules.conf and /modprobe.d/rt2500, which contains the alias ra0 rt2500, but changing it to wlan0 didnt have an effect in both files.

Thanks in advance!

I find those forums a bit more usefull then the dutch ones i think, because these contain more posts and information:)

W04tah

---

### Post by Quirky on 2006-01-20
I am pretty sure that you can use /etc/iftab to do this. See "man iftab" for details!

---

### Post by W04tah on 2006-01-21
Thank you, it worked:)

It only displayed my wired NIC, eth0, so i added a line:
wlan0 mac "the mac address"

Just finished this post so that someone else can use it with the search function;)

---

