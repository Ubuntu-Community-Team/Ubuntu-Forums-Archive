---
title: "Slow Wireless Download Speed"
date: 2010-06-05
forum: General Help
---

### Post by MarcW10 on 2010-06-05
Hi There

Sorry my first post is a problem but this one is bugging me something rotten. Basically the problem is a slow download speed over my wireless connection that does not occur in Windows Vista. The reason I'm so annoyed is that the speed is not constantly slow. It bursts at around 600kb/s (good for my internet connection). The problem is that while trying to download a file it bursts for about a second,then total throughput decreases to +/- 1kb/s for a few seconds, then another burst and so on. Note the file I'm downloading is a http:// download, not p2p or anything. I've attached a screenshot of the System Monitor because I'm no good at explaining things and figure the visual will help. 

[ATTACH]159475[/ATTACH]

Some additional info. I'm using Ubuntu 10.04 with all available updates installed. The browser in use is Google Chrome. 

Any questions please ask away, if anyone can help me figure this one out I'll love them forever or something!

Marc

---

### Post by MarcW10 on 2010-06-05
I'ma bump this one because it disappeared off the 1st page without a reply.

---

### Post by MarcW10 on 2010-06-06
Any ideas?

---

### Post by MarcW10 on 2010-06-06
Ok, one last bump before I bugger off back to Vista

---

### Post by an0dos on 2010-06-06
> **MarcW10 said:**
> Ok, one last bump before I bugger off back to Vista

What type of wireless card do you have in your computer? If you don't know off the top of your head, you can run the following command in the terminal:

```
sudo lshw -C network
```

and post the output here.

Is this a laptop? If so, have you tried connecting to different wireless networks with it?

---

### Post by MarcW10 on 2010-06-06
Output below. Can't pick up any other networks to try atm.

```


*-network               
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 00
       serial: 00:15:af:bd:10:20
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 ip=192.168.1.4 latency=0 multicast=yes wireless=RT2860 Wireless
       resources: irq:18 memory:f0200000-f020ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0e:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:49:92:01
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:a000(size=256) memory:f0300000-f0300fff memory:80400000-8041ffff(prefetchable)

```

Thanks for the reply!

---

### Post by dearingj on 2010-06-06
> **MarcW10 said:**
> Ok, one last bump before I bugger off back to Vista

1) Please don't bump so often; people do look at more than just the first page :).

2) Do you have another type of connection you could try, perhaps one that's not wireless? If so, do you get the same kind of speed problem?

---

### Post by an0dos on 2010-06-06
Okay, I googled the particular wireless chipset you have and Ubuntu 10.04. There was a post on the following blog about this problems with this card and Ubuntu 10.04. I cannot vouch for the accuracy of the information on this site and I personally probably won't be able to answer questions if you get stuck. You may get better results directly asking questions on the blog as opposed to these forums if you decided to follow the post and get stuck. The post is from May 1, 2010 and so it should still work.

[http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html](http://www.ctbarker.info/2010/05/ubuntu-1004-wireless-chipsets-and-wpa.html)

Or you can wait till someone responds to your post who knows more about troubleshooting problems with wireless cards. :)

---

### Post by MarcW10 on 2010-06-06
Thanks for the link. I'm a total Linux noob so I'm going to try and work through all that, might take me a lil while.

Thanks again, I owe ya.

---

### Post by an0dos on 2010-06-06
You can also check out this thread on the forum:

[http://ubuntuforums.org/showthread.php?t=1467789&page=2](http://ubuntuforums.org/showthread.php?t=1467789&page=2)

If you get really stuck, I think this was a regression in 10.04. Your wifi may work in Ubuntu 9.10. It may be worth checking out Linux Mint; however, it may not work there either because it is based on Ubuntu.

---

### Post by MarcW10 on 2010-06-06
One problem I seem to be coming across while trying to carry out these instructions is that when I try to edit the following files they both don't exist on my system.

./common/cmm_wpa.c.

./os/linux/config.mk.

Any ideas?

---

### Post by davidmohammed on 2010-06-06
the instructions depend on you having extracted the files into your home directory.

where did you extract your files?  For example, could be ~/Downloads

in that case, 

cd Downloads
your extracted files will then exist there.

---

### Post by nuffink666 on 2010-06-06
Hi,
 
Not sure from your output of the network whether or not that driver your using is one that 10.4 has assigned you or the one that is provided by the realtek site url below
 
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)<br>RTL8102E(L)/RTL8101E/RTL8103T<br>RTL8401/RTL8401P](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)<br>RTL8102E(L)/RTL8101E/RTL8103T<br>RTL8401/RTL8401P) 
 
but i used this driver and installed as per the instructions as i was having the same issues originally but thsi driver corrected it for me and now ahve no problems with conssitency.
as also suggested would also try connecting via cable and see if the fluctruations still exist to eliminate that its a network provider inconsistency.

---

### Post by MarcW10 on 2010-06-06
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)<br>RTL8102E(L)/RTL8101E/RTL8103T<br>RTL8401/RTL8401P](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=7&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8100E/RTL8101E/RTL8102E-GR/RTL8103E(L)<br>RTL8102E(L)/RTL8101E/RTL8103T<br>RTL8401/RTL8401P) 

Hi there. Thanks a bunch for the reply. Tried downloading from the above link and all three mirrors are asking for a user and password that I don't have. And I'm for some reason unable to get my head around installing from tar.bz2 files, but that's another story for another time.

Marc

---

### Post by nuffink666 on 2010-06-06
MarcW10
 
there you go one downlaoded tar file.
 
save to home directory
 
open a terminal from applications menu
 
sudo su (changes you to root)
 
tar -xvf [the tar tar file name attached]
 
now should have directory without the tar.bz bit 
 
follow the instructions formt here. 
 
post back if you have any other problems.

---

### Post by MarcW10 on 2010-06-06
nuffink666, you are now officially my hero!

Download speeds now constant between 900kb/s and 1.2mb/s after installing the driver file you gave me. 

Thanks all for helping out a new guy in his hour of need.

Marc

---

