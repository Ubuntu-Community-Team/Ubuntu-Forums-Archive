---
title: "constently losing internet and can't kill firefox-bin"
date: 2011-05-15
forum: General Help
---

### Post by someitalian123 on 2011-05-15
I keep losing my internet. I'm using ndiswrapper with a Netgear wg311v3, according to the compatibility list it should work fine. I've tried the Marvell Libertas driver and the Netgear driver, both of them work until I lose internet. I usually lose internet while streaming video. I'm using ndisgtk, in the past I had just installed the driver form the command line, but either way I install it I have this problem. The only way to get my internet back is to restart the computer, but the problem with that is that my computer hangs on shutdown because firefox-bin is still running. I can't kill firefox-bin, I've tried kill -9, pkill -9, and killall -9 none of which work. I tried adding sudo in front of it but when ever I use sudo it hangs at the command line and I have to close the command line and open up another if I want to use any more commands. What should I do.

---

### Post by SecretCode on 2011-05-15
One possibility is that the MTU value (Maximum Transmission Unit) needs to be smaller. By default it's 1500 on Ethernet but on wireless it needs to be 1492 ... or 1472 ... or even 1450. If it's too high (meaning higher than what your router treats it as) you will get packet loss and possibly driver lockup when large packets are sent.

Unfortunately I can't find a definitive site to direct you to. These pages provide some info: [[Solved] Wireless network mtu setting (Page 1) - Help & Support - CrunchBang Linux Forums](http://crunchbanglinux.org/forums/topic/7083/solved-wireless-network-mtu-setting/) ... [How to Change MTU (Maximum Transmission Unit) of network interface in Ubuntu Linux*|*Ubuntu Geek](http://www.ubuntugeek.com/how-to-change-mtu-maximum-transmission-unit-of-network-interface-in-ubuntu-linux.html)

---

### Post by someitalian123 on 2011-05-15
Thank you for providing me with some information other than I guide to setting ndiswrapper. I'll give it a try and then I'll try to reproduce the problem. I don't know much about linux or networking, will changing the mtu make my internet connection slower?

Edit:

I forgot to ask, how do I know if I should set the mtu to 1492 or 1472 or 1450? Is their some kind of test I can run to see what number works best for my hardware?

---

### Post by SecretCode on 2011-05-16
> **someitalian123 said:**
> I forgot to ask, how do I know if I should set the mtu to 1492 or 1472 or 1450? Is their some kind of test I can run to see what number works best for my hardware?

The accepted procedure is to reduce it until you don't get the problems any more.

Although, wait ... there is a definite way to tell ...
run (replace 192.168.0.1 with your router's IP address)
```
ping 192.168.0.1 -M do -c 1 -s 1500
```
This will send a ping with the DF "do not fragment" bit set, and it will result in an error because the packet size (1500+control) is too large. Keep reducing the -s parameter until it pings successfully.

---

