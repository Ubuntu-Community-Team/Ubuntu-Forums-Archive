---
title: "No Terminal?"
date: 2010-02-05
forum: General Help
---

### Post by Grimmjow-Akutabi on 2010-02-05
Hey guys, i've just installed Ubuntu off of the disc and i've come across a major problem, or so it seems. I have no terminal. I've been told I can find it under System Tools, but it's not there. 

I can't connect to the internet via Ubuntu so i'm currently typing this off of a W7 boot. Any idea why the Terminal isn't there? I can't install my dongle drivers without it =/

Thanks guys,

Grimmjow

---

### Post by chewearn on 2010-02-05
Applications > Accessories > Terminal ?

---

### Post by lewisforlife on 2010-02-05
How about:

```
alt+f2
xterm
```

or:

```
alt+f2
gnome-terminal
```

or:

right click on the desktop, click create launcher, name it and in the command type either xterm or gnome-terminal.

or:

ctrl+alt+f1

---

### Post by Grimmjow-Akutabi on 2010-02-05
> **chewearn said:**
> Applications > Accessories > Terminal ?

This worked thanks. Sorry for the noob question, my friend said it was in System Tools.

Sorry to ask more but, is there a way to install my Dongle's drivers from the disc without ndsiwrapper? Just, I need to download that, and I have no internet via Ubuntu, and I can't connect an ethernet cable to my PC cause i'd have to go through the floor. 

Sorry about this guys,

I can obviously download files via Windows if that is any help,

Thanks again,

Grimmjow

---

### Post by chewearn on 2010-02-05
If the dongle disc contains Windows driver, I don't see a way to install it without ndiswrapper.

Have you trying plug in the dongle and see if you can connect?  Maybe it actually works with Linux kernel natively?

After you plug it in, if you can't find any connection in the Network Manager (network icon in the top right), try these commands to find out what's going on.

This will show the last 20 messages from the kernel:
```
dmesg | tail -n 20
```This will list the USB devices:
```
lsusb
```This will show the detected network hardware:
```
lshw -c network
```This will show available network devices:
```
ifconfig -a
```

---

### Post by Grimmjow-Akutabi on 2010-02-05
OK well lsusb gave me this;

Bus 001 Device 002: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 046d:c047 Logitech, Inc. Laser Mouse
Bus 002 Device 002: ID 045e:0730 Microsoft Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Shall I paste you what the others say too?

---

### Post by chewearn on 2010-02-05
Ok, I found this page:
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper))

---

### Post by r_s on 2010-02-05
well I think your friend was talking about fedora.

---

### Post by NFblaze on 2010-02-05
Root Terminal is located in System Tools. No real big difference though.

---

### Post by ranatanveer on 2010-02-05
yes

---

### Post by Grimmjow-Akutabi on 2010-02-05
> **chewearn said:**
> Ok, I found this page:
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper))

It says the page doesn't exist?

Is there anyway I could download ndiswrapper on Windows and put it onto Ubuntu some how?

---

### Post by NFblaze on 2010-02-05
> **Grimmjow-Akutabi said:**
> It says the page doesn't exist?

Is there anyway I could download ndiswrapper on Windows and put it onto Ubuntu some how?

Have you tried the Ndiswrapper sourceforge page:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

---

### Post by Grimmjow-Akutabi on 2010-02-05
> **NFblaze said:**
> Have you tried the Ndiswrapper sourceforge page:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

My dongle is on the supported list, if that's what you mean. Or do I need to look at something else?

Sorry.

---

### Post by chewearn on 2010-02-06
> **Grimmjow-Akutabi said:**
> It says the page doesn't exist?

Is there anyway I could download ndiswrapper on Windows and put it onto Ubuntu some how?

Sorry, for some reason, the last character in the url was missed.
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29")

---

### Post by Grimmjow-Akutabi on 2010-02-06
> **chewearn said:**
> Sorry, for some reason, the last character in the url was missed.
[https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29")

OK that's cool. I can download the files there, but I have to do it while on Windows. I have a seperate hard drive that I can put the files on, but how do I run them in Ubuntu? 

Is there a way to to download ndiswrapper on my Windows machine and run it on Ubuntu? 

Thanks,

Grimmjow

---

### Post by frt975 on 2010-02-06
Yes, just save it on your windows machine and then click on your windows partition and find the file you downloaded.

---

### Post by Grimmjow-Akutabi on 2010-02-06
> **frt975 said:**
> Yes, just save it on your windows machine and then click on your windows partition and find the file you downloaded.

OK. So I can find the files I downloaded, but how do I install/run them? 

Eg: I download ndiswrapper and save it to my storage partition, how do I then run and install ndiswrapper?

Or, those files that were in the link I was sent above?

---

### Post by chewearn on 2010-02-06
> **Grimmjow-Akutabi said:**
> OK. So I can find the files I downloaded, but how do I install/run them? 

Eg: I download ndiswrapper and save it to my storage partition, how do I then run and install ndiswrapper?

Or, those files that were in the link I was sent above?

The [link]("https://help.ubuntu.com/community/WifiDocs/Device/TP-Link_TL-WN620G_%28ndiswrapper%29") has all the information you need.  But I understand it could be confusing, since the instruction is not easy.

If you need detail guidance, here is what you need to do first:

Step 1: tell us which Ubuntu version you have installed.
If in doubt, run this command and post the output:
```
cat /etc/lsb-release
```

Step 2: to be sure your hardware is exact match to the one described in the guide (it's better to be 100% sure)
```
lshw -c network
```
Post the full output here.

---

### Post by Grimmjow-Akutabi on 2010-02-06
I installed Ubuntu 9.04 (Or so my disc says).

And when I put in lshw -c network I got this;



WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:16:cb:13:05:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by chewearn on 2010-02-06
> **Grimmjow-Akutabi said:**
> I installed Ubuntu 9.04 (Or so my disc says).
Okay, roger that.

> 
And when I put in lshw -c network I got this;



WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 92:16:cb:13:05:8b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yesWell, looks like the wifi hardware is not showing up.  Sorry for the doubt, but do you have the dongle plugged in when running this command?  Just want to be 100% sure.

Also, if you could plug the dongle in, then wait 10 seconds or so, then run this command:
```
dmesg | tail -n 20
```Sorry for the long preamble, but I'm just trying to be thorough.

P.S. Please add [noparse]```
 
```[/noparse] tag between the command's output for easy reading.

---

### Post by Grimmjow-Akutabi on 2010-02-06
Yeah, the dongle was plugged in, but it wont turn on because of no drivers being installed. It was the same on Windows, wouldnt turn on until I installed the drivers. I'll go try that code now for you, and post back the results.

---

### Post by Grimmjow-Akutabi on 2010-02-06
OK. When I put in ```
dmesg | tail -n 20
``` I got;

```
[   13.136019] hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
[   13.702665] lp: driver loaded but no devices found
[   13.762592] Adding 1349420k swap on /dev/sdb7.  Priority:-1 extents:1 across:1349420k
[   14.291958] EXT3 FS on sdb6, internal journal
[   15.157724] type=1505 audit(1265467634.517:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2164
[   15.194674] type=1505 audit(1265467634.554:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2168
[   15.194741] type=1505 audit(1265467634.554:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2168
[   15.194770] type=1505 audit(1265467634.554:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2168
[   15.194797] type=1505 audit(1265467634.554:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2168
[   15.295835] type=1505 audit(1265467634.654:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2173
[   15.295949] type=1505 audit(1265467634.654:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2173
[   15.315128] type=1505 audit(1265467634.674:9): operation="profile_load" name="/usr/sbin/mysqld-akonadi" name2="default" pid=2177
[   15.335435] type=1505 audit(1265467634.694:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2181
[   17.432084] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.432087] Bluetooth: BNEP filters: protocol multicast
[   17.446590] Bridge firewalling registered
[   18.364087] ppdev: user-space parallel port driver
[   22.641089] eth0: no link during initialization.
[   22.641495] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   39.976671] UDF-fs: No VRS found

```

That help?

---

### Post by chewearn on 2010-02-06
Too bad, the dongle doesn't show up at all.

Well, assuming the device "Atheros Communications, Inc. AR5523 (no firmware)" is the correct one, here is the next step.

Step 3: Install ndiswrapper
I am following the instruction give here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Insert the Ubuntu LiveCD into the CD drive, while your Ubuntu install is already booted and running.  After a few seconds, a dialogbox should pop-up, asking whether you want to add the LiveCD into the software repository.  Answer YES.

Open: System > Adminstration > Synaptic Package Manager

Enter "ndis" into the search box.  You should see an item called "ndiswrapper-utils-*".  Go ahead and install this package.

---

### Post by chewearn on 2010-02-06
Please unplug the dongle while doing the following steps.

Step 4:
Copy/unzip the WIFI windows driver into the desktop.

Step 5:
Run these command (one by one).  If there is any error message, please stop and post the error.

Navigate to the folder containing the inf file:
```
cd ~/Desktop/2007*/Win2000_XP/Driver\ Files/
```Step 6:
Install driver:
```
sudo ndiswrapper -i net5523.inf
```Step 7:
Confirm device is found (post the output from this):
```
sudo ndiswrapper -l
```Step 8:
Activate driver:
```
sudo modprobe ndiswrapper
```

Step 9:
Now, plug in the dongle and check if you can now find connections in the Network Manager.

---

### Post by Grimmjow-Akutabi on 2010-02-06
OK. No dialogue box popped up.

I was wondering, could I just download ndiswrapper to the storage partition, copy it to the desktop, and install it from there?

See, I downloaded ndiswrapper on here earlier. Surely there is a way to install it if I have the files?

Just to make sure, if that is possible, could you give a download link that will definately work? I spent a while looking for files that I have seen mentioned and didn't notice 'em in the Utils folder.

Thanks,

Grimmjow

---

### Post by chewearn on 2010-02-06
Okay, here are the direct download links for Ubuntu 9.04

If you have 32bit Ubuntu:
[http://packages.ubuntu.com/jaunty/i386/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/jaunty/i386/ndiswrapper-utils-1.9/download)
[http://packages.ubuntu.com/jaunty/all/ndiswrapper-common/download](http://packages.ubuntu.com/jaunty/all/ndiswrapper-common/download)

If you have 64bit Ubuntu:
[http://packages.ubuntu.com/jaunty/amd64/ndiswrapper-utils-1.9/download](http://packages.ubuntu.com/jaunty/amd64/ndiswrapper-utils-1.9/download)
[http://packages.ubuntu.com/jaunty/all/ndiswrapper-common/download](http://packages.ubuntu.com/jaunty/all/ndiswrapper-common/download)


To find out whether you have 32bit or 64bit Ubuntu, run this command:
```
uname -m
```

If it says "i686", then you have 32bit.
If it says "x86_64", then you have 64bit.

---

