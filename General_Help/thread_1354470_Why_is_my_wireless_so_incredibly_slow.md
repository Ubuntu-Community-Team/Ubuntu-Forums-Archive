---
title: "Why is my wireless so incredibly slow?"
date: 2009-12-13
forum: General Help
---

### Post by trpnblies7 on 2009-12-13
I can't for the life of me figure out what's wrong with my wireless connection. Sometimes it works ok, but for the most part it's excruciatingly slow--often times I can't get any websites to load. I'm using:

-Ubuntu 9.10
-Asus WL-167G USB adapter (which has always worked well in the past)
-RT73USB driver
-Linksys WRT54GL router with DD-WRT v24-sp2

It's not a Firefox issue, because everything that uses the internet is slow (Thunderbird, Pidgin, Synaptic, etc.). I recently switched from Network Manager to WICD to see if that would make a difference, but it didn't help. I've also tried changing my wireless channel, but I get the same results regardless of which channel I use.

I can't figure out if it's a driver issue, the physical distance of my wireless adapter to my router (my connection is usually between 60-65%, but that never used to be a problem), or something else. I don't have the option of using a wired connection, so I need to figure out why this is happening.

I don't know where to begin. Any help at all would really be appreciated.

---

### Post by trpnblies7 on 2009-12-14
I've been trying OpenDNS since last night, and I think it's helping a little, but it's definitely not fixing the problem.

---

### Post by polki@mac.com on 2009-12-15
Try Googles dns: 8.8.8.8 and 8.8.4.4

I'm just guessing wildly, but it might work...

---

### Post by northern lights on 2009-12-15
Can you please post the output of ```
sudo lshw -C network && ifconfig && iwconfig
```Thank you.

---

### Post by trpnblies7 on 2009-12-15
> **northern lights said:**
> Can you please post the output of ```
sudo lshw -C network && ifconfig && iwconfig
```Thank you.


Here's my output:

```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:7d:0c:39:3b
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:c000(size=256) memory:fa000000-fa000fff memory:fb100000-fb11ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1e:8c:d6:37:95
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.134 multicast=yes wireless=IEEE 802.11bg
eth0      Link encap:Ethernet  HWaddr 00:1d:7d:0c:39:3b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:1e:8c:d6:37:95  
          inet addr:192.168.1.134  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fed6:3795/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2185 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1914 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1542445 (1.5 MB)  TX bytes:271132 (271.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1E-8C-D6-37-95-64-36-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"1908PineApt3"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:23:69:2E:B1:83   
          Bit Rate=54 Mb/s   Tx-Power=9 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by northern lights on 2009-12-15
Your output looks as it should. Unfortunately, that is, as that doesn't help determining the cause of your wireless being slow.

The only weird part I'm seeing is that the noise level should also be displayed in this line> **trpnblies7 said:**
> Link Quality=44/70  Signal level=-66 dBm
You could manually check```
cat /proc/net/wireless
```but that should yield no other result as *iwconfig* pulls this info directly form */proc/net/wireless*. Still, post the output of that also. SNR (Signal-to-noise-ratio) is more interesting than the signal strength itsself.

Unfortunately the cause of your problem appears quite hard to determine from afar.

Are you certain switching channels does not alter (for the better or the worse) the wireless' performance?

Also, have you checked your speed via a service such as [http://www.speedtest.net/]("http://www.speedtest.net/")? That'll give a more objective measurement than subjective PC usage. If that yields good results, it's an application problem. If not, it's your network.

---

### Post by trpnblies7 on 2009-12-15
The result is:

```

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   46.  -64.  -256        0      0      0      0      0        0

```

Switching channels sometimes helps for a little while, but then it'll go right back to not working well. I checked speedtest.net, and my result seemed ok right now. Currently, I'm not having an issue. Maybe OpenDNS is helping--I'm not sure.

---

### Post by trpnblies7 on 2009-12-19
Everything is very slow again, so apparently OpenDNS isn't helping. Any ideas?

---

### Post by Beeeerock on 2009-12-19
I'm also running 9.10.  Laptop is a Dell D800.  The wireless card is an internal Broadcom - a B/G card.  My output as above doesn't show anything out of the ordinary, but I can post if requested.  I also have an old Lucent PCMCIA wireless card that is capable of 11 Mb/sec.  The internal Broadcom comes up as WLAN0 and the Lucent as ETH1

I have two routers.  One is an older D-Link B/G (WEP) and the other is a new ASUS B/G/N (WPA2).  They are located in the same room.  I can connect to either with the Broadcom, but only the D-Link with the Lucent.  This is because the Lucent doesn't do WPA encryption.

I have done some testing with the speedtest page for my ISP.  It has proven to be quite reliable and consistent.  The Broadcom/ASUS combination doesn't want to move any data at all.  The Broadcom/D-Link combination moves a little under 1 Mbit/sec on the download, 450 kbit/sec up.  The old Lucent connected to the D-Link shows rates at around 2.8 Mbit/sec up, 450 kbit/sec down.  'iwlist rate' during the testing tells me the Broadcom is connected at 48 or 54.  The Lucent shows 11.  So, there seems to be a bottleneck in the system somewhere.  However, when I ran the iwconfig command a few times with no data moving, I saw the result show random 1 Mbit/sec results, mixed with 48 and 54.  This was for the Broadcom card... the Lucent was consistent at 11.

Incidentally, if I connect to the D-Link or ASUS with Ethernet cable, the speed test shows around 20 Mbit/sec down, 450 kbit/sec up.

If I try the test with my Dell Mini9 running Ubuntu 9.10 from a few rooms away, I get 6 Mbit/sec down, 400 kbit/sec up with the D-Link and 16 Mbit/sec 450 kbit/sec connected to the ASUS.

I can't help but think there is something messed up in the Broadcom driver somewhere... I want to use this laptop as a Myth frontend box.  Not sure whether 54 Mbit/sec will be enough, but I know 1 Mbit/sec won't be!  

Any ideas?

---

### Post by trpnblies7 on 2009-12-22
I'm desperate to figure out what the problem is. I've now switched to Google DNS, which is helping a little bit, but things are still slower than they should be. Could there be a problem with my DNS settings that's causing my network to bottleneck or something? I just don't understand why I can't get this to work correctly.

---

### Post by trpnblies7 on 2009-12-23
Things are still slow...

---

### Post by trpnblies7 on 2009-12-30
Anyone?

---

### Post by trpnblies7 on 2010-01-03
It is crawling. I'm desperate to figure out why this isn't working correctly.

---

### Post by SinxarKnights on 2010-01-03
Possible someone is stealing internet from you? Try plugging in to the router with ethernet and see if that helps. If not I would be checking to see if anyone else is connected to the router.

---

### Post by trpnblies7 on 2010-01-03
No one is stealing my internet. The only two computers on the router are mine and my roommate's. Unfortunately I don't have the option of using an ethernet cable because my computer is too far away, otherwise I would.

---

### Post by SinxarKnights on 2010-01-03
> **trpnblies7 said:**
> No one is stealing my internet. The only two computers on the router are mine and my roommate's. Unfortunately I don't have the option of using an ethernet cable because my computer is too far away, otherwise I would.

How about roommate downloading? Torrents will kill any thing else connected to the network if left unchecked. Youtube is also very bad for that.

You could also try unplugging the modem for 10 mins and rebooting the router, sometimes static buildup causes problems.

But before trying any of that, if possible, try out the roommates PC and see if its slow aswell.

---

### Post by trpnblies7 on 2010-01-03
No, it's not anything my roommate is doing. He doesn't download much, nor does he know how torrents work. His computer works fine with the router.

My computer used to work fine with older versions of Ubuntu, 8.04 and 8.10 especially. I don't know what's going on with the past two versions.

---

### Post by SinxarKnights on 2010-01-03
Oh well, i tried :( 

In 9.10 my wireless don't work at all. cant find any networks so im stuck with 9.04.

If you figure it out let us know what was wrong. Intresting problem you have.

---

### Post by jbslaw on 2010-01-03
Karmic changed dns lookups to be more compatible with the current standards.  Unfortunately, if you have a consumer-level wireless router that doesn't handle ipv6 dns lookups, it waits for the ipv6 lookup to time out before falling back to the ipv4 lookup.  

I did two things to fix it on my laptop.  First was to eliminate ipv6 altogether by changing /etc/default/grub.  Find this line:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;quiet splash&#8221;

Change it to:

GRUB_CMDLINE_LINUX_DEFAULT=&#8221;ipv6.disable=1 quiet splash&#8221;

then run "sudo update-grub".

I also changed /etc/nsswitch.conf to reorder the lookup preferences.  

Find the line that says:

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4 

Change it to:

hosts:          files, dns, mdns4_minimal [NOTFOUND=return] mdns4

Also, if you are trying to access windows shares on a windows network, install winbind and add "wins" before "mdns4_minimal

---

### Post by trpnblies7 on 2010-01-03
I made those changes. I can't tell if anything is different yet, but hopefully it'll help. Thank you.

---

### Post by trpnblies7 on 2010-01-05
I think these changes actually made things worse. It seems to be cutting out much more than before now. I'm going to put it back how it was. Thanks, though.

Any other ideas?

---

### Post by ljrmorgan on 2010-01-06
I have the same problem, my internet is frustratingly slow. Here are a few details:
- I'm on cable broadband, it's very fast when I boot into windows.
- I'm on an amd64 desktop, but on a different floor of the house from the router. The signal strength is good though, and as I've said, it works on Windows (on the rare occasion that I use it).
- I alpha tested Karmic (upgraded from Jaunty which was upgraded from Intrepid, etc.) but reformatted completely and did a clean install when the final release of Karmic came out.
- After having problems resolving domain names I switched to google's public DNS. The internet is still slow, though it now seems to be slow while waiting for a page to load as opposed to while "Resolving host...".
- I've also tried disabling IPv6, in network manager, firefox (though I mostly use chromium anyway) and via GRUB, this hasn't helped.
- My wireless has WPA2 on it, with a massively long randomly generated key, so no one else is using it.
- There is another computer in the house on the network, but it isn't used that often, so my problem isn't caused by someone else torrenting or anything like that.

Any thoughts? I haven't had this problem before with ubuntu (Jaunty etc.), and I chose my wireless card carefully to make sure it was supported by linux.

---

### Post by adam814 on 2010-01-06
What channel is your router on?  I check from time to time to make sure a neighbours network isn't on the same channel as mine.

---

### Post by trpnblies7 on 2010-01-06
There are always other networks on the channels, regardless of if I use 1, 6, or 11. Changing channels doesn't seem to help.

---

### Post by ljrmorgan on 2010-01-06
I'm not sure about the channel, there aren't that many other wireless networks near by though, and that wouldn't explain why it works in Windows and on the computer downstairs.

---

### Post by darco on 2010-01-06
I would try another wl card.....


darco

---

### Post by ljrmorgan on 2010-01-06
> **darco said:**
> I would try another wl card.....


darco

Well, I'm quite reluctant to do that. This card has always worked flawlessly with ubuntu until Karmic, and works on XP, so it must be a software problem. Given that it worked with Jaunty, it's hopefully a fairly small fix. I don't have any other cards lying about that I can try, and I don't want to buy a new one when that could just as easily not work properly in Lucid.

Also, here's the output for the command in post 4

```
  *-network:0             
       description: Wireless interface
       product: RT2561/RT61 802.11g PCI
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:05:06.0
       logical name: wmaster0
       version: 00
       serial: 00:0e:2e:4e:93:39
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt61pci ip=192.168.1.2 latency=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:16 memory:d5000000-d5007fff
  *-network:1
       description: Ethernet interface
       product: 88E8001 Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: c
       bus info: pci@0000:05:0c.0
       logical name: eth0
       version: 13
       serial: 00:13:d4:c2:2f:f0
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=skge driverversion=1.13 firmware=N/A latency=32 link=no maxlatency=31 mingnt=23 multicast=yes port=twisted pair
       resources: irq:17 memory:d500c000-d500ffff ioport:a800(size=256) memory:d6100000-d611ffff(prefetchable)
eth0      Link encap:Ethernet  HWaddr 00:13:d4:c2:2f:f0  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:13:d4:c2:24:38  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 B)  TX bytes:300 (300.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:0e:2e:4e:93:39  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93445 errors:0 dropped:0 overruns:0 frame:0
          TX packets:62442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:117770454 (117.7 MB)  TX bytes:9165251 (9.1 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-0E-2E-4E-93-39-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Netgear"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1E:2A:6B:C9:38   
          Bit Rate=2 Mb/s   Tx-Power=17 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

And here's the output for the command in #6:
```

Inter-| sta-|   Quality        |   Discarded packets               | Missed | WE
 face | tus | link level noise |  nwid  crypt   frag  retry   misc | beacon | 22
 wlan0: 0000   52.  -58.  -256        0      0      0      0      0        0

```

Does this shed any light on anything?? Thanks :-)

---

### Post by wkulecz on 2010-01-06
> I don't have the option of using an ethernet cable because my computer is too far away  Wireless has never solved that problem for me if data transfer speed is an issue!

If it sometimes works OK, look for interference, as some pre-standard cards ended up killing any other wireless networks in range.  When my wife runs the microwave oven the 2.4GHz wireless is pretty much toast while its on.

I've a 2.4GHz and 5GHz dual band 802.11n setup and a few feet location change can result in 60Mbps vs 1lMbps.  I never see anywhere near the advertised speeds and thats with linksys N router to linksys N card on Windows.

My wife won't let me run a wire to her computer, so she lives with the low wireless file transfer speeds, although the decrement for external internet access is pretty minimal.

---

### Post by darco on 2010-01-06
Well my response was actually for the OP...

Your bit rate "=2 Mb/s" is small.....you need to run:

```
sudo iwconfig wlan0 rate 54M
```

then restart network or reboot

darco

---

### Post by ljrmorgan on 2010-01-06
The problem for me is that it works on Windows, so that suggests that the problem is not due to the card itself, other peoples wireless, or any other interference with the network. I'm using 802.11g, so microwaves etc. shouldn't interfere anywawy. Also, the problem is basically constant and crippling - I often have to refresh pages endless times in an effort to get them to load, and that's just basic web pages. I rely on the internet, and it's basically rendered my computer unusable.

---

### Post by darco on 2010-01-06
> **trpnblies7 said:**
> There are always other networks on the channels, regardless of if I use 1, 6, or 11. Changing channels doesn't seem to help.

Also, any cordless phones nearby? That could also be your issue.

---

### Post by ljrmorgan on 2010-01-06
darco, I don't understand that: I just ran iwconfig again (without running your command first), and it was listed as 54Mb/s. And I ran it again, and it now says 36Mb/s. Not sure why it's fluctuating like that, I'm not moving about.

---

### Post by darco on 2010-01-06
> **ljrmorgan said:**
> darco, I don't understand that: I just ran iwconfig again (without running your command first), and it was listed as 54Mb/s. And I ran it again, and it now says 36Mb/s. Not sure why it's fluctuating like that, I'm not moving about.

ya thats strange....I was just looking at your post and it showed 2mbs....
Also it shouldnt change when you move, its just telling the card you have "g" capability.

---

### Post by wkulecz on 2010-01-06
If the 9.10 drivers for your card are bad, you can search for new drivers or get a new card.  You seem to have exhausted most other possibilities and options.

802.11g is 2.4GHz and being near a microwave most certainly affects it, my wife's computer is the other side of the wall in the kitchen where the microwave is.  Since she doesn't usually sit at her computer while she is nuking something, she's never noticed, but my marginal connection with my XP laptop in the dining room most certainly does.

When I went from G to N my wife's usb wireless G wouldn't work, although it still worked fine on my XP laptop and gave its full 54Mbps which my wife mostly got G router to 8.04, she is still running 8.04).  There is precious little "official" wireless support for Linux :(

You could google ndiswrapper and see if you can use the XP drivers with your current network card on 9.10.  I've always found it easier to buy a new card than to mess with this. YMMV.

I've only tried 9.10 on a wired network.  You could search to see what wireless cards are working well for people with 9.10.

--wally.

---

### Post by trpnblies7 on 2010-01-06
My wireless card has worked fine in previous versions of Ubuntu. As ljrmorgan said, it seems more to be a software problem, or maybe a driver problem in Karmic.

---

### Post by trpnblies7 on 2010-01-06
> **darco said:**
> Also, any cordless phones nearby? That could also be your issue.

I usually have my cell phone with me in my room, but that didn't used to cause any problems, nor do I keep it right next to my wireless adapter.

---

### Post by darco on 2010-01-06
> **trpnblies7 said:**
> My wireless card has worked fine in previous versions of Ubuntu. As ljrmorgan said, it seems more to be a software problem, or maybe a driver problem in Karmic.

Basic troubleshooting says to never overlook the obvious. I am not saying its broken but why not try another card. 
Boot into the livecd....does wl work there?

---

### Post by darco on 2010-01-06
> **trpnblies7 said:**
> I usually have my cell phone with me in my room, but that didn't used to cause any problems, nor do I keep it right next to my wireless adapter.

cell phones do not cause issues...I am talking about cordless house phones...do you live in an apt. building?

[http://en.wikipedia.org/wiki/Electromagnetic_interference_at_2.4_GHz](http://en.wikipedia.org/wiki/Electromagnetic_interference_at_2.4_GHz)

---

### Post by trpnblies7 on 2010-01-06
I'm not against trying another card; I would just prefer to not waste money on one only to find out that it was a software problem.

I'll try the live cd when I get home tonight.

---

### Post by darco on 2010-01-06
> **trpnblies7 said:**
> I'm not against trying another card; I would just prefer to not waste money on one only to find out that it was a software problem.

I'll try the live cd when I get home tonight.

You could always return it

---

### Post by trpnblies7 on 2010-01-06
> **darco said:**
> cell phones do not cause issues...I am talking about cordless house phones...do you live in an apt. building?

Yes, I live in a building with a few other apartments. I don't have a cordless phone, but I don't know if my upstairs or downstairs neighbors do.

---

### Post by adam814 on 2010-01-06
> **wkulecz said:**
> 

You could google ndiswrapper and see if you can use the XP drivers with your current network card on 9.10.  I've always found it easier to buy a new card than to mess with this. YMMV.


+1

Might help as a last resort.  I've used ndiswrapper before and while it's a brilliant concept it's a huge pain in practice.  I found that rather than "solving" my driver problems it gave me a second driver layer to debug.  Now I'll take the any native Linux driver I can get over ndiswrapper.

---

### Post by arrancaru on 2010-01-07
I too have this problem using a rt73usb wireless chip. Connection drops at every 5~10 seconds using the ubuntu native drivers on a wpa protected network (uncheck connect automatically on wicd). Surfing the web is ok but it's impossible to do downloads, watch youtube videos or even using apt-get to install packages. Using ndiswrapper the connection doesn't drops so frequently but the problem with the downloads continues. I suspect that is a router problem. Will do a firmware update since I suspect that this problem occurs in windows too.

Best of luck.

---

### Post by rumli on 2010-01-14
I had a similar problem.  It turned out to be related to a recent kernel update.  When I selected the older kernel (any kernel before 2.6.31-17-generic) in the GRUB menu, the wireless worked like a charm again.

Ubuntu 9.10
Asus WL-167G USB
Linksys router

---

### Post by yzfr6wr on 2010-01-17
Did this ever get resolved?  I have exactly same issue and researched this thread with MANY MANY people having this issue with no resolution.  If there is a problem with the kernel then the kernel needs to be FIXED in 9.1.  Anyone with answer?????

---

### Post by trpnblies7 on 2010-01-17
I don't think it's been solved yet. I've been having mixed results by setting up a spare router I have as a repeater bridge and using a wired connection. Sometimes it works, but after awhile it seems to go really slow again.

---

### Post by mehturt on 2010-01-18
my problem with Asus WL-167g was solved by:
iwconfig wlan0 power off

---

### Post by caffienated on 2010-01-18
My old Prism g adaptor (Vigor 540 iirc) is actually faster and more reliable under xubuntu 9.10 than it was under 8.04...

---

### Post by trpnblies7 on 2010-01-18
> **mehturt said:**
> my problem with Asus WL-167g was solved by:
iwconfig wlan0 power off

And what does that do? That looks like it would turn off my wireless adapter, no?

---

### Post by mehturt on 2010-01-18
turns off some kind of power saving

---

### Post by trpnblies7 on 2010-02-10
I've tried *everything* and nothing will solve this problem. My wireless is still so incredibly slow and there just doesn't seem to be a good reason why. 

This is so incredibly aggravating.

---

