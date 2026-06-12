---
title: "Wireless problems"
date: 2011-02-22
forum: General Help
---

### Post by tom1252 on 2011-02-22
Hi,

After all the trouble of downloading error riddled copy's of the latest ubuntu OS, i have yet again come up with more troubles. All though it has been a challenged I think it is cracking piece of software, and it's FREE. Anyway I have a WG111v2 Netgear dongle. I have followed the following guide 10 steps of how to set up WiFi (Netgear WG111) on Ubuntu - Ubuntu Forums, the best i can. It is for the older version and a few things have changed. (E.g. Buttons have different names.). Anyway it has picked up a neighbours wireless network but can't find mine. Its not on the avaliable list. So i tried to add it manually and that worked and says it is connected but no Internet connection. Any idea's why? 

Thanks

Tom

P.S The router is the same one as i am connected to wired.

---

### Post by alket on 2011-02-22
Just asking. Have you tried System > Administration > Additional Drivers ?

---

### Post by tom1252 on 2011-02-22
Yeah I have. Thanks for the reply anyway tho.

---

### Post by tom1252 on 2011-02-23
I have narrowed it down to being something with the router settings. I  have no idea what i am looking for with the settings but I can log in to  the router to edit them. So if someone with experience knows what to do  it would be great. Thanks Tom

---

### Post by runeh76 on 2011-02-23
Hi

I have usb dongle also.
Im pretty sure that problem is ur router somehow.
Can u plug ur dongle straight to USB without router?

---

### Post by tom1252 on 2011-02-23
> **runeh76 said:**
> Hi

I have usb dongle also.
Im pretty sure that problem is ur router somehow.
Can u plug ur dongle straight to USB without router?

Hi, Thanks for the reply but I am not sure what your asking? 

I had to download drivers to setup the dongle so it picked up other routers. It finds my neighbors but not mine.

---

### Post by runeh76 on 2011-02-23
Sry i dont understand so well, but do u have 3G connection USB-stick?

---

### Post by tom1252 on 2011-02-23
Thanks.

The USB Dongle, isn't 3G. It enables me to connect to my router via wireless.

Here is the particular model:

[http://kb.netgear.com/app/products/model/a_id/2557](http://kb.netgear.com/app/products/model/a_id/2557)

---

### Post by runeh76 on 2011-02-23
Ooh i see  :) 
Then its up to ur router settings. U can access ur router from address-bar something like 192.168.0.1
Have u tryed to config ur router? Reset it first if it have reset- button and try default settings.
Im not a router expert, but isnt there should be ur ISP ip-address, user name/password and config dhcp and DNS (u can use these 208.67.222.222, 208.67.220.220) ..not sure sry.

edit: Oh and if u use mobloguer or firewall...apply ur connection to router 192.168.0.1 or something  :)

---

### Post by tom1252 on 2011-02-23
Thanks, hadn't thought of resetting the router. I will have a look now and let you know the outcome.

Thanks again.

---

### Post by tom1252 on 2011-02-23
This is the router i have:

[http://www.ebuyer.com/product/78906](http://www.ebuyer.com/product/78906)

---

### Post by runeh76 on 2011-02-23
[https://help.ubuntu.com/community/Router]("https://help.ubuntu.com/community/Router")

Check that, i need to sleep  :)

---

### Post by tom1252 on 2011-02-23
Cheers, you have been a great help tonight. Enjoy your sleep!:)

---

### Post by tom1252 on 2011-02-23
:d

---

### Post by tom1252 on 2011-02-23
I have gone through some of the router settings. I have changed the security type from WEP, WPA and none at all. No luck. I have no idea what to do. Windows is so much easier to setup wireless network but Ubuntu is a lot better at other stuff, otherwise i would have gone back.

---

### Post by runeh76 on 2011-02-24
Hi

I check ur router back-side, and just a thought... u could plug cable (rj45) between ur router<-->PC
U dont need that dongle then...

---

### Post by tom1252 on 2011-02-24
I reset the router but have had no luck. The router is downstairs and my computer is upstairs so a slight problem there. :(

Thanks anyway

---

### Post by tom1252 on 2011-02-24
Also when I try and manually connect to my router, it asks for the key and I type it in. A message pops up says wireless disconnected and then asks for the key again. Forgot to mention that.

---

### Post by runeh76 on 2011-02-24
Ahaa okey

Have u tryed Network-manager from upper right corner.
If u have created connection there (i think u need to create Wireless-connection)check ur IPV4settings. U could try when u get that "key thing" just ignore it and click mouse-left from Network-manager to connect ur connection.

I have same thing, when i take my 3G dongle off from USB and put it back. I get pin-code screen (under that is smaller "real" pin-code screen), i ignore it and click from network-manager and it takes around 10seconds to connect.

---

### Post by tom1252 on 2011-02-24
Ok thanks.

I will have a look later. At uni at the moment.

---

### Post by runeh76 on 2011-02-24
I didnt remember to ask..do u know if ur router is in NAT-mode? If so, it doesnt show up outside. It needs to be in (Full Routing (Non-NAT)) 
By the way, how did u configure ur router (with other PC or straight to Ubuntu PC with cable?)


Here is also good thread, same problem and dongle what u have:
[http://ubuntuforums.org/showthread.php?t=1390994]("http://ubuntuforums.org/showthread.php?t=1390994")

Here is information of NAT&wireless router

"The short answer is to make sure the wireless access point is not also attempting to provide NAT. How you do that will vary based on the access point, so check your documentation for NAT or for providing DHCP services to wireless clients and turn that off.

NAT is a technique that lets multiple machines on one side of your router share a single internet connection, and most importantly a single internet IP address as well. The router does this by handing out local IP addresses to each machine on your local network and translating between those addresses and the "real" internet IP address when the local computers access the internet.

Many wireless access points can be also configured to act very much like a broadband router. In fact there are several combo devices that are both a broadband router and wireless access point in one package. In either case, they may also be able to provide NAT functionality between the wireless and wired networks.

If NAT is turned on at both the broadband router and the wireless access point, all wireless devices are going through two levels of NAT to access the internet. Not only is that adding unnecessary overhead, but it also introduces some real problems. NAT "protects" the "local" devices from the remote devices ... in this case, the wireless access point will "protect" the wireless machines from the rest of your local network. In effect, it'll make them inaccessible.

So as I said earlier, the solution is fairly simple. You only need one level of NAT between the internet and the rest of your LAN. Anything on your local network is safe and does not need additional NAT. Make sure that NAT or DHCP is turned OFF on the wireless access point. (To be clear, the wireless access point may still use DHCP to get an address for itself, but it should not provide DHCP functionality to wireless devices.)"

---

### Post by tom1252 on 2011-02-24
Not sure how to tell whether it is in NAT mode but could not find anything on the router settings.

I did find that DHCP was on so i have un-ticked that. I will let you know if it works.

---

### Post by runeh76 on 2011-02-25
umm..what u mean, u couldnt find router settings?


Two ways to configure ur router: (with other PC or straight to Ubuntu PC with cable)

So how did u try it?

---

### Post by tom1252 on 2011-02-25
I used other PC. I have to put DHCP back on as it mucked up the internet for my iPad.

On the router settings I couldn't see anything about NAT mode.

Cheers

---

### Post by highspider on 2011-02-25
first check in ubuntu the IPv6 is set to ignor
  network manger > wireless > whatevername it has (guessing auto) > edit  

----------------------------------------------------------------

assuming you have windows also on a pc.

from windows command prompt
>  ipconfig /all

or from the right click the networking icon and click "connection status"
>

right down the ip info,

IP address, subnet amsk default rounte and primary dns.


load up ubuntu 

right click the network manger 
   click the wireless tab
     click Add.
  (you can copy all the info from auto)
     then under ipv4 settings change automatic to Manuel 
(rember to press enter key after entering the numbers yes its annoying)  
address should be like  192.168.0.10 
netmask should be like 255.255.255.0
gateway should be like 192.168.0.1    (route address)

DNS severs should be like 192.168.0.1 (route address) (same as gateway)


you could use your isp dns but the router will do it for you for non-static dns if you use the router address for dns severs  

click apply.

---

### Post by runeh76 on 2011-02-25
Yes ur router have NAT-support, i copyed next from ur router overview:

NAT (Network Address Translation) Features
Many-to-One (NAT)
Full Routing (Non-NAT)

Do also what highspider posted.
Hope u get it  ;)

---

### Post by tom1252 on 2011-02-25
Ok thanks. What did the NAT mean by the way?

Also having a bit of trouble finding everything. Can i use a different computer to find the information. 

Here is what came up:

[IMG]http://img571.imageshack.us/i/94260791.png/[/IMG][http://img143.imageshack.us/i/10805739.png/](http://img143.imageshack.us/i/10805739.png/)
[IMG]http://img571.imageshack.us/i/94260791.png/[/IMG]

---

### Post by runeh76 on 2011-02-25
Google NAT

U need to plug ur router to PC with cable (rj45), and type to address-bar ur router ip-address. Its usually 192.168.0.1 (gateway)

---

### Post by tom1252 on 2011-02-25
I have done that yesterday. Do i then look for the information provided earlier.

Thanks

---

### Post by runeh76 on 2011-02-25
Okey then u have to find these:

Many-to-One (NAT)
Full Routing (Non-NAT)


And choose **Full Routing (Non-NAT)**

---

### Post by tom1252 on 2011-02-25
Couldn't find either of them. :confused:

---

### Post by runeh76 on 2011-02-25
This is ur router overview, link what u posted:
I dunno if ur router has same things..but if u didnt find anything about NAT, then u dont have that support and it should be easier to connect...
Did u check router Firewall settings also?

Product Highlights
Combines modem, router, switch, 802.11g access point, and SPI True Firewall
Super Fast! – 108 Mbps with Super G Technology (when used with NETGEAR 108Mbps Super G Products)
Super Easy! – Smart Wizard gets you up and running in fewer than 5 clicks
True Firewall with Stateful Packet Inspection (SPI) & Intrusion Control, Denial of Service (DoS), Virtual Private Network (VPN) pass-through
Super Reliable! – 802.11g standard compliance; interoperable with existing 802.11b and 802.11g networks
Smart Wizard Install Assistant detects/connects to your ISP
Future proof with support for ADSL2+
Routing Features
Internet Protocols : PPPoA, PPPoE
Static routing and Dynamic Routing with RIP v1 and v2
DHCP Server, DHCP Client
Configurable MTU Size
Dynamic DNS
- DynDSN.org
Wireless Features
Confirms to IEEE 11Mb/s 802.11b specification
- Frequency band : 2.4GHz
- Modulation : Direct Sequence Spread Spectrum (DSSS)
- Non Overlapping Channels : 3
Confirms to IEEE 54Mb/s 802.11g specification
- Frequency band : 2.4GHz
- Modulation : Orthogonal Frequency Division Multiplexing (OFDM)
- Non Overlapping Channels : 3
Data rates of wireless : 108Mbps (Fallback to 108, 54, 48, 36, 24, 18, 12, 11, 9, 6, 5.5, 2 and 1Mbps, Automatic Rate Selection)
Operating Modes : Infrastructure
Disable Wireless
Operating Channel 1 - 13
Wireless Mode : g and b, g only, b onl, 108 only or Auto 108
Wireless Access Point Security
Encryption
- 128-bit WPA-PSK TKIP
- 128-bit WEP
Authentication
- Open System and Shared Key
Access Control
- MAC Address Control
Firewall and Security Features
Stateful Packet Inspection Firewall
- Filter on destination port values
- Defends router against Denial-of-Service (DoS) attacks
- Intrusion detection
Content Filtering
- Keyword and URL blocking
- Trusted IP access
- Time scheduling
- Email and logging notification
VPN (Virtual Private Network) Features
Single-session Virtual Private Network (VPN) Pass-through (IPSec, L2TP), PPTP
[B][U]NAT (Network Address Translation) Features
Many-to-One (NAT)
Full Routing (Non-NAT)[/U][/B]
Applications & Gaming Features
Port Forwarding
UPnP Support
Single DMZ Support
Management Features
Web Based Interface
- Multi-lingual Web User Interface, (English, French, German and Italian)
- 5-click Installation Wizard
System performance and status monitoring
Remote Management via Web services
- Restrict IP Address(es)
- Change Port number
LAN Ports
4 Port 10/100 Ethernet switch
- Auto Sensing
- Auto Uplink
- Half/Full Duplex Support
WAN Ports
RJ-11 ADSL Port
- Built-in ADSL Modem
- ADSL2 / 2+ upgradable via firmware updates
Manufactures Warranty
2 years
System Requirements
BT ADSL Broadband Service - All UK and Channel Islands ISP's are compatible (including AOL).
2.4 GHz wireless adapter or Ethernet adapter and RJ45 cable for each computer
Windows® 98, Me, NT, 2000, XP, Mac® OS, NetWare®, UNIX®, or Linux®
Internet Explorer 5.0 or Netscape® 4.7 or higher
Package Contents
NETGEAR DG834GT 108Mbps Super G ADSL Wireless Router
Free Microfilter
UK Power adapter
RJ11 Telephone Cable
RJ45 Ethernet cable
Resource CD
Installation guide
Warranty card
Support information card

---

### Post by tom1252 on 2011-02-25
Their is nothing on the firewall section and i have put in a hyperlink to what the router settings page looks like:

[http://www.kitz.co.uk/routers/images/DG834GT_Be_setup3.png](http://www.kitz.co.uk/routers/images/DG834GT_Be_setup3.png)

---

### Post by Hakunka-Matata on 2011-02-25
> Thanks

Tom

P.S The router is the same one as i am connected to wired.

That's from your first post.  Maybe a dumb question, but...  are you attempting to have both a wired connection and your wifi connection working on the same computer at the same time?  If so, your wired connection may well be disabling the wifi connection, try one or the other.

---

### Post by tom1252 on 2011-02-25
Hi, yes i was original but since then i have unconnected the wire and tried accessing by wireless. But no luck.

---

### Post by runeh76 on 2011-02-25
> **tom1252 said:**
> their is nothing on the firewall section and i have put in a hyperlink to what the router settings page looks like:

[http://www.kitz.co.uk/routers/images/dg834gt_be_setup3.png](http://www.kitz.co.uk/routers/images/dg834gt_be_setup3.png)

yes there read cat-sized letters:  Nat(network address translation  enable  disable) !!!

---

### Post by tom1252 on 2011-02-25
When i linked that page i thought it was the same as mine but it is not. At the top under setup: ADSL Settings is missing and so is basic settings. That is where NAT is listed

---

### Post by runeh76 on 2011-02-25
:confused:

Well then its up to ur router config.

---

### Post by tom1252 on 2011-02-25
Just looked up something. Because the router is a sky router it can't access the basic menu. Looks like i am out of luck. :(

---

### Post by runeh76 on 2011-02-26
sry Tom i cant help anymore..no more ideas if earlier stuff wont help.

---

