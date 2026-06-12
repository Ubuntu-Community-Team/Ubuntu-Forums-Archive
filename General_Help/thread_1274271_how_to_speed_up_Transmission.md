---
title: "how to speed up Transmission ?"
date: 2009-09-24
forum: General Help
---

### Post by doron387 on 2009-09-24
please, 
i wish to add [SOLVED] to this thread a.s.a.p
it is not logic. for few days Transmission worked in speed of around 200-300 kb/s
but then, it went down to hardly 5-15 kb/s.

i disarmed firestarter firewall, 
the port is open in the router tcp/udp (i think that this what written there, but it is according to Transmission help page)
i have 2.5 Mb/s ADSL wired network.
why, why, why, how ? how ? how ?

how can it be that it won't work ?
i am sure that somebody out there has a Transmission that works great, other ways, it should have been off ubuntu ages ago, so how is it that there are so many guides for this issue and i (and with me a lot of users) can't have it work ?

please help, with detailed explanation.

thnx a lot,
doron387

---

### Post by credobyte on 2009-09-24
[http://www.speedtest.net](http://www.speedtest.net) - please show us what you have there .. numbers can be imagined :p

---

### Post by Mighty_Joe on 2009-09-24
[Transmission Wiki: Troubleshoot Slow Speeds]("http://trac.transmissionbt.com/wiki/SlowSpeeds")

---

### Post by doron387 on 2009-09-24
it seems quit crazy :
download speed : 0.97 Mb/s
upload  speed  : 0.03 Mb/s
ping : 576 ms

it is slow or is it logic  ?
is there something to do ?

---

### Post by lovinglinux on 2009-09-24
See the Troubleshooting section of [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). It asks a series of questions to narrow down the possible causes, until you can determine the culprit.

---

### Post by doron387 on 2009-09-24
lovinlinux, 
you did a very fine work there.
it is indeed very comprehensive and every word that you will write to me in this thread will be taken as god's words as you showed that you know what you r talking about and not just saying "did you check that your port is open ?"
ok, i read your essay. every thing is as you said.
it might be that i chose low seed or/and peers torrents (but it's because of the files that i wanted to download)
and it also might be related to my isp, which i will know if you read 2 post above the details that i got from speedtest.net and tell me whether it is normal number or it is vvvveeerrrryyy low speed.
there are so many units for this speed issue M m k K g G , etc... so please let me know what you r thinking about my computer's speed.
thanks, 
doron387

---

### Post by lovinglinux on 2009-09-24
> **doron387 said:**
> there are so many units for this speed issue M m k K g G , etc... so please let me know what you r thinking about my computer's speed.
thanks, 
doron387

Your download speed is normal, if you have 1 Mega plan, assuming you didn't change the default speedtest settings (megabits). Your maximum download speed will be about 120 KiB/s. This is the maximum value you should expect from your torrents. Nevertheless, your upload speed is unusual. Your maximum upload speed on the torrent client would be 3.66 KiB/s. 

Just for comparison, I have a 4 Mega plan and my upload speed is 74 KiB/s while my download speed is 488 KiB/s. So while my download/upload bandwidth ratio is 6:1, yours is almost 33:1. Which means your upload speed is very limited in comparison to your download speed. Keep in mind that a very low upload speed will also reduce your download speed when using BitTorrent clients.

I don't know what is the common bandwidth ratio in your country, but that seems odd to me. I would recommend asking your ISP if everything is normal and checking your contract for the promised speeds. 

Additionally, your ping latency is kind of high. This probably won't be a problem for torrents, but it is for multiplayer games. You should try another server on speedtest.net to see if this values reduces. For comparison, my ping is 56 ms when testing with a server in my own town.

---

### Post by doron387 on 2009-09-25
hey, lovinglinux, i wish to figure out something aboout port forwarding, 

attached a Word document, as i tried for 15 minutes to copy it into the forum thread but everything just messes all the time.

thnx

---

### Post by lovinglinux on 2009-09-25
> **doron387 said:**
> hey, lovinglinux, i wish to figure out something aboout port forwarding, 

attached a Word document, as i tried for 15 minutes to copy it into the forum thread but everything just messes all the time.

thnx

Have you checked the Configurations section of my tutorial?

---

### Post by doron387 on 2009-09-25
yep, but i don't understand which number to put where as i don't know what submask / subnet / gateway etc... means. 
in the attached document in my last post you can see all the options that i got, not to speak on my ubuntu machine, when i terminal>'ifconfig' i get much more ip's [i think that they are ip's] and names that i don't have a clue which number symbolizes what.
confused
doron387

---

### Post by lovinglinux on 2009-09-25
> **doron387 said:**
> yep, but i don't understand which number to put where as i don't know what submask / subnet / gateway etc... means. 
in the attached document in my last post you can see all the options that i got, not to speak on my ubuntu machine, when i terminal>'ifconfig' i get much more ip's [i think that they are ip's] and names that i don't have a clue which number symbolizes what.
confused
doron387

OK. I guess I was sleepy when I opened the doc file. Here it goes:

> Hi guys, i have not give up yet. I am going to understand how bittornet client should work fine.
Here are some details from my computer, i am starting with my xp machine, then i will move to my ubuntu machine. 
I have to let you know, i do not know what subnetmask means, what default gate means etc.... so i decided to show you all the tables that my machine and router offers me and let you give me the directions which number to put where.
After that, when it works i intend to write it all down in order to help others, so let's start.

In the xp machine, in the shell command line :
C:\Documents and settings\name>ipconfig
Windows IP Configuration
Ethernet adapter local area connection :

       Connection-specific DNS suffix .  : home
        IP address    .   .   .   .   .   .   .   .   .  : #.#.#.# 
        Subnet Mask  .   .   .   .   .    .   .   .   : #.#.#.#
        Default Gateway .   .  .   .   .   .   .   . : #.#.#.#

IP address is the internal IP of your machine, that can be assigned automatically via DHCP or configured manually via Network Manager. The value depends on your router, but it is usually 192.168.**1**.x. or 192.168.**2**.x. Check your router IP to see which one of these ranges it belongs. The router is usually 192.168.**1.1** or 192.168.**2.1**.

Subnetmask is explained [here](http://en.wikipedia.org/wiki/Subnet_mask). The value is usually 255.255.255.0

The [Default Gateway](http://en.wikipedia.org/wiki/Default_Gateway) is the IP of the machine used to connect directly to the ISP. So you should put the IP of the router in this value.

> Pre-defined / User defined : (I can choose, if I choose user defined I have to fill up the following : )

Choose "User Defined"

> From Internet Host IP Address:  (options : all/single/subnet &#8211; what to choose ?)

IP Addr: (what to type here ?)	

Netmask: (what to type here ? )



I'm not sure what you should put in these options, since I don't have a similar router. Have you checked [portforward.com](http://portforward.com/) instructions for your particular router?

> Forward to Internal Host IP Address: (what to type here ? )	

Is the internal IP of your machine, configured previously in the machine or assigned via DHCP.

> Protocol: TCP UDP TCP/UDP (I can choose one of these options)

TCP should always be used. You only need UDP if you are using DHT in your BitTorrent client. Nevertheless, it won't hurt to allow both.

> External packet: Port start Port end

I'm not sure. This is probably the port used by the sender trying to connect to you. My router doesn't have such option.

> Forward to internet host: Port start Port end

The port or port range used by your torrent client. If you are using for example 6881-6889 in the torrent client, then you should put 6881 as "Port Start" and 6889 as "Port End". If you are using a single port in your client, then put the same value for both.

---

