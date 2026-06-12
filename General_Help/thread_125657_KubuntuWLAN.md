---
title: "Kubuntu/WLAN"
date: 2006-02-04
forum: General Help
---

### Post by deluxxx on 2006-02-04
Since a few days my Wireless Inet is not working anymore .
I had the Problem before and didnt find any way how to solve it.
The only way to make the network working again is Installing again and let it autodetect the Network. But i dont want to do that all the time and hope their is away arround could i start the autodetect setup in KDE/Shell ?
The WLAN is using a WEP key
Here the Settings its supposed to use
Ip-address (DHCP=
Standardgateway 172.41.1.2
DHCP-Server 172.41.1.2
DNS Server 172.41.100.1
If i try to set the Settings via Kcontrol (root) it doesnt save the settings for the gateway the WLAN doesnt work (I Set the Key) except i do it via iwconfig -essid 2034562345 
but then it doesnt get the IP via DHCP so i have to set it again with ifconfig
now i can Ping Computers but my Internet is still not working =( .
I appreciate any Help =)

EDIT: Im using a intel 2200bg drivers are up to date

---

### Post by GeneralZod on 2006-02-04
> If i try to set the Settings via Kcontrol (root) it doesnt save the settings for the gateway

Yeah, this is a bug that's biting a lot of people:

[http://ubuntuforums.org/showthread.php?t=111956&highlight=gateway+kubuntu](http://ubuntuforums.org/showthread.php?t=111956&highlight=gateway+kubuntu)

You'll have to edit /etc/network/interfaces manually; the thread above contains an example.

---

### Post by deluxxx on 2006-02-04
Now its working i played around with the Settings but i think it wont work again after the next restart .
I think i still have problems with the Wlankey



iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
  #      address 172.41.101.28
	wireless-key 8037867211
	gateway 172.41.1.2

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet

---

### Post by deluxxx on 2006-02-05
[QUOTE=deluxxx]Now its working i played around with the Settings but i think it wont work again after the next restart .
I think i still have problems with the Wlankey



iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
  #      address 172.41.101.28
	wireless-key 8037867211
	gateway 172.41.1.2

iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet[/QUOTE]

Edit: Like i had expected it Inet Not working =( again

---

### Post by deluxxx on 2006-02-08
If i Set it to Static I successfully restarts the Interface (eth1) but if I try it with DHCP it doesnt work.
If i set a Static Ip address and i try to ping the Gateway it says no Network but i see that the Wireless is ok (at least the Key ...)

---

### Post by deluxxx on 2006-02-15
Still didnt get it working does anybody how to start the NetworkAutoconfiguration which u have to run at the Ubuntu installation when Ubuntu is already installed ( I dont feel like reinstalling it ).
 Thx

---

### Post by GeneralZod on 2006-02-15
Can you re-cap with exactly what the current problem is? Can you get net access, but lose it when you reboot, or can't you get it at all?

---

### Post by deluxxx on 2006-02-15
its weird sometimes i can get it but as soon as i restart its not working again says that i have no connection to the Network . With Windows everything is working fine.
I think the Problem started to occur after I set a specific IP with : "ipconfig eth1   Ip" since then i dont get it working with DHCP and Static Ip address.

---

