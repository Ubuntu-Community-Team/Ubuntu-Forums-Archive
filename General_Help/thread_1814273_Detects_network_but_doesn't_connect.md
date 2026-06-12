---
title: "Detects network but doesn't connect"
date: 2011-07-29
forum: General Help
---

### Post by jiri2 on 2011-07-29
Hi. I just downloaded Ubuntu a couple of days ago. I'm not booting it alongside a half broken Windows7 hoping for some way to recover Win7s files before I experiment with a Win7 recovery.

I'm currently using it from a CD, until I figure out what [this]("http://ubuntuforums.org/showthread.php?p=11097823#post11097823") means.

I'd like to connect it to the internet. It says it's detected my home network, and the networks of my neighbours, just like the Vistas, and Win7s I have in the house.

But it won't even detect my modem home page, the typical 192.168.0.1, on the mozilla browser it comes with. On the other hand it even detects the strength of the networks it sees. It knows my home network is stronger than those of my neighbours.

But I can't connect to anything.

The modem is a Sagem Fast 2404. I've gone over this with my DSL's support but they can't do anything for me. When I go to network / network connections I play around with the config because it didnt detect it automatically, but even before I started touching it wouldnt budge.

In Wired it seems to connect instantly. Right now it says last used '2 hours ago'.

I have no wiring. Doesnt make much sense.

In 'Wireless', it detects my wireless and those of my neighbours.

I've interpreted BSSID to be the password of my router. The number that comes alongside 'WPA'.

I don't know what Device MAC adddress is, nor Cloned Mac adress. MTU is set to automatic.. Mode is 'infrastructure'. SSID is what comes under my router beside that term.

'Wireless security' I've interpreted to be what comes alongside the WPA, written under my router. I thought WPA & WPA2 Personal would be appropriate.

Under IPv4 settings, I've tried both with Manual and Automatic (DHCP), despite there being other options.

In Manual I've tried inserting the IP address, the netmask and the gateway I've seen in another PC, a Vista, I have in the house, that's still working.

I introduced nothing in 'DNS Servers', nor in 'Search domains', and tried both with and without the checkbox 'Require IPv4 addressing for the connection to complete'.

I haven't done anything with IPv6.


Are there any suggestions you may have, please, i'm a bit desperate and clueless! :-/

---

### Post by grahammechanical on 2011-07-29
First the good news.

You are running from the live CD and it recognizes your wireless adapter and is using it to detect wireless networks in range. This is good news because it means that when you install ubuntu to the hard disc your wireless adapter will work out of the box, as people say.

But, because you are running Ubuntu from the live CD it does not store your network connection settings. It cannot and will not automatically connect to your wireless network unless you make the connection.

With a hard disc installation your settings will be remembered but first you have to make the connection. How, is the stupid OS to know which is your wireless router out of all the wireless routers in range unless you tell it so? Then you have to edit the connection to set it to connect automatically.

So, I suggest that you select your wireless network from the list of networks and fill in the fields in the box that appears. When asked to authenticate the connection put in the wireless key or pass phrase, also called WPA-PSK. It is usually 10 characters long. Yes, WPA & WPA2 personal should be sufficient for security. The connection settings in the computer must be set to the same encryption method as in the router or the two will not be talking the same language. And let network manager do its stuff.

I know that this works because I tried it with my sister's Sky router and a live CD. All I need was the WPA-PSK key from a label on the side of the router and I was surfing the Internet with the live CD.

By the way, are you sure that you have the correct url for the modem settings page? My looks slightly different.

Regards.

---

