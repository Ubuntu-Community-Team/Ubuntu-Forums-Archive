---
title: "Cannot Connect to Internet"
date: 2011-06-07
forum: General Help
---

### Post by PsyclonJohn on 2011-06-07
Earlier today, I decided to make one of my laptops to run Ubuntu only since it was duel boot with Win 7 (Win 7 corrupted and I didn't need it anymore), so I put in my Ubuntu 10.04 disk and I wasn't able to connect to the Internet  (wired and Wireless). I wasn't sure if it was an OS or Computer problem (Unsure still, but I'll let you know what I've tried so far). 

After hours of looking through tutorials on how to fix this problem, I failed to come up with any solution, so I tried out Linux Mint, Puppy Linux, Ubuntu 11.04, and CentOS (I was very busy!) and every single distro wouldn't allow me to connect to the Internet except for Puppy Linux on the first time installation. After several minutes, it disconnected and I couldn't access the Internet anymore. 

I need to install Broadcom STA Drivers, which appear accessible in Linux Mint (very similar to Ubuntu) but cannot activate them. I tried going to their website and downloading the tar.gz but had no luck... got a few errors. I downloaded the drivers using the computer I'm on now (my desktop) and transfered them via USB stick. 

But if it helps, I'll post my info:

```


john@Inspiron-1545 ~ $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:25:64:5c:f2:67  
          inet6 addr: fe80::225:64ff:fe5c:f267/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:43584 (43.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7756 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7756 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:615404 (615.4 KB)  TX bytes:615404 (615.4 KB)

This is the important information from the 'lspci' command:

09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)


```Anyone who knows how to fix this, please let me know. I've about tried everything, but maybe theres something I left out?

---

### Post by Bucky Ball on 2011-06-07
In Ubuntu, get online with a cable. You will be offered updates and your card should be picked up. Check System>Administration>Additional Drivers. Anything disabled?

I am presuming you are talking about getting online with wireless? Cable works okay? That wireless card should work virtually out-of-the-box but you need to get online with a cable first. Catch 22. *Should* be quite simple.

If this doesn't work, System>Administration>Synaptic Package Manager. Search for and install b43-fwcutter and firmware-b43-installer. Reboot.

If there is a wireless on/off button on the computer itself, you have it switched on? Sounds obvious but you never know.

---

### Post by PsyclonJohn on 2011-06-07
I really wish it was that easy. I been trying to connect with a cable all day. I cannot connect with cable and wirelessly. I really don't know what it could be... I have two other computer running Ubuntu and the Internet is fine.

---

### Post by dragonfly41 on 2011-06-07
I've had problems with cable connection on my Inspiron 1720 (I see that you have Inspiron too).  

we also have the same Network Controller ..

[COLOR=Navy]0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)[/COLOR]

....

First the basics ...

It may be that you've been trying connections while your cable modem remains powered.

To [COLOR=Navy]force a reset of your IP address[/COLOR] ... have you tried shutting down the power to your cable modem and pulling out cable to your Inspiron?   This advice usually comes as first troubleshooting tip from your ISP provider.

....

After a couple of minutes restore the power to cable modem, reconnect to Inspiron and reboot.

....

Then System > Preferences > Network Connections

Under wired tab do you see "Auto eth0"

---

