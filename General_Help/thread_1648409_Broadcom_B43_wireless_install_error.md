---
title: "Broadcom B43 wireless install error"
date: 2010-12-18
forum: General Help
---

### Post by antwon619 on 2010-12-18
Well for starters im new to linux so im not familiar with ANYTHING...
basically for shorts im running Ubuntu on an Hp mini 1000. i got the wired connection to work. so now im trying to get my wireless to work additional drivers> activate broadcom b43. well after it "attempts" to install i get this message: "SystemError: installArchives() failed" 
for some reason the b43 firm is conflicting with everything i try to install, an to top it off i apparently don have permission to access /lib/firmware. well at least im not able to extract anything into that folder....

can someone please help me ive looked everywhere. yes ive used google... i rather use windows xp BUTi cant install it cuz well i cant install wine due to b43.... >_<

---

### Post by Verbeck on 2010-12-18
run *sudo apt-get update* from a terminal (in accessories) and try again

btw, xp/vista/7 cant be installed through wine, you'll have to boot from the cd

---

### Post by TBABill on 2010-12-18
Are you positive you need the b43 and not the STA for a Broadcom card? Can  you provide the output of ```
lspci
``` in a terminal?

---

### Post by BicyclerBoy on 2010-12-18
It is very difficult to determine exactly which HP netbook you have.
The model naming is a total shambles.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

My HP mini 110 1004TU uses the broadcom STA not B43.
I had to de-activate the B43 driver by following the above Ubuntu instructions for 1010nr.

The other install problems could be:
The netbook 10.04 live CD/USB includes the required broadcom firmware but it does not install it to HDD. So after cold reboot from new installed OS, the wifi does not work any more. This may or may not occur with 10.10 netbook edition.

Fortunately you have a  wired connection to allow you to fix the problem.

---

### Post by BicyclerBoy on 2010-12-18
Don't even dream of thinking you can install/run XP in Wine on netbook.

An OS needs a virtual machine or real bare system to install on.
This is well beyond your abilities (& the PC) 

You can use wine on the netbook to run many windows apps (some) but you may need some IT skills.
Remember a netbook is not a small powerful laptop.

I have found the ubuntu netbook edition to work extremely well & am well impressed.

---

### Post by Bucic on 2011-01-24
After I got the same error today I downloaded the driver manually and did:
```
tar xfvj broadcom-wl-4.80.53.0.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.80.53.0/kmod/wl_apsta_mimo.o
```as found here [http://ubuntuforums.org/archive/index.php/t-763995.html](http://ubuntuforums.org/archive/index.php/t-763995.html)

After computer restart I don't get the b43 listed under "Additional drivers" at all. Should it be that way?

Edit:
Another instance of the same error! This time during **Wicd** installation. Same reason - url location inaccessible.

In the meantime, can we change the number of retries from 20 to e.g. 3?

---

### Post by Bucic on 2011-01-25
The Update manager recommended to use the command. Here's what I got:
```
~$ sudo apt-get install -f
[sudo] password for hg1: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
~$ sudo dpkg --configure -a
Setting up firmware-b43-installer (4.150.10.5-4) ...
--2011-01-25 14:00:59--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... failed: Name or service not known.
wget: unable to resolve host address `mirror2.openwrt.org'
dpkg: error processing firmware-b43-installer (--configure):
 subprocess installed post-installation script returned error exit status 4
Errors were encountered while processing:
 firmware-b43-installer
~$ 

```
I did it without internet connection on purpose because the [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) URL is dead anyway and I skipped 40 timeouts and retries!

---

### Post by theozzlives on 2011-01-25
To install software, drivers or run Update Manager, you NEED to be connected!! Connect your wire first.

---

### Post by Bucic on 2011-01-25
> **theozzlives said:**
> To install software, drivers or run Update Manager, you NEED to be connected!! Connect your wire first.
I already did, tens of times. The only thing I get is connection timeouts (40 of them!) for the [http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2) URL which is dead.

---

### Post by Bucic on 2011-01-25
I decided to follow this guide [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#b43%20-%20No%20Internet%20access) since it eliminates the worse unknown (no guide teaches how to deal with inaccessible packages):

```
hg1@bleble:~$ ls 
broadcom-wl-4.150.10.5.tar.bz2  Downloads         Pictures   Videos 
Desktop                         examples.desktop  Public 
Documents                       Music             Templates 
hg1@bleble:~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
broadcom-wl-4.150.10.5/ 
broadcom-wl-4.150.10.5/driver/ 
broadcom-wl-4.150.10.5/driver/config/ 
broadcom-wl-4.150.10.5/driver/config/wlconfig_apdef 
. 
. 
. 
. 
. 
broadcom-wl-4.150.10.5/shared/sromstubs.c 
broadcom-wl-4.150.10.5/shared/xip.lds.in 

hg1@bleble:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
**Cannot open input file wl_apsta-3.130.20.0.o **
```And some wonder why people hate "terminal solutions"... :roll:

Edit:
Apparently it needs firmware to be installed first so I did as per [http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian](http://wireless.kernel.org/en/users/Drivers/b43#Ubuntu.2BAC8-Debian) in the same guide:
```

hg1@bleble:~$ cd broadcom-wl-4.150.10.5/driver
hg1@bleble:~/broadcom-wl-4.150.10.5/driver$ sudo apt-get install b43-fwcutter
[sudo] password for hg1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-installer (4.150.10.5-4) ...
--2011-01-25 17:11:40--  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Resolving mirror2.openwrt.org... 46.4.11.11
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out.
Retrying.

--2011-01-25 17:12:02--  (try: 2)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out.
Retrying.

--2011-01-25 17:12:25--  (try: 3)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out.
Retrying.

--2011-01-25 17:12:49--  (try: 4)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out.
Retrying.

--2011-01-25 17:13:14--  (try: 5)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Connecting to mirror2.openwrt.org|46.4.11.11|:80... failed: Connection timed out.
Retrying.

--2011-01-25 17:13:40--  (try: 6)  http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
Connecting to mirror2.openwrt.org|46.4.11.11|:80... 


```Guess what! Ubuntu bangs the same dead URL which was the very source of my problems in the first place! [IMG]http://forums.eagle.ru/images/smilies/doh.gif[/IMG]

---

### Post by TBABill on 2011-01-25
It looks like you are mixing up b43 and the STA driver. The STA driver's real name is "wl". So these are 2 different drivers. And from so many attempts to get this going from source and links online I'm wondering how much work you are doing is geared toward Ubuntu and how much is geared toward other distros. All distros do NOT install hardware or software the same way so you must understand what you are working with before making assumptions that a fix in openSUSE, for example, will work in Ubuntu.
 
I would suggest a fresh reinstall. You have, or had, it working with wired so it should work again if you reinstall. Then you need to come here, list your hardware by going into a terminal and entering some simple codes, then pasting back here the output with a description of what you need help with. From your posts I still have no idea which Broadcom chipset your machine uses. If you're willing to do that, just use a couple to get started: ```
lspci
``` and ```
sudo lshw -C network
```
 
EDIT: You will still need firmware, similar to what you did earlier, but the system will do it for you if you follow the assistance that can be provided if you give us some info to work from.

---

### Post by TBABill on 2011-01-25
Ok, disregard my last post. I see you have a BCM4318 Broadcom card and you are working the b43 driver...perfect. But the file seems to not be found when you ```
sudo apt-get install b43-fwcutter
``` Still looking at this and will post back if I find the answer. Looks like > b43-fwcutter is already the newest version. from your earlier post. So you have the firmware and just need to get the driver going. 
 
At this point you should be able to go to System>>Administration>>Hardware/Additional Drivers and activate the b43 driver. Have you tried that since you found the b43 option was missing from that location early on? If not, perhaps restart and then see if it's there and available to install.
 
Just to be sure, you can open the file /etc/modules and make sure the b43 is listed. This is where the driver should show up so the system enables it upon boot. And make sure the wl is not in that file because it would conflict.

---

### Post by Bucic on 2011-01-25
> **TBABill said:**
> 
At this point you should be able to go to System>>Administration>>Hardware/Additional Drivers and activate the b43 driver. Have you tried that since you found the b43 option was missing from that location early on? 
It's the obvious start for someone new. Yes, I tried that in the beginning and it was ending up on timeouts too. It seems so ridiculous that every single Ubuntu module tries to bang that poor ol dead URL, that I can't even find words for it. But I see you may be able to help me out so I'll focus on answering your questions as precise as I can.

 > **TBABill said:**
> 
Just to be sure, you can open the file /etc/modules and make sure the b43 is listed. This is where the driver should show up so the system enables it upon boot. And make sure the wl is not in that file because it would conflict.
My */etc/modules* contents:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
```Yup, that's it.

BTW, I found this [http://ubuntuforums.org/showthread.php?t=1044898]("http://ubuntuforums.org/archive/index.php/t-1044898.html")
You could take a look at the "Summarized version",bottom part of the first post.

---

### Post by TBABill on 2011-01-25
I'm going to check out the link you provided, but can you try to ```
sudo modprobe b43
``` and see if it enables? It should be listed if installed properly. May end up having to go into Synaptic and search for b43, then install any files not already installed, but that assumes it'll hit a mirror that works. I haven't done it in forever, but you can change your mirror within Synaptic to get around the URL issue I think.
 
Edit: the modprobe command will enable the driver for this session only, but should at least be able to tell if it will work or if the driver is just missing.

---

### Post by Bucic on 2011-01-25
The command return nothing, but no errors neither. Now the B43 is listed in the Additional Drivers applet. Of course the driver still can't be downloaded.

---

### Post by TBABill on 2011-01-25
Yeah you wouldn't see anything. It just activates that driver, if available, for the current session. Now that it's there, can you install?

---

### Post by Bucic on 2011-01-25
> **TBABill said:**
> Yeah you wouldn't see anything. It just activates that driver, if available, for the current session. Now that it's there, can you install?
Can't be downloaded, so can't be installed.


From your previous post:
> **TBABill said:**
> Still looking at this and will post back if I  find  the answer. Looks like  from your earlier post ```
b43-fwcutter  is already the newest version.                      
``` . So you  have the firmware  and just need to get the driver going. 
I think b43-fwcutter is just a tool to extract... or something..., but not the actual firmware.

---

### Post by TBABill on 2011-01-25
Can you go into Synaptic and see where to change your mirror? I know the option is available but I'm not on a Linux machine to be able to assist more thoroughly. Once you change which mirror you are hitting that issue should go away because you'd be getting the file from another location. Or that's the assumption I'm making...not sure since I can't see it for myself on this machine. I think once that's straight you'll be able to download and activate without much additional issue. Activation will take care of adding the driver to /etc/modules as well so it'll be there on each restart.

---

### Post by Bucic on 2011-01-25
I don't see any options to specify the source location in synaptic for specific packages. That said trying to download it is IMO a dead end. I'll try that guide I linked before.

Plus I don't really know  which packages should I install
[IMG]http://i17.photobucket.com/albums/b68/Bucic/ubuntuforumsorg/b43_broadcom_packages.png[/IMG]

---

### Post by TBABill on 2011-01-25
I believe it's one of the options along the top. Like in a Microsoft program you have File, Edit, View, etc....I think it's in one of the menus to change your mirror. I wish I were home to see it and guide better.

---

### Post by Bucic on 2011-01-25
> **TBABill said:**
> I believe it's one of the options along the top. Like in a Microsoft program you have File, Edit, View, etc....I think it's in one of the menus to change your mirror. I wish I were home to see it and guide better.
I don't believe - I checked.  Besides I don't  know  which packages should I install so I won't do it blinfolded. I'm about to start with the manual procedure...

---

### Post by TBABill on 2011-01-25
Easier method to change to the fastest available mirror...
 
System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the **[COLOR=#dd4814]fastest[/COLOR]** for you.

---

### Post by Bucic on 2011-01-25
I did exactly as "summarized version" here [http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898) says with no errors along the road but it doesn't look like it changed a thing. The b43 driver is still listed in the Additional Drivers.

---

### Post by Bucic on 2011-01-25
> **TBABill said:**
> Easier method to change to the fastest available mirror...
 
System, Administration, Software Sources.

Where it says "Download from" you can select to use the Main server, a localized server or "other" to manually select a server. 
"Other" can also test all servers to see which is the **[COLOR=#dd4814]fastest[/COLOR]** for you.
Ubuntu installers in all their moronity insist on downloading the problematic package not only from the same server but from the exact same dead URL, regardless of the sources configuration. I hope it's clear now and that we've established already that we cannot let Ubuntu access the internet in this case or else it will *k it all up again (do its usual 30 minutes 40 timeouts routine and fail).

Status correction:
The driver is no longer listed under Additional drivers ATM.

EDIT:
Thank you for bearing with me, **_[TBABill. ]("http://ubuntuforums.org/member.php?u=974469")_**
I'm getting more and more grumpy but please don't take it to yourself. Just try to imagine wasting a second day on such a %$#@


And here's my latest attempt with the same procedure but with the latest driver instead of the one linked there. This time error did occur
```

hg1@bleble:~$ sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
[sudo] password for hg1: 
This file is recognised as: 
  ID         :  FW10 
  filename   :  wl_apsta.o 
  version    :  295.14 
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3 
Extracting b43legacy/ucode2.fw 
Extracting b43legacy/ucode4.fw 
.
.
.
Extracting b43legacy/b0g0initvals2.fw 
Extracting b43legacy/a0g0bsinitvals5.fw 


hg1@bleble:~$ tar xfvj broadcom-wl-4.150.10.5.tar.bz2 
broadcom-wl-4.150.10.5/ 
broadcom-wl-4.150.10.5/driver/ 
.
.
.
broadcom-wl-4.150.10.5/shared/sflash.c 
broadcom-wl-4.150.10.5/shared/sromstubs.c 


hg1@bleble:~$ sudo b43-fwcutter --unsupported -w /lib/firmware  broadcom-wl-4.150.10.5**/driver /**wl_apsta_mimo.o 
Sorry, the input file is either wrong or not supported by b43-fwcutter. 
This file has an unknown MD5sum d41d8cd98f00b204e9800998ecf8427e. 


hg1@bleble:~$ sudo b43-fwcutter --unsupported -w /lib/firmware  broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o 
This file is recognised as: 
  ID         :  FW13 
  filename   :  wl_apsta_mimo.o 
  version    :  410.2160 
  MD5        :  cb8d70972b885b1f8883b943c0261a3c 
Extracting b43/pcm5.fw 
Extracting b43/ucode15.fw 
.
.
.
Extracting b43/b0g0bsinitvals5.fw 
Extracting b43/b0g0initvals5.fw 


hg1@bleble:~$ sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy 


hg1@bleble:~$ sudo ifconfig wlan0 up 


wlan0: ERROR while getting interface flags: No such device 
hg1@bleble:~$ 
```

---

### Post by Felliph3 on 2011-01-25
Hey, I did a write up for this, it might be outdated by now but should still work.

[http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898)

Give it a try, its pretty simple. 

What I usually do is install Ubuntu and then connect it to an ethernet connection and hit update and install the driver from restricted drivers and it works after that. Ubuntu is pretty sad with their wifi though, this stuff should be working out of the box

Let me know if it works or not and I'll try to help you

---

### Post by Bucic on 2011-01-25
> **Felliph3 said:**
> Hey, I did a write up for this, it might be outdated by now but should still work.

[http://ubuntuforums.org/showthread.php?t=1044898](http://ubuntuforums.org/showthread.php?t=1044898)

Give it a try, its pretty simple. 

What I usually do is install Ubuntu and then connect it to an ethernet connection and hit update and install the driver from restricted drivers and it works after that. Ubuntu is pretty sad with their wifi though, this stuff should be working out of the box

Let me know if it works or not and I'll try to help you
I already tried as per your how-to (see the listings above). 

I connected my ethernet too. The kind of connection present does not matter as ubuntu keeps banging a dead URL no matter what I do.

---

### Post by Felliph3 on 2011-01-25
Gee, its pretty hard to troubleshoot from here without seeing whats going on. I dont know what commands to tell you to enter like most people lol.

If you're connected to the internet you should be able to get it to work but if its trying to download a dead link then maybe check the sources for any issues? Is this a fresh install? Maybe if I could connect to it via teamviewer I could take a look?

---

### Post by Bucic on 2011-01-25
> **Felliph3 said:**
> Gee, its pretty hard to troubleshoot from here without seeing whats going on. I dont know what commands to tell you to enter like most people lol.

If you're connected to the internet you should be able to get it to work but if its trying to download a dead link then maybe check the sources for any issues? Is this a fresh install?
Yup, fresh install and the source configuration doesn't affect Ubuntu wanting to download from that particular dead link.

---

### Post by Felliph3 on 2011-01-25
Have you seen this thread? Maybe they can help
[http://ubuntuforums.org/showthread.php?t=1604868&page=9](http://ubuntuforums.org/showthread.php?t=1604868&page=9)

---

### Post by TBABill on 2011-01-25
What does ```
iwconfig
``` and ```
sudo lshw -C network
``` return in terminal? Now that you have done so much work the outputs should be different than when you began.

---

### Post by Bucic on 2011-01-25
> **TBABill said:**
> What does ```
iwconfig
``` and ```
sudo lshw -C network
``` return in terminal? Now that you have done so much work the outputs should be different than when you began.
First one
```
lo        no wireless extensions.

eth0      no wireless extensions.

```second
```

*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:1e:8c:b8:f5:1a
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=full firmware=5788-v3.26 ip=10.2.1.77 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=100MB/s
       resources: irq:23 memory:d0000000-d000ffff
  *-network:1 UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=64
       resources: memory:d0010000-d0011fff


```

I have to get some sleep now. Thanks for bearing with me! Please post your thoughts and I'll reply as soon as I can.

---

### Post by Bucic on 2011-01-26
News for today.

The problematic package is **firmware-b43-installer** * and it's marked as already installed. It can't be uninstalled via synaptic... because URL is dead. Yup, the very same URL banged to death by every Ubuntu component out there. [EDIT] *Uninstalled using Mark for complete removal.*

Properties - Installed files in synaptic says:
```
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/firmware-b43-installer
/usr/share/doc/firmware-b43-installer/NEWS.Debian.gz
/usr/share/doc/firmware-b43-installer/changelog.Debian.gz
/usr/share/doc/firmware-b43-installer/copyright
```* I found it today while going through terminal sessions I posted here.


When I try to install it again Synaptic warns me about firmware-b43-installer not being authenticated.

So it went like this:
1. Synaptic - File - Generate script
```
#!/bin/sh
wget -c ftp://ftp.man.szczecin.pl/pub/Linux/ubuntu/pool/multiverse/b/b43-fwcutter/firmware-b43-installer_4.150.10.5-4_all.deb
```2. firmware-b43-installer installed via Synaptic, the normal way. Succesfully!

Conclusion:
Firmware installer downloads and installs. And is to blame for all because it appears it's this very package that tries to access a dead URL 
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)


Anyone? :(

---

