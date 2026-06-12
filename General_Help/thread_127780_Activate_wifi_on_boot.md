---
title: "Activate wifi on boot"
date: 2006-02-09
forum: General Help
---

### Post by brain.g on 2006-02-09
My wireless card on my laptop gets picked up by Ubuntu OK, I just have to manually go into the Connection Properties, then click on Configure, then Activate the connection every time I reboot.  For whatever reason as well, Ubuntu grabbed my wireless and added eth1 and eth2 both for wireless connections, while eth2 is the only one that will actually activate and connect.   I'm willing to live with having 2 wireless connections in there when I only have 1 card and only 1 works, but having to manually activate it after every reboot is a pain.

I've edited the /etc/network/interfaces file and put the (auto eth2) in front of iface ..., but still no luck.  Any ideas?

---

### Post by dcstar on 2006-02-10
[QUOTE=brain.g]My wireless card on my laptop gets picked up by Ubuntu OK, I just have to manually go into the Connection Properties, then click on Configure, then Activate the connection every time I reboot.  For whatever reason as well, Ubuntu grabbed my wireless and added eth1 and eth2 both for wireless connections, while eth2 is the only one that will actually activate and connect.   I'm willing to live with having 2 wireless connections in there when I only have 1 card and only 1 works, but having to manually activate it after every reboot is a pain.

I've edited the /etc/network/interfaces file and put the (auto eth2) in front of iface ..., but still no luck.  Any ideas?[/QUOTE]
Is this any use:

[http://ubuntuforums.org/showthread.php?t=122809](http://ubuntuforums.org/showthread.php?t=122809)

---

### Post by brain.g on 2006-02-14
I went ahead and gave it a shot anyways, but no luck.

---

### Post by brain.g on 2006-04-08
Any takers?  I still have this problem with Ubuntu on a laptop and wireless connections.

---

### Post by elamericano on 2006-04-08
You've removed all references to eth1 in the interfaces file?

---

### Post by Snocrash on 2006-04-08
Hmmmm.....

Could you post your interfaces file????

There are a couple of scripts you can use to bind IP addresses and interfaces to MAC addresses if you have more then one card or setup....

I travel alot so my laptop has multiple interfaces (wired and wireless) and setups (DHCP and static) depending on where I am and what I am doing.

I ended up writing an interface file for each option (4 of them) and then writing a little script the runs at boot and asks me wich one I want and then links that file to /etc/network/interfaces.

I know...seems like a lot of work, not really tho, and networking comes up clean the way I want it at boot.

Is it a PCMCIA card?????

I have had issues in the past with other distros and pcmcia cards. Usually I had to change the boot sequence to bring up PCMCIA before networking so the card would configure and start. Have not had this issue with Ubuntu tho.

---

### Post by brain.g on 2006-04-08
[QUOTE=Snocrash]Hmmmm.....

Could you post your interfaces file????[/QUOTE]

As of right now the wireless connection is not working at all.  Even when I activate it, it no longer will connect.  Here is my interfaces file currently.  I turned off WEP for right now to make this a little easier, figure I can come back later and turn it back on.

-----
# This file ...
# and how ...

# The loopback network interface
auto lo
iface lo inet loopback

# This is ...
# They will be ...
mapping hotplug
script grep

# The primary network interface
iface eth0 inet dhcp

iface eth2 inet dhcp
wireless-essid MYROUTER

auto eth2
-----

[QUOTE=Snocrash]Is it a PCMCIA card?????[/QUOTE]

Yes, it's a Cisco wireless PCMCIA card.  When I plug it into the PCMCIA slot on the laptop, Ubuntu seems to pick it up and adds two wireless connections, eth1 and eth2.  So when I go into the main menu, SYSTEM >> ADMINISTRATION >> NETWORKING, I see eth2, eth1, eth0, and ppp0.  eth 0 is the wired internal connection and ppp0 is the internal modem connection.

---

### Post by Snocrash on 2006-04-09
Ok..... I don't quite understand the eth1 and eth2 thing, but I have never used a cisco card so I don't know if this is normal.

That being said, I will ask a few dumb question.....

1. Is your gateway set to eth2 ?
2. What is the output of "sudo ifconfig" ?
3. What is the output of "sudo iwconfig" ?
4. What is the output of "lsmod" ?
5. What is the output of "dmesg | grep pcmcia" ?
6. did you install linux-wlan-ng or something else???
7. Can you ping you router's IP address ( ping -c4 xxx.xxx.xxx.xxx) ?
8. Can you ping a computer on the same network ?
9. Can you ping google (ping -c4 [www.google.com](www.google.com)) ?
10. If you boot the machine with the card inserted does it work, if not do a "sudo /etc/init.d/networking restart", then does it work ?

The reason for question 6 is because I have had problems with wlan in the past. Sometines I can get it to work fine, sometimes not. And after installing it, it can take some work to get everything working after you remove it.

If 10 works, it is probably a boot sequence problem.

The rest of them are just qathering info and seeing how far it works if at all.

As far as I can tell, you interfaces file is fine. Here is my static one. the commented DHCP stuff at the bottom is for DHCP at work or when traveling. May want to "map eth2" under mapping. Don't know if it will help because I am not sure what is wrong.

-----------------------------------------------------

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth1

# The primary network interface
iface eth1 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        address 192.168.1.218
        netmask 255.255.255.0
        gateway 192.168.1.1
        wireless-key XXXXXXXXXX

auto eth1

#iface eth0 inet dhcp

#auto eth0

---------------------------------------------------------

Hope some of this helps.


-Sno

---

### Post by smokey_ketchup on 2006-04-10
I won't pretend to be an expert, but I you could try the following changes to your /etc/network/interfaces file, with the changes in red:

```

# This file ...
# and how ...

# The loopback network interface
auto lo
iface lo inet loopback

# This is ...
# They will be ...
mapping hotplug
script grep
[COLOR="Red"]map eth2[/COLOR]

# The primary network interface
iface eth0 inet dhcp

iface eth2 inet dhcp
wireless-essid MYROUTER

[COLOR="Red"]#auto eth2[/COLOR]
```


Commenting out the auto eth2 should prevent  the interface being brought up at the starting network interfaces... , before PCMCIA has been started. Adding the map eth2 should let hotplug deal with the bringing up of the interface, which will be boot time, if you have the card inserted.


Again I am not an expert, but this is some advice that I have picked up when trying to solve my own wireless problems, and I only offer this advice because it involves minimal changes to your system.


Hope this helps

---

### Post by brain.g on 2006-05-31
Still no luck over here.  Not sure if anyone else has a possible solution?

---

