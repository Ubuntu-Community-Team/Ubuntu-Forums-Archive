---
title: "Some network problems. Need some help please."
date: 2006-03-20
forum: General Help
---

### Post by haaglin on 2006-03-20
Hi. 

A few days ago, I booted the computer, and when i log in i have no network connection. I went into kcontrol, and tried to activate Ath0, my Wlan card, and it just gets disabled right away. but when i try using the Gnome Network tool, i have no problem getting it activated. and i have to do this every time after a reboot/shutdown. i have seen some posts with this, but no solution. is there any?

My other problem is, that my router cant seem to find my hostname. so it wont give me the same ip after a reboot. this worked fine in windows. is there any other place i have to enter the hostname?

---

### Post by mority on 2006-03-20
I can't help you with the first problem.

Regarding the second problem: You have a DHCP server on your router and want to get the same IP address from it everytime you start this particular client, right? This has nothing to do with your hostname 'cause DHCP is on a much lower layer. The DHCP server is mapping MAC addresses to IP addresses. So you have to enter the MAC address of the network interface of your client (you get it with ifconfig) together with the IP address you wish to get for that client into the routers DHCP configuration.

---

### Post by haaglin on 2006-03-20
[QUOTE=mority]I can't help you with the first problem.

Regarding the second problem: You have a DHCP server on your router and want to get the same IP address from it everytime you start this particular client, right? This has nothing to do with your hostname 'cause DHCP is on a much lower layer. The DHCP server is mapping MAC addresses to IP addresses. So you have to enter the MAC address of the network interface of your client (you get it with ifconfig) together with the IP address you wish to get for that client into the routers DHCP configuration.[/QUOTE]

There is no such configuration in my router, and everything is the same in the config of the router, as when i used windows. but now in the main window, it says "unknown" on the host name of my computer.

---

### Post by randcoop on 2006-03-20
There are two files that you may need to work with.  I say may, because it's possible that once the first one is correct, the second will set itself.  Working with kcontrol on this rarely works.  You'll need to work in the konsole.  For both files, you'll need to work as root (so to edit the files, you'll use sudo kwrite to get to your file editor).

The first file to look at is /etc/network/interfaces.  I'm assuming that your network interface card is being recognized as ath0 or wlan0.  The line you need in the interfaces file is:

iface ath0 inet dhcp

Substitute wlan0 for ath0 if appropriate.  If you're not using dhcp (you permanently assign your ip address for the card), then your line would say

iface ath0 inet static

If you use static, then you'll need to assign the other aspects of the card by adding lines underneath that first one like:

address 192.168.0.12

for the ip address of your card and

gateway 192.168.0.1

for the ip address of the gateway.  You might also want to put

wireless-essid any

or whatever for the essid.

Anyhow, this is where all the interface stuff goes.  Once the listing is there, then you should be able to run

sudo dhclient

or 

sudo ifup ath0

to get on the internet.

If that doesn't work and you think you need to manually add a DNS, then the file to edit is /etc/resolv.conf.

There, simply add the line

nameserver xxx.xxx.xxx.xxx

obviously filling in the actual nameserver address.  If there is more than one, the others go on lines of their own.  

Once that's there, together with the interface, try running dhclient or ifup/down again.

If all this works, you can make the connection automatic at boot by addiing 

auto ath0

as a line (before the iface line) in your /etc/network/interfaces file.

---

### Post by haaglin on 2006-03-20
Hi. thanks for the reply. All of this is in the interfaces file, but the line auto ath0 is below all of it. Maybe that is the problem? I have no problem manually getting the network working, the problem is getting it to work with KDE. i will move the line above and see.

---

### Post by haaglin on 2006-03-20
No, that didn't work.

---

### Post by haaglin on 2006-03-20
Figured it out! found this post [http://ubuntuforums.org/showpost.php?p=545735&postcount=17](http://ubuntuforums.org/showpost.php?p=545735&postcount=17), and changed this

> 
iface ath0 inet dhcp
wireless-mode managed
wireless-essid default

iface eth0 inet


into this:
> 
iface ath0 inet dhcp
wireless-mode managed
wireless-essid default

iface eth0 inet **dhcp**


And added ath0 to the auto lo line. (auto lo ath0)

Thanks to everyone who helped.

---

