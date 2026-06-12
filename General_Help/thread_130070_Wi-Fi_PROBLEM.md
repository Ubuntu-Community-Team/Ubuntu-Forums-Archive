---
title: "Wi-Fi PROBLEM"
date: 2006-02-15
forum: General Help
---

### Post by rosvit on 2006-02-15
hi people, 
 i have problem with connecting on my wi-fi network from my notebook with ubuntu 5.10. notebook have ralink rt2500 wi-fi card.

on my router i have set ascii 128 bit wep key. authentification type is:  shared key. channel is 2.
i have set everything correctly on notebook (ssid, ip, mask, gateway,dns), but network i still cannot connect on net. on that same notebook is ms windows installed also and there are no problems with wi-fi.

please help. i was thinking that in ubuntu it is impossible to set (or i don't know where) that key is 128 bit and it is shared. also problem should be with channel (is not 1, but 2). i don't know if i am right, because i cannot change settings of router because other other computers on network will not work. 
 THANK YOU VERY MUCH...

---

### Post by soonindallas on 2006-02-15
does your file etc/network/config correctly reflect the shared key management ?

type ```
cat etc/network/config
``` and post the results.

---

### Post by gosh on 2006-02-15
Can you ping your router, other computers on the network or internet?

---

### Post by Ramses de Norre on 2006-02-15
What's a shared key? Is it different from just a WEP key?
I've also got problems with WEP, in the GUI networking configuring tool it didn't worked but when I manually changed /etc/network/interfaces it worked just perfect. I added the line "wireless-key ********" there (fill in your key:p).
The channel shouldn't be a problem, he finds it himself. I am operating at channel 11 and didn't had to configure that.

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface ath0 inet static
address 192.168.123.###
netmask 255.255.255.0
gateway 192.168.123.###
wireless-essid RAFAEL
wireless-key ##########

auto ath0

```

This is what my working config is like.

PS: tried checking out /etc/network/config just to check but I don't have such a file.

---

### Post by rosvit on 2006-02-15
[QUOTE=gosh]Can you ping your router, other computers on the network or internet?[/QUOTE]

no, i cannot :(

---

### Post by rosvit on 2006-02-15
[QUOTE=Ramses de Norre]
PS: tried checking out /etc/network/config just to check but I don't have such a file.[/QUOTE]
 i also do NOT have that file...

---

### Post by soonindallas on 2006-02-15
[QUOTE=Ramses de Norre]
PS: tried checking out /etc/network/config just to check but I don't have such a file.[/QUOTE]

ok - I mistyped, but you guessed what I originally meant.

what do you see if you type:```
iwlist scan
```

---

### Post by soonindallas on 2006-02-15
[QUOTE=rosvit]i also do NOT have that file...[/QUOTE]

that's normal, I mistyped. sorry.

---

### Post by jcaceres on 2006-02-15
please execute

ifconfig -a

and put the output ...

---

### Post by rosvit on 2006-02-16
so here are outputs of ifconfig -a and iwlist scan:

ifconfig -a
```
ra0       Link encap:Ethernet  HWaddr 00:90:4B:D7:12:A5
          inet addr:192.168.1.250  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:4bff:fed7:12a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1676 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:65898 (64.3 KiB)
          Interrupt:11 Base address:0x4000
```

iwlist scan:
```
ra0       Scan completed :
          Cell 01 - Address: 00:E0:98:52:B1:14
                    Mode:Managed
                    ESSID:"tatooine"
                    Encryption key:on
                    Channel:2
                    Quality:0/100  Signal level:-40 dBm  Noise level:-206 dBm
```

---

### Post by rosvit on 2006-02-16
please, where can be problem? can be in that i am not using hexcadcimal but ascii wep key?
then the second problem may be SHARED WEP KEY set on router, i haven't found in ubuntu where i can set it.

---

### Post by rosvit on 2006-02-16
finally i have found out where is the problem. combination of SHARED and ASCII wep is total K.O. for ubuntu :S is the would be hex there will be no problems, but i cannot change it to hex, because it is not my router. :confused:  does anyone know about some way to make this combination working? plsss :)

---

### Post by jcaceres on 2006-02-17
Install wifi-radar and try to configure your wi-fi from there

sudo apt-get install wifi-radar

Regards,
JCY

---

### Post by Robor on 2006-02-17
[QUOTE=jcaceres]Install wifi-radar and try to configure your wi-fi from there

sudo apt-get install wifi-radar

Regards,
JCY[/QUOTE]
I've had some flakyness with my wireless adapter.  Sometimes it boots up without getting an IP address and I have to deactivate/activate it for it to grab one.  I'm using the standard 'Administration | Networking' method of configuring my adapter.  Would using this wifi-radar cause an issue/conflict?

---

### Post by jcaceres on 2006-02-17
wifi-radar is to resolve the conflict between  SHARED and ASCII wep.

To connect to my home wireless net i use this script

iwconfig wlan0 essid Wireless.JCY
iwconfig wlan0 key s:<Ascii password>
dhclient wlan0

---

### Post by rosvit on 2006-02-18
[QUOTE=jcaceres]wifi-radar is to resolve the conflict between  SHARED and ASCII wep.

To connect to my home wireless net i use this script

iwconfig wlan0 essid Wireless.JCY
iwconfig wlan0 key s:<Ascii password>
dhclient wlan0[/QUOTE]

thank you, but it isn't working, maybe i set something wrong. :???:

---

