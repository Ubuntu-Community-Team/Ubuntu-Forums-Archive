---
title: "connecting to the internet using a modem , Increasing partition size"
date: 2009-09-28
forum: General Help
---

### Post by McWeirdo on 2009-09-28
Hello,
I am using Ubuntu 9.04, and I have 2 questions:
 
1)I am using a cable modem to connect to the internet using my stationary computer which has another OS, It's connected to the PC via sort of a LAN cable, and not via USB.
So I connected the modem to my laptop which has UBUNTU on it and it did recognize that I connected a modem but I couldn't surf the internet, means that I'm not really connected, a good expression for it could be " Local connection", and it's not a dial-up modem but I still think I need to write my Username and Password once ,some where but I don't know, I just speculate, so if some one can help me here I will appreciate it.
 
 
2)When I first installed Ubuntu I didn't give it that much of a "work room" , and now when I look how much space is left in the "System files" or whatever it is, it says 1.2gb, and I want to increase it, so I went to my other OS on the laptop trying to increase a partition size, apparently there is no another partition :| but when I installed it I\m almost sure I made another partition for it(when I installed it there was a bar of blue orange green thing, while orange is for Ubuntu), did I do something wrong, or am doing something wrong? and how can I fix it?
 
Thank You very much,
and excuse me for being a New-B :DDD
MCW

---

### Post by Giblet5 on 2009-09-28
You probably need to talk to whomever sold you the cable modem.



As for the partitioning issue, it's difficult to correct a partitioning problem after install and, even if someone explains how to do it, the odds that something else will get messed-up is high.

I would back up my HOME directory (/home/yourname) to a thumbdrive, CDRW, or something similar, and reinstall, paying closer attention during the partitioning phase.

When I install, I usually dedicate 32GB to a / partition and 100GB+ to a /home partition. You'll be limited by other OSes though and your mileage will vary.

Good news: disk drives are really cheap.

---

### Post by McWeirdo on 2009-09-28
It's a modem from my ISP,it works on other OS...
damn, so i will back up my home directory and reinstall ubuntu... or I'll just ubstall it on my stationary PC.
 
I have 800GB free on 1 HDD, can I make a partition there and then install ubuntu on this partition???hope I won't screw things up, and I really think I shouldn't do it, cause I have ATI 4870X2 on that pc , and it gets very hot if I don't increase the fan speed , therefore I need drivers for linux, I hope there are any :S

---

### Post by P4man on 2009-09-28
> **McWeirdo said:**
> Hello,
I am using Ubuntu 9.04, and I have 2 questions:
 
1)I am using a cable modem to connect to the internet using my stationary computer which has another OS, It's connected to the PC via sort of a LAN cable, and not via USB.
So I connected the modem to my laptop which has UBUNTU on it and it did recognize that I connected a modem but I couldn't surf the internet, means that I'm not really connected, a good expression for it could be " Local connection", and it's not a dial-up modem but I still think I need to write my Username and Password once ,some where but I don't know, I just speculate, so if some one can help me here I will appreciate it.

Is that modem also a router? (does it have more than 1 ethernet port?). Perhaps you can find a product type and post it here?  Im not very familiar with cable modems that are not routers, if its a router it should be easy to solve. If not, then im not so sure. 

Either way, open a terminal, and type 

```
ifconfig
```

And copy/paste the result here. 

 
> 2)When I first installed Ubuntu I didn't give it that much of a "work room" , and now when I look how much space is left in the "System files" or whatever it is, it says 1.2gb, and I want to increase it, so I went to my other OS on the laptop trying to increase a partition size, apparently there is no another partition :| but when I installed it I\m almost sure I made another partition for it(when I installed it there was a bar of blue orange green thing, while orange is for Ubuntu), did I do something wrong, or am doing something wrong? and how can I fix it?


It depends. if you did a "wubi" install, then it will be difficult (or at least, I do not know of a way to resize wubi installs). If you did a regular install, installing ubuntu on to its own parition(s), then it should be easy, but you can not do it from windows, windows doesn't recognize linux partitions (it will prompt you to format them).

Instead, boot from an ubuntu liveCD (or usb stick), and run the partition editor from there (system > administration > partition editor). You can resize the "/" parition easily, but you may have to right click the swap partition and select "swap off" first. Then right click the light blue extended partition  (if any) and resize that first. Its like a container which contains ubuntu partition(s). After resizing the extended, you can resize the ubuntu Ext3 or Ext4 partition itself. It takes a LONG time though, and under no circumstance abort the process once you started it, before it finished.
 > 
Thank You very much,
and excuse me for being a New-B :DDD
MCW

Why would you apologize? We were all noobs when we started using linux :)

---

### Post by McWeirdo on 2009-09-28
Hi P4Man,
Thank You for the reply!!
The modem isn't a router, it has only 1 ethernet port , the modem is Terayon TJ715, it sucks.
I'll try the ifconfig(i guess ipconfig?) but It would take me time to re write it cause I can't copy paste it (no internet on that one :P), but It's ok ,I've sent an email to my ISP provider, It will take few days before they'll answer , so I thought its easy and I'm wasting their time , just wanted to try Ubuntu with it's full power ASAP ( cause I see I must have internet using ubuntu).
 
about the second question,
I've booted with the LiveCD , went into the partition manager, right clicked the swap aprtition and pressed swap off, now I tried to resize the Extended partition, but couldn't it says maximum size is 5840 MB ( what i dedicated for it), I missed a step??
 
and btw, I only have ext3 , and not ext 4 .
 
Thank you very much!!!!!
 
MCW
 
EDIT:
Lol, ok i forgot that i first need to shrink my main (windows) C: partition :P
doing it right now , and I will check if it will work.
 
2# Yep , It's in the process :D it will take 40 min... but  one thing that worries me.. when I shrink my windows partition , I shrinked from right to left , as I should(AFAIK), but when resizing the extended, I had to enlarge it from right to left, the unallacoated area was in the left of this partition... is it wrong?
and excuse me for my English...

---

### Post by P4man on 2009-09-28
> **McWeirdo said:**
> Hi P4Man,
Thank You for the reply!!
The modem isn't a router, it has only 1 ethernet port , the modem is Terayon TJ715, it sucks.
I'll try the ifconfig(i guess ipconfig?)

no, i**f**config. you're on linux now, not windows :)
I guess there is no need to type the entire output, i just wanted to see if your network card (usually identified as eth0 or eth1) gets an IP address from the modem or not.

I did some googling on the modem, and from what I could find, the modem sucks lol, but shouldn't need any special software over ethernet, unless your ISP requires it; Try unplugging the modem (power cable and ethernet), then reconnect the power and wait a minute or so, then reconnect the ethernet and see if it helps (this should work on a the live CD as well, so you can try it while you're changing partitions ;) )

---

### Post by P4man on 2009-09-28
> **McWeirdo said:**
> 
2# Yep , It's in the process :D it will take 40 min... but  one thing that worries me.. when I shrink my windows partition , I shrinked from right to left , as I should(AFAIK), but when resizing the extended, I had to enlarge it from right to left, the unallacoated area was in the left of this partition... is it wrong?


NO, thats entirely normal. By shrinking the windows partitions "to the left", you made room to its right, and therefore you can expand the extended and then later the ExT3 volume in that same direction (to the left). Not sure what else you were expecting?

---

### Post by McWeirdo on 2009-09-28
> **P4man said:**
> NO, thats entirely normal. By shrinking the windows partitions "to the left", you made room to its right, and therefore you can expand the extended and then later the ExT3 volume in that same direction (to the left). Not sure what else you were expecting?
 Aight So I'll test the i_F_config in a moment, I need the modem so I can write here :D and I'll get the laptop near the stationary... and I know this modem sucks, that's what we're paying for here :P
so I'll report what's going on with ifconfig..
 
about the partitioning , I realized that when I shrinked the main partition to the left' i gave extended more room to grow, but seems reasonable that i somehow should move the "Extended" to the left of the Unallocated space and just then expand it... jsut seemed reasnable ... guess I'm wron, and weird the partitioning now says one hour and half to go, while it said 40 min last time i checked :O
well another thing is, how can i quick reply in this forum!?!! I couldn't find the quick reply icons that they ask ,lol :P
 
Thank You for your [EMAIL="help!@%"]help!%[/EMAIL]!!!! :guitar:

---

### Post by P4man on 2009-09-28
> **McWeirdo said:**
>  weird the partitioning now says one hour and half to go, while it said 40 min last time i checked :

It may well go up further; I told you it takes a LONG time. Depending how big the drive is, several hours would be to be expected. If its a laptop, make sure its not on batteries.

the good news however, is that while it runs, you can try/test the network connection :)

---

### Post by McWeirdo on 2009-09-28
Ok so I tried connecting the thernet cable , it said eth0 connection established , and it said it's active, went into mozilla tried ot enter a website(any) it didn't work... basically I'm NOT connected :SS
 
wrote ifconfig and I got:
Link encap:Ethernet Hwaddr:xx:xx:xx..................... xx for numbers and letters.
inet addr: 85.xx.xxx.xx Bcast 85.xx.xx.xxx.xxx mask:xxx.xxx.xx.x
inet6addr and so on....
 
in the packets thing its states : no errors no dropped, in other words everything is 0 except it says RX packets 162 and TX 65
hmm, this is the information required??
 
 
Thanks again :D
 
MCW
 
EDIT
Now I've done IPconfig in windows , I get same mask and IPV6 ADDR is the same is inet6addr, but the IPV4 address is nothing like any of the things in ifconfig.. but it's only different from inet addr and bcast in the last two parts of the ip.
 
EDIT2: found the quick reply thing :X

---

### Post by P4man on 2009-09-28
> **McWeirdo said:**
> 
wrote ifconfig and I got:
Link encap:Ethernet Hwaddr:xx:xx:xx..................... xx for numbers and letters.
inet addr: 85.xx.xxx.xx Bcast 85.xx.xx.xxx.xxx mask:xxx.xxx.xx.x
inet6addr and so on....


It looks like you got an IP address. Perhaps its a DNS problem. See if you can reach google website using IP:
[http://216.239.59.147](http://216.239.59.147)

---

### Post by McWeirdo on 2009-09-28
Couldn't reach google with this IP :< 
it said that although the address seems valid , firefox couldn't establish a connection bluh bluh make sure you set up the fire wall and bluh bluh ....
 
I edited my last post with some more information ...
 
Thanks :)
MCW

---

### Post by P4man on 2009-09-28
hmm... so if I understand you right, the IP (v4) address you get in windows is totally different from that in ubuntu? Not sure if that really is a problem, but try this in a terminal:

```
sudo dhclient -r
sudo dhclient 
```

The should force  a new IP lease from the DHCP server (which I assume is your modem). After that, try ifconfig again, see if anything changed?

Also, try this in a terminal:

```
route -n
```

The last line should be something like
```

0.0.0.0        ** 192.168.1.1**     0.0.0.0         UG    0      0        0 eth0

```

Im particularly interested in the IP address of the number I put in bold (your default gateway).

---

### Post by McWeirdo on 2009-09-28
ok , the dhclient didnt change the IP, and it's the same as it was before( well not suprising cause my ip is not dynamic) .
 
about the route :
in ubuntu :
85.64.XXX.1
 
in windows
85.64.YY.1
 
so it's different in 1 part...
and the ip is different in the last 2 parts ...
it means something is wrong??
 
thanks once again :P

---

### Post by oldfred on 2009-09-28
I know when I plugged a different computer into the modem it would take 45 minutes for the cable co to recognize a new mac address. I then learned to spoof the mac address but found it easier just to buy a router so I did not have to switch cables and mess with mac addresses. This may be your problem? The mac address should be the same as it is the same hardware, but it may be a similar timing issue.

---

### Post by McWeirdo on 2009-09-28
Hmm could be , cause I haven't tried for longer than 10 minutes...
but when the laptop is with windows and i switch bewtween them it takes a second, so maybe it's not the problem, but I'll try when I will finish the partition thing.
 
thanks for the comment :D

---

### Post by P4man on 2009-09-28
> **oldfred said:**
> I know when I plugged a different computer into the modem it would take 45 minutes for the cable co to recognize a new mac address. I then learned to spoof the mac address but found it easier just to buy a router so I did not have to switch cables and mess with mac addresses. This may be your problem? The mac address should be the same as it is the same hardware, but it may be a similar timing issue.

I think its something along those lines, although I imagine the mac address would be identical between windows and ubuntu on the same machine. Unless the OP is switching machines.

Either way, it probably is something trivial, and probably not even OS related.. Id try again unplugging and resetting the modem, wait 10 minutes, reconnect ethernet,  renew IP lease (see command above),

---

### Post by McWeirdo on 2009-09-28
I am switching machines (laptop and stainoary).
I will try to unplugg and reset and etc and I will report tomorrow :)
thank you for all your kind help P4man! 
I think the partioning is done :D

---

### Post by McWeirdo on 2009-09-28
It didn't work :<
I'll just wait for a call from my ISP(hope it's gonna be tomorrow...) , and I will post wat they've told me to do ,so other people that have the problem will know what to do.
 
Thank You for your help, I hope I will like ubuntu very much :P

---

### Post by oldfred on 2009-09-28
You said:
```
well not suprising cause my ip is not dynamic
```

We have assumed you are using DHCP which is how all the default setting are nowadays since most people use dynamic settings.

You need to find all your settings and in system, preferences, network connections, click on your connection in wired, edit, it will ask for password, then IPv4 settings, change from auto (DHCP) to manual, then add your ip settings. This can be done from ifconfig but reuires all the parameters so it is difficult to type in one line.

If you do not have a set-up page from your ISP you can copy your settings from the working windows computer.

Your ISP may not be helpful. They usually only have the script for Windows and do not know how to get to the correct screen for Ubuntu. 
If you can not figure out all your settings, get everything you can from your ISP and someone here should be able to help you.

---

### Post by McWeirdo on 2009-09-30
> **oldfred said:**
> You said:
```
well not suprising cause my ip is not dynamic
```We have assumed you are using DHCP which is how all the default setting are nowadays since most people use dynamic settings.

You need to find all your settings and in system, preferences, network connections, click on your connection in wired, edit, it will ask for password, then IPv4 settings, change from auto (DHCP) to manual, then add your ip settings. This can be done from ifconfig but reuires all the parameters so it is difficult to type in one line.

If you do not have a set-up page from your ISP you can copy your settings from the working windows computer.

Your ISP may not be helpful. They usually only have the script for Windows and do not know how to get to the correct screen for Ubuntu. 
If you can not figure out all your settings, get everything you can from your ISP and someone here should be able to help you.

 Hi, I called the ISP, they said they have no Linux experts or W/E today, so they'll call me back tomorrow. I'll try what You just wrote, sorry if I was misleading, anyway after a deep research I also discovered that I should get this : pptp-linux package and all the dependencies and the dependencies of the dependencies, which sounds so fun!! :+}} Ok i'll try the IP thing, thank You!!!

---

### Post by McWeirdo on 2009-09-30
Well I wrote all the IP settings, but couldn't figure out the DNS SERVER , I think I'll wait till tomorrow, I hope they'll call :S I can't wait to see Ubuntu with Internet, I already have fun with it , and I'm not even connected ! and it's good to know there is such an helpful forum!! Thanks.

---

### Post by oldfred on 2009-09-30
When in Windows open a cmd and run ipconfig -all and it should show all your settings. I am using DHCP but it still shows settings for DNS.

---

### Post by McWeirdo on 2009-09-30
This is annoying, I didnt manage to connect . tried to insert the details manually , it didn't work. the ISP dude just called me, asked me to do all sort of ping tests ,finally he said that it's probably the network adapter and that I should install the network adapter drivers to linux(ahhmmm where should I get them??).And I accidentally deleted eth0 connection, so I messed everything up, I'll probably reinstall it unless there are any other suggestions? thanks :D

---

### Post by oldfred on 2009-09-30
Unless you have something really weird in the way of a network adapter, linux has the drivers installed.

In network connections will it not let you add a eth0?

Do you have a network interfaces file?

I just copied this from another thread.

You can edit your /etc/network/interfaces to assign a static IP to your ethernet card.
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 208.67.222.222 208.67.220.220

---

### Post by McWeirdo on 2009-10-01
> **oldfred said:**
> Unless you have something really weird in the way of a network adapter, linux has the drivers installed.

In network connections will it not let you add a eth0?

Do you have a network interfaces file?

I just copied this from another thread.

You can edit your /etc/network/interfaces to assign a static IP to your ethernet card.
auto eth0
iface eth0 inet static
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 208.67.222.222 208.67.220.220

well when I connect the modem to the pc it says " Auto Ethernet" connection, and not eth0. I have no idea how to recreate eth0. I'll try the thing that you wrote from another thread when I come back,I really hope it'll help  cause if not ,I need to reinstall ubuntu so that the isp guy will have no excuses :<  I really appreciate your help. Thank You.  MCW

---

### Post by P4man on 2009-10-01
Try this:
Right click the network manager (network icon top right), chose "edit connections". Under "wired" click "add". Leave everythng at default or blank settings, just give it a name (say 'test') and on the first tab, change MTU from "automatic" to "1500". Click "apply". Then left click the network manager icon, and select your "test" connection.

If that fails, then find a thumbdrive. Open a terminal and type 


```

cd Desktop
ifconfig > networkinfo.txt
lspci > hardwareinfo.txt

```
(note lspci is LSPCI in lowercase)
That will put 2 text files on your desktop. Copy them to your thumbdrive, and post the contents from another computer.

---

### Post by McWeirdo on 2009-10-01
"You can edit your /etc/network/interfaces to assign a static IP to your ethernet card"
Ok, just tried that, and I couldn't save the file, it said I have no permission , :S.
 
and P4man
I made the test connection, at first it didn't show up when i connected the modem, but after a restart it did, but still didn't work... :<
and I'm still missing the eth0 thing, maybe I dropped this detail before:
when I connect the modem it says connection to "Auto ethernet" established  it was eth0 before, 
now the thing is that I need to enter my ISP'S Portal and enter my UN and PW, While I've done it in windows the ISP guy told me that I should first disconnect from windows and just then connect via linux( so i booted to vista and disconnected) and when i'm back to linux, it still didn't work...
 
here are the files: just censored a bit.
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
02:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
06:00.0 FireWire (IEEE 1394): JMicron Technologies, Inc. IEEE 1394 Host Controller
06:00.1 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
06:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
06:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
06:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller

eth0      Link encap:Ethernet  HWaddr 00:XX:8b:cf:17:XX  
          inet addr:XX.64.101.XX  Bcast:85.XXX.101.XXX  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:XXXX:1784/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:67396 (67.3 KB)  TX bytes:6008 (6.0 KB)
          Interrupt:248 Base address:0x2000 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:27 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1988 (1.9 KB)  TX bytes:1988 (1.9 KB)
wlan0     Link encap:Ethernet  HWaddr 00:22:fa:ce:b0:7a  
          inet6 addr: fe80::222:faff:fece:b07a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
wmaster0  Link encap:UNSPEC  HWaddr 00-22-FA-CE-B0-7A-30-37-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
 
So what do You think it is??
 
Thank You.

---

### Post by P4man on 2009-10-01
IM pretty sure its a problem with the network card driver. There are a gazillion bug reports relating to that  same specific network card. Such as here:
[http://ubuntuforums.org/showthread.php?t=1277425&page=3](http://ubuntuforums.org/showthread.php?t=1277425&page=3)

The good news is that most ppl seem to have it working stable with Karmic (ubuntu 9.10), but that version is not released yet, will be released in about a month (though an alpha version is available).

I assume you don't have wireless in the house to use ad interim? If not, well, perhaps you might as well download Karmic, and boot from a cd or usb stick and see if it helps. If it does fix your network problem, then I can't stop you from installing it :) just be aware karmic is NOT finished, has tons of updates every day, and some of those may break your install. Running it from a live cd/stick to test your network should be completely safe though, so grab it here:

[http://www.ubuntu.com/testing/karmic/alpha6](http://www.ubuntu.com/testing/karmic/alpha6)

---

### Post by McWeirdo on 2009-10-01
I will :D  thanks. Will report.  MCW.

---

### Post by P4man on 2009-10-01
eh, just noticed I linked to your own thread instead of the bug report(s).
I meant to give this link:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347711](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/347711)

---

### Post by McWeirdo on 2009-10-01
Ok,
You have to hear that!!
I've tried to launch ubuntu 9.10 with the live cd, and surprisingly It didnt work!!!!
I mean it took about 20 minutes just to get to an ubuntu screen or what ever, so i 
booted into ubunu 9.04 and after that the modem was disconnected from either pc for about an hour i connected it to the pc and it said connection to test established as always but now I can surf!!!

this is funny and weird, but in fact im writing from linux now.

but It's still not satisfing cause there are bugs as you said and I don't want to wait 30 minutes before changing frmo 1 os to another... but still...


thanks for your help!

---

### Post by oldfred on 2009-10-01
To edit any system file you have to use sudo for the terminal or gksudo for a graphical program like gedit.
I like to use Naulitus to find the file in computer and then use open with another application and at the bottom use a custom command where I enter "gksudo gedit" withoutquotes in the window that opens. 
That way I am only at root for this one change and have not opened a gksudo nautilus that can allow you to make mistakes since everything you do is at root.
If you are using two computers I still think your issue may be different mac addresses. The cable co or provider sees a new unique device and has to assign a new ip. If you have the same mac address it knows you and immediately connects. One advantage of a router is that only the router mac address is seen by the cable co.

---

### Post by McWeirdo on 2009-10-01
I see,
well If i change directory till i get to the directory the system file is in.
and then i just write in terminal  :
gksudo gedit filename?

---

### Post by oldfred on 2009-10-01
It is not in terminal but in naultius. Open with, then open with other applications (not double click), use custom command and in a one line window type in gksudo gedit.  After you do this gksudo will be a choice in other applications and you can click it.

[IMG]file:///tmp/moz-screenshot.jpg[/IMG][IMG]http://ubuntuforums.org/home/fred/Screenshot.png[/IMG]

---

### Post by oldfred on 2009-10-01
I tried posting screen shot but it did not work. When I checked it was too large anyway per rules.

---

### Post by McWeirdo on 2009-10-01
Oh I see... Not so hard :d
and its good to know..
thanks.
btw, now that im connected to the INTERNET, do you recommend doing something ? like updating stuff?
I mean I did some updates and installed basic things... but seems something is missing.

another question a bit OT:
can i make shortcuts to commands?
like instead of writing sudo get-apt
I'll write "sga" or just doing shortcuts on the desktop , like when i doubleclick it it will open the terminal and write something as I configured it would?

thanks!!

---

