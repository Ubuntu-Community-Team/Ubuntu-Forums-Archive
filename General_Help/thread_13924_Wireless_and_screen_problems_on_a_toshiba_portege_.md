---
title: "Wireless and screen problems on a toshiba portege 4000"
date: 2005-02-03
forum: General Help
---

### Post by supergrapeman on 2005-02-03
Don't like to winge, but I'm having problems getting the Jan 2005 Ubuntu live hoary release work properly on a toshiba portege 4000. I should point out that other live debian CD's like Mepis, Kanotix and knoppix work just fine.

Problem 1: no wireless. Wireless does not work at all. Looking at the boot up messages, Ubuntu live figures out information about the wireless connection, tries to set it up as eth1, but when I get into the desktop, eth1 is not there. iwconfig commands confirm there is no wireless present. What should my next step in resolving this be?

FYI: I'm running debian unstable right now on this laptop, and the wireless card is picked up fine:

orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
eth1: Station identity 001f:0001:0006:000e
eth1: Looks like a Lucent/Agere firmware version 6.14
eth1: Ad-hoc demo mode supported
eth1: IEEE standard IBSS ad-hoc mode supported
eth1: WEP supported, 104-bit key
eth1: MAC address 00:02:2D:45:6B:5E
eth1: Station name "HERMES I"
eth1: ready
eth1: index 0x01: Vcc 3.3, irq 11, io 0x0100-0x013f
eth1: New link status: Connected (0001)

Problem 2: screen size is 640x480. Should be 1024x768, but selecting different options (such as fb1024x768) at startup have no effect.

These problems are a pity, and are rather offputting. Any help welcome!

---

### Post by supergrapeman on 2005-02-05
Ok, the screen problem is fixed by the very latest (Feb 5th) Live CD. Wireless problem remains. Anyone help?

By the way, an lsmod command shows that the orinoco and orinoco_cs modules are loaded. It's just that eth1, which is detected at boot time has disappeared. This is annoying!

---

### Post by alastair on 2005-02-05
The output of :

ifconfig -a
iwconfig

might be useful.

---

### Post by supergrapeman on 2005-02-05
[QUOTE=alastair]The output of :

ifconfig -a
iwconfig

might be useful.[/QUOTE]

This is where it gets horrible. First, though, here is the output from ifconfig -a and iwconfig:

root@ubuntu:/home/ubuntu # ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:00:39:0F:72:D6
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.255.255.255
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1146 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1146 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:92826 (90.6 KiB)  TX bytes:92826 (90.6 KiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

root@ubuntu:/home/ubuntu # iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

The reason it gets horrible is this - every time the tosh is running off the mains, or running off batteries with a lot of charge, I get the above i.e no wireless. If the tosh is running off batteries with little charge, when it powers up the screen is dimmer, everything runs much slower (some sort of low battery power save mode), but I do get wireless - eth1 pops up when I run an ifconfig -a, the PC associates with my AP, gets an IP address, all automatically.

Some sort of race condition? Eek?

---

### Post by alastair on 2005-02-05
I don't actually use Ubuntu (yet), but tried the latest live CD last weekend on my laptop (thinkpad). I had some "fun" with wireless as well.

If I lost (or hosed) the network, I tried to do an "rmmod" on the wireless module (for me "ipw2100"), then a "modprobe" on it. Do a "tail -f" of /var/log/syslog in a separate shell and see what happens.

For your screen res problem, it might be worth checking the settings in /etc/Xorg.conf. If you play with resolution, take a backup copy of this file before.

---

### Post by supergrapeman on 2005-02-06
[QUOTE=alastair]I don't actually use Ubuntu (yet), but tried the latest live CD last weekend on my laptop (thinkpad). I had some "fun" with wireless as well.

If I lost (or hosed) the network, I tried to do an "rmmod" on the wireless module (for me "ipw2100"), then a "modprobe" on it. Do a "tail -f" of /var/log/syslog in a separate shell and see what happens.

For your screen res problem, it might be worth checking the settings in /etc/Xorg.conf. If you play with resolution, take a backup copy of this file before.[/QUOTE]

Thanx. The very latest livecd cures the screen problem, so I'm only fighting one problem. I have tried removing and reinserting modules, to no avail. Will try again, and post what syslog says.

---

### Post by supergrapeman on 2005-02-06
[QUOTE=alastair]I don't actually use Ubuntu (yet), but tried the latest live CD last weekend on my laptop (thinkpad). I had some "fun" with wireless as well.

If I lost (or hosed) the network, I tried to do an "rmmod" on the wireless module (for me "ipw2100"), then a "modprobe" on it. Do a "tail -f" of /var/log/syslog in a separate shell and see what happens.

For your screen res problem, it might be worth checking the settings in /etc/Xorg.conf. If you play with resolution, take a backup copy of this file before.[/QUOTE]

Ok, tried this unloading and reloading the modules via the rmmod and modprobe commands, whilst monitoring syslog. Nothing appears in syslog.

To add a further twist to this problem, booting with the wireless card switched off gets stuck (the liveCD prompts for an SSID mid boot, and whatever you enter does not work (because the wireless card is switched off), so it fails to connect, and prompts you again and again etc...). No big deal, this, I suppose.

Whate grates is that the wireless card is detected ok during boot, and actually goes and picks up the DNS settings via DHCP, before the wireless is knocked out by something later in the boot sequence.

---

### Post by MickeMisar on 2008-04-28
Hello

I am using a Toshiba Portege 4000 myself and have problems with the screen resolution when installing the latest release of Ubuntu 8.04. 

I can't even choose any screen resolutioon larger than 800x640. The result gets quite interesting since this means that the user interface only takes up the center of the laptop screen.

When running Windows XP, I have to force the screen resolution to 1024x768. When looking in Device Manager, under screen, one can see that there seem to be two different screens. Could this be the problem? 

Best regards
/Thomas

---

