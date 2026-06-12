---
title: "Static IP"
date: 2010-02-16
forum: General Help
---

### Post by Zynon on 2010-02-16
So I am fairly new to Ubuntu and I am wanting to set my Ubuntu box up with a static IP. When I say static I.P. I mean a local static I.P.   I have done some looking from google and found that I have to use the sudo vi /etc/network/interfaces  command to edit the file.

Here is where I am having the problem. I have a basic Linksys home network and I do not know or understand what network or broadcast mean? 
I understand IP SUBNET and gateway but have no clue what those values are supposed to be.

Here is my network Information if someone would be so kind as to tell me what to put there and what they mean and for.

I.P 192.168.1.104
Subnet 255.255.255.0
gateway 192.168.1.1


Thank you in advance

---

### Post by 2hot6ft2 on 2010-02-16
I have a linksys router as well but I'm using dd-wrt firmware on it so your setup will be different but in a web browser log onto your router at 192.168.1.1 just put it in the address bar of your browser and hit enter.

This is how it's done in dd-wrt so yours will not be the same but the principles are the same.

In DD-WRT v24 you would go to Services > Services > Static Leases and click on Add, this will open 3 boxes where you can put your adapters
"MAC Address - A description or name like Server or Client (no spaces allowed) - IP Address you want the adapter to have, like 192.168.1.104".
More ifo and a guide here: [http://www.dd-wrt.com/wiki/index.php/Static_DHCP](http://www.dd-wrt.com/wiki/index.php/Static_DHCP)
Be sure to set your static IPs outside of your automatic DHCP address range (see the above guide).
Click on "Apply Changes" at the bottom of the page to make it take effect immediately. The router will reboot itself and the changes will be in effect. So wait for it to reboot.

Your router is assigning IP Addresses to the computers on your local network so that is where you want to change it.
You can find out your adapter MAC Address by going to a terminal
Applications > Accessories > Terminal
and putting in
```
ifconfig
```
eth0 will be your wired connection adapter
wlan0 "your first wireless adapter each additional adapter will go up a number like wlan1, wlan2 etc.."

---

### Post by giammy on 2010-02-16
> **Zynon said:**
> So I am fairly new to Ubuntu and I am wanting to set my Ubuntu box up with a static IP. When I say static I.P. I mean a local static I.P.   I have done some looking from google and found that I have to use the sudo vi /etc/network/interfaces  command to edit the file.

Here is where I am having the problem. I have a basic Linksys home network and I do not know or understand what network or broadcast mean? 
I understand IP SUBNET and gateway but have no clue what those values are supposed to be.

Here is my network Information if someone would be so kind as to tell me what to put there and what they mean and for.

I.P 192.168.1.104
Subnet 255.255.255.0
gateway 192.168.1.1


Thank you in advance

See System->Preferences
Select the ethernet cart (probably eth0) and press edit
then click on ipv4 settings, and select Manual configuration

you should get a mask to insert your infos

bye

---

### Post by Zynon on 2010-02-16
> **2hot6ft2 said:**
> I have a linksys router as well but I'm using dd-wrt firmware on it so your setup will be different but in a web browser log onto your router at 192.168.1.1 just put it in the address bar of your browser and hit enter.

This is how it's done in dd-wrt so yours will not be the same but the principles are the same.

In DD-WRT v24 you would go to Services > Services > Static Leases and click on Add, this will open 3 boxes where you can put your adapters
"MAC Address - A description or name like Server or Client (no spaces allowed) - IP Address you want the adapter to have, like 192.168.1.104".
More ifo and a guide here: [http://www.dd-wrt.com/wiki/index.php/Static_DHCP](http://www.dd-wrt.com/wiki/index.php/Static_DHCP)
Be sure to set your static IPs outside of your automatic DHCP address range (see the above guide).
Click on "Apply Changes" at the bottom of the page to make it take effect immediately. The router will reboot itself and the changes will be in effect. So wait for it to reboot.

Your router is assigning IP Addresses to the computers on your local network so that is where you want to change it.
You can find out your adapter MAC Address by going to a terminal
Applications > Accessories > Terminal
and putting in
```
ifconfig
```

Thanks for the information however, the router part is not where I am having the problem. I don't understand what broadcast and network values are supposed to be.
The other 3 values I understand it's those 2 that confuses me.

---

### Post by 2hot6ft2 on 2010-02-16
> **Zynon said:**
> Thanks for the information however, the router part is not where I am having the problem. I don't understand what broadcast and network values are supposed to be.
The other 3 values I understand it's those 2 that confuses me.
The router will set them but
Bcast:192.168.1.255 
Mask:255.255.255.0

---

### Post by 2hot6ft2 on 2010-02-16
If you're determined to set it up in the network interfaces file it would look like this

> # The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

Is that what you want?

---

### Post by undecim on 2010-02-16
Here is part of that file from my server. I'm also using a linksys router, factory firmware. I've added comments explaining it all ```
        address 192.168.1.18	# Static IP address. I kept the last byte under 100 to prevent conflicts with DHCP clients
        netmask 255.255.255.0	# indicates which bits of the address are shared by all hosts on the network (almost always the same value as this on a home network)
        network 192.168.1.0	# This is the result of a bitwise AND of netmask and address (In other words, the numbers of the IP that are the same for all hosts on the network)
        broadcast 192.168.1.255	# This is the highest value that fits into your network (packets from to this IP are picked up by all network hosts)
        gateway 192.168.1.1	# Your router's IP address (almost always the lowest value other than 0 that fits into the network)
```Yours should be identical, except with possibly a different static IP.

---

### Post by 2hot6ft2 on 2010-02-16
> **undecim said:**
> Here is part of that file from my server. I'm also using a linksys router, factory firmware. I've added comments explaining it all ```
        address 192.168.1.18	# Static IP address. I kept the last byte under 100 to prevent conflicts with DHCP clients
        netmask 255.255.255.0	# indicates which bits of the address are shared by all hosts on the network (almost always the same value as this on a home network)
        network 192.168.1.0	# This is the result of a bitwise AND of netmask and address (In other words, the numbers of the IP that are the same for all hosts on the network)
        broadcast 192.168.1.255	# This is the highest value that fits into your network (packets from to this IP are picked up by all network hosts)
        gateway 192.168.1.1	# Your router's IP address (almost always the lowest value other than 0 that fits into the network)
```Yours should be identical, except with possibly a different static IP.
That's a good explanation of it.

---

### Post by audiomick on 2010-02-16
Hallo.
It is worth your while having a look to see if your router can reserve an IP address. That is how I do it.
The router needs to know the MAC address of your Ethernet connection, and then always assigns the same IP address to it via DHCP. I saves you having to mess around with all of that stuff. 

Unfortunately, not all routers can do it, but it is worth a look.

---

