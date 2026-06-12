---
title: "Wireless Network w/ Linksys WPC54g"
date: 2006-06-02
forum: General Help
---

### Post by skb on 2006-06-02
First of all, thank you very much to the entire Ubuntu team. I consider myself a BSD guy, and after having a ton of trouble with my laptop, I finally came to try Ubuntu at the recommendation of a friend. After a seamless install I went about setting up my system, and had trouble with my wireless card. For the record, my system is an IBM Thinkpad T23, and my wireless card is a Linksys WPC54g v1.2.

After a ton of feverish googling here's how I got it to work. I'm posting this in the hopes that having all the info in one place will help anyone in the future who has the same problem.

1 ) Open Synaptic, and in SETTINGS->REPOSITORIES enable Universe repositories.

2 ) Search for NDIS. In the results mark "ndisgtk" and "ndiswrapper-utils" for installation, then install them.

3 ) Search for fwcutter. Mark bcm43xx-fwcutter for installation, and install it.

4 ) Download the latest drivers for the Linksys WPC54g. Note that if your card says it is version 1.2, YOU ACTUALLY NEED THE V2 DRIVERS. Whacky, I know. Blame Linksys.

5 ) Extract the files. I chose to extract them to ~/linksys/

6) Open System->Administration->Windows Wireless Drivers (this item is added by ndisgtk). Click to Install New Driver, and navigate to your linksys directory. Choose the appropriate INF file. Mine was "lsbcmds.inf"

7 ) Open a terminal. If you followed my installation path issue:
```
cd ~/linksys
bcm43xx-fwcutter bcmwl5.sys
```Note that "bcmwl5.sys" should be replaced with the appropriate sys file for your drivers. You'll see a screen or three of text, and maybe even one or two errors. Don't sweat them.

8 )Finally:
```
cp *.fw /lib/firmware
(or if that fails, like it did for me)
sudo cp *.fw /lib/firmware
(and then)
exit
```
9 ) Go to the network settings item in the Administrator tools and enter all the data for your wireless card. If you're using DHCP you shouldn't need to do anything. I'm not, so I did. Make sure you first deactivate your laptop's integrated ethernet device (if it has one) and then activate the wireless connection. If all is well it should fire right up.

Hopefully this well help someone else who's in the same situation I found myself in. I'm now looking forward to exploring everything Ubuntu has to offer, only with less wires!

--skb

---

### Post by ketsugi on 2006-06-02
Any luck getting Network Manager to configure this instead? How about WPA?

Edit: Oh never mind, my WPC54G is a v2, and the stupid TI ACX111 chip still isn't supported very well.

---

### Post by skb on 2006-06-02
[QUOTE=ketsugi]Any luck getting Network Manager to configure this instead? How about WPA?

Edit: Oh never mind, my WPC54G is a v2, and the stupid TI ACX111 chip still isn't supported very well.[/QUOTE]

Actually if you read on down in my post one of the things I've puzzled out is that the v1.2 -IS- the v2, which was at least part of the problem. I think most people seeing 1.2 will just use the v1.0 branch drivers and end up getting nowhere.

I had no luck with the Network Manager, and it's precisely because of the ACX111 chipset. You pretty much have to use NDIS to set it up, and apparently NDIS has some oddities extracting the firmware from the Windows driver, which takes us the long way around the barn to the process I had to go through to make it work.

If you ever catch any word of updated driver support for the WPC54Gv2, I'd love to hear about it!

--skb

---

### Post by ketsugi on 2006-06-02
So what about WPA? Managed to get that working right?

Anyway, I tried your advice. The first issue (which I encountered with other guides previously) is that the v2 card uses the lstinds.inf instead of the lsbcmds.inf file. I'm not sure if this is a problem.

There were 2 or 3 errors in the fwcutter as expected.

However I'm unable to detect any networks, and WPA doesn't seem to be enabled at all (also as expected, as I've read previously that the ACX111 linux drivers via ndiswrapper do not support WPA) so this is pretty much useless to me. I expect I'll be picking up a D-Link card sometime.

---

### Post by Fass on 2006-06-02
The ndiswrapper-utils and ndisgtk parts of this guide are unnecessary, seeing as the OP isn't actually using ndiswrapper for anything. It's the latter part with fwcutter and the use of the kernel's own bcm43xx module that made the card work.

---

### Post by skb on 2006-06-03
[QUOTE=Fass]The ndiswrapper-utils and ndisgtk parts of this guide are unnecessary, seeing as the OP isn't actually using ndiswrapper for anything. It's the latter part with fwcutter and the use of the kernel's own bcm43xx module that made the card work.[/QUOTE]

Oops, you're right about that. The fwcutter steps alone seem to solve the problem. Thanks for that. :)

--skb

---

### Post by dipswitch on 2006-06-04
First off I want to thank everyone in this community for all your help and information and generosity. I didn't want to start a new thread on this so I'll bump this one.

I installed Ubuntu last night on this laptop and I have a Linksys WPC54g. I was able to get it working using the steps above and using the lsbcmds.inf diver. My problem is that I can see the signal and everything but when I have wlan0 selected as my default it shows that its disconnected. Why? I've setup my ESSID and everthing and the Network Settings show that its active. Should I be using plain ASCII or hexadecimal for my key settings?

[IMG]http://img421.imageshack.us/img421/1903/screenshotconnectionproperties.jpg[/IMG]

---

### Post by skb on 2006-06-05
ASCII or Hex depends on how your WEP key is set up. If you haven't enabled WEP on your wireless router (it'd be under either the security or privacy settings) then it doesn't matter as long as the key field is left blank. As far as network security goes, I recommend WPA over WEP, but getting it to work in Ubuntu would currently require you to download and set up something like wpasupplicant, which is a little outside the scope of this thread.

Short version:  ASCII or Hex... Doesn't matter which if you don't have WEP enabled. If you did, you'd know which you'd set up. If someone else administers your wireless network, ask them about it, but otherwise just leave the key field blank.

As for network manager showing your wlan0 as being disconnected, I have the same problem (although for me it's eth1). I was able to work around this by downloading Wifi Radar (some people recommend GTKwifi, but I didn't have any luck with it. Assume user error!). Then I edited my /etc/network/interfaces file (remember to use sudo) and changed it so that the only reference to my wireless card was:

> 
auto eth1
iface eth1 inet manual


Then, back in the shell:

> 
sudo /etc/init.d/networking restart


After that I opened Wifi Radar (it installs to Applicaitons->Internet by default) and set up my connection. It scanned out the AP for me, so it was a snap. If in doubt on a setting, leave it blank. :)

I've added a Wifi Radar launcher to my toolbar, so when I boot gnome I click to launch, click my AP, click connect, and off I go. It's not quite automatic at boot, but I'm still working on that.

Hope this helps.

--skb

---

### Post by skb on 2006-06-05
[QUOTE=skb]As for network manager showing your wlan0 as being disconnected, I have the same problem (although for me it's eth1). I was able to work around this by downloading Wifi Radar[/QUOTE]

More detail on this for the general edification of the thread. This turned out to only be the case if I wasn't using DHCP on my ap/router (so I could use NAT pinholes, e.g.). The network-manager + network-manager-gnome packages from Synaptic seem to work pretty well if you're only really worried about DHCP networks, which will be the case for casual university, work, home, or coffeeshop users.

In this configuration my /etc/network/interfaces file is:
> 
###loopback
auto lo
iface lo inet loopback

###wired interface
#iface eth0 inet manual

###wireless interface
auto eth1
iface eth1 inet dhcp


Note that changing this requires a "sudo /etc/init.d/networking restart &" or a reboot to take effect. I commented out my wired interface since I never use it, and because having both interfaces go up at once has caused me some really amusing, hair-ripping problems, like the wireless connection being unable to accept a DHCP lease.

So:  If you're using wireless in an environment where you need to have a static IP I recommend the WiFi Radar approach from the previous post, as I was unable to get Network Manager (not to be confused with Network Monitor) to play nice with static settings. It'd claim it's connected when it's really not.

If you're using wireless in a DHCP environment, go with the above detailed Network Manager approach.

Again, hope this helps someone out there.

And just in case it comes up, yeah I tried gtkwifi with my DHCP approach, and it still didn't work. ;) I think it just hates Dapper.

--skb

---

### Post by nzruss on 2006-06-06
I used this, seems I got away with the old way... might not work for everyone though.

[http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101](http://www.ubuntuforums.org/showthread.php?p=1105101#post1105101)

---

### Post by Bdanger on 2006-06-10
Does anyone have some info on how to get this to work with Version 4??  The instructions on this page seemed to work well for me until I loaded "lsbcmds.inf" and it said "Hardware Present: No"  I then found that it was the "wlipnds.inf" that i needed to install, which then detected my card...BUT the wlipnds.inf uses I2220.SYS instead of BCMWL5.SYS.  

When doing the "bcm43xx-fwcutter I2220.SYS" command it says:

"Sorry, the input file is either wrong or not supported by fwcutter. 
I can't find the MD5sum 9bdda2f25392blcfcl62e747d9302d09 :("

Does anyone know how to get around this?  I'm a newbie and I have gotten this card to work with other distros before.

---

### Post by jimmymac on 2006-07-27
Legend, I've spent hours trying to fix this problem after I nuked my system from 5.1 to 6.06.  Then I come across this post and hey presto!!

Int milk brilliant!

---

### Post by tobaccoman on 2006-09-17
Thank you very much!

After struggling during 3 days I finally managed to get WLAN working on my PAVILION zd800 following your description ([http://www.ubuntuforums.org/showpost.php?p=1080128&postcount=1](http://www.ubuntuforums.org/showpost.php?p=1080128&postcount=1))

Thank you again!

Daniel::

---

### Post by jdcaron on 2006-11-15
Thank you very much for thoses instructions. They are by far the best I found and they finally resolved my problem!

---

### Post by boob11 on 2008-02-15
Thanks

======================

---

