---
title: "network driver"
date: 2011-10-03
forum: General Help
---

### Post by dron on 2011-10-03
I am trying to set up a server on a shuttle xs35 v2.  Atom 1.6 D525 dual core CPU, Intel NM10 chipset, Intel GMA3150 graphics, 4g ddr3 and a 1tb 2.5" WD blue drive. Ubuntu server 10.4, 10.10 and 11.4 -64 will run but they are missing the network driver. How do I add the jmc driver for the jmc 251 10/100/1000 network card? Some desktop distros have the driver and they work well on the system. I am still trying to get my head around the linux term so please keep it simple if possible

---

### Post by matt_symes on 2011-10-03
Hi

To start with open a terminal and type 

```
sudo lshw -c network
```

Enter your password. It will not be echoed to the screen.

Copy and paste the results of this command back into your next post between code tags like so

[noparse]```
 results 
```[/noparse]

That will make it easy to read and produce output like so

```
 easy to read 
```

Kind regards

---

### Post by dron on 2011-10-03
I copied the info from screen
```


*-- network DISABLED

	description: Ethernet interface
	product: JME250PCI express Gigabit Enthernet Controaler
	vendor: JMicron Technology Corp
	physical id: 0.5
	bus info: pci@0000:02:00.5
	logical name: eth0
	version: 03
	serial:80:ee:73:18:70:af
	size:10Mbit/s
	capacity: 1Gbits/s
	clock: 33mhz
	capabilities: pm pciexpress msix msi bus_master cap-list enthernet physical tp mii 10bt 10bt-fd 100bt-fd 1000bt 1000 
bt-fd autonegotiation
	configuration: autonegotiate=off broadcast=yes driver=jme driverversion=1.0.7 duplex=half latency=0 link=no multycast=y
es port=Mll speed+10Mbit/s
	resources: irq17 memory:feaf4000-feaf7fff ioport: dc00(size=128) ioport: 9800(size=256)
*- network DISABLED
	discription: Wireless interface
	produce: RTL8188CE 801.11b/g/n WiFi Adapter
	vendor Realtek Semiconductor Co., Ltd.
	physical id: 0
	bus info: pci@0000:03:00.0
	logical name:wlan0
	version: 01
	serial: e0:91:53:55:08:3a
	width:64 bits
	clock:33mhz
	capabilities: pm msi pciexpress bus_master cap_list enthernet physical wireless
	configuration: broadcast=yes driver=rt18192ce driversion=2.6.38-8-server firmware=N/A latency=no multicast=yes
wireless=IEEE 802.11bgn
	resources: irq19 ioport:e8000(size=256) memory:febf000-febfffff

```

---

### Post by matt_symes on 2011-10-03
Hi
[FONT=monospace]
[/FONT]```
*-- network [COLOR=Red]DISABLED[/COLOR]
<snip>
configuration: autonegotiate=off broadcast=yes [COLOR=Red]driver=jme driverversion=1.0.7[/COLOR] duplex=half latency=0 link=no multycast=y es port=Mll speed+10Mbit/s

```The card is disabled but it has loaded a driver (jme) for the card. That suggests either the wrong driver is loaded or there is a bug in the driver (although it could be other things).

What version of Ubuntu is this 11.04 or 10.10 ?

Your wireless is disabled as well.

Need to do some research on this one.

Kind regards

---

### Post by dron on 2011-10-03
Hi
  11.4 amd alt-64 this time. 10.4 lts and 10.10 do the same thing. During install the network card is not detected. If you go back to add it manually it does not list the jme driver. It dose not find the wifi card as well. If I continue it sets up the computer provided I do not add any thing other than the basic install. If I choose to add ssh, mail,samba etc the install fails. I386 version will give the same error's

---

### Post by matt_symes on 2011-10-04
Hi

Sorry for the late response. Timezones!!!

Have a look at  this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/851070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/851070)

I am wondering if this is affecting you as, as far as i can tell, the driver should be working (unless you have the newest cards).

The poster built the newest driver from source. Could you do that ?

Kind regards

---

### Post by dron on 2011-10-04
I just downloaded the driver file and printed the how to. I have managed to do a little on a desktop system in the past but with a GUI to help me navigate. I will give it a go next time I can string some time together. (A day or two) I will post the result 

Thanks

---

### Post by dron on 2011-10-05
OK I have the driver untared into a directory called jmedp1.0.8.3. I then  cd /jmebp1.0.8.3
ls , the content is there
I then try to sudo make install and I get a no command error for make
I try sudo apt-get install make and get a not found in repository error. I have no network to download it but I do have the instillation disk mounted

several other basic commands I tried to use for the untar/ copy as by the instillation guide did not work and I ended up uncompressing onto a USB drive on my desktop computer, Mounting the drive and moving the content with sudo mv /xxxxx etc

I am running out of ideas at this point.

SO many commands to learn so many old dos commands to forget. At least that is why I started a [www.air-stream.org.au](www.air-stream.org.au) free access point and am trying to set up this server, or is it a form of madness?

thanks

---

### Post by matt_symes on 2011-10-05
Hi

I need to know exactly what you have tried so far.

Can you copy and paste what you have tried from the terminal along with all the errors ?

Kind regards

---

### Post by dron on 2011-10-06
OK
   Hard to cut/past running in a term with no GUI and not many tools working, so I installed the desktop version 10.10 amd 64. It picked up the network card and the wifi. I followed a how to and set up open ssh from a term. Rebooted and ssh in with putty. Installed samba, Apache, MySQL and P2P for luck. All inside an hour. I have an open Firefox window with the samba system and all seems to work. I now have a system with all the desktop extras that I was trying to avoid but it seems with my chosen hard wear and current skill level it may be the best for now. I hope the next version of ubuntu server x86-64 will have the driver sorted. below is the output of sudo lshw -c network for the 10.10 desktop version just for a comparison.

Thanks for the help
Darren
```
darren@ubuntu:~$ sudo lshw -c network
  *-network
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0.5
       bus info: pci@0000:02:00.5
       logical name: eth0
       version: 03
       serial: 80:ee:73:18:70:af
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.6 duplex=full ip=192.168.1.6 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:45 memory:feaf4000-feaf7fff ioport:dc00(size=128) ioport:d800(size=256)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:e800(size=256) memory:febfc000-febfffff

```

---

### Post by matt_symes on 2011-10-07
Hi

I'm glad you got it working :) even if the solution is not ideal. 

You can remove the desktop by unistalling it if you want.

As for copy and paste, maybe i should have said 'redirect the output to a file and post that'.

Kind regards

---

### Post by padapa on 2012-10-12
Matt,

Thanks for helping Darren and now me.  I have a Shuttle XS36V and in trying to setup 12.04 server found the exact same issues, so reading the thread has been helpful.

Why would a live Mint 10 distro recognize the chipset properly and have no issues and Ubuntu (which Mint is sourced from), fail to provide the current drivers.

Am I missing something here?

Also, why does server's install not include the tools to compile code.  I had to go back and install them manually.  Now I'm getting make errors, so I'm sure I missed something that is a dependency for something else.  

It is hard to fix network things without a network connection to pull packages and knowledge over.

Anyway, thanks again for the help.

---

### Post by guzzi57 on 2013-01-26
Hello,
I had the same problem. Here is the way I fixed it.
1.) download the driver from [http://driversworld.us/app/drivers/?id=8202](http://driversworld.us/app/drivers/?id=8202)
2.) copy the driver on an USB-Stick
3.) put the USB-Stick in an installed ubuntu-system
4.) mount the usb-stick "mount -t vfat /dev/sdb1 /mnt"
5.) change to the directory /mnt
6.) build the binary-files "make" maybe you have to install 
     gcc (ssh root "apt-get install gcc") and 
     make (ssh root "apt-get install make")
7.) change directory (cd)
8.) umount the usb-stick (umount /dev/sdb1)
9.) begin to install the ubuntu-server on your host
10) it stops with the message "can't find network adapter"
11) go back and open a shell
12) put your usb-stick in an usb-slot and mount it (mount -t vfat /dev/sdb1 /mnt)
13) copy your driver-binaries into the lib/modules-directory 
      (cp -R /mnt/jmebp /lib/modules/3.2.0-29-generic/kernel/drivers/net/
       cd /lib/modules/3.2.0-29-generic/kernel/drivers/net/
       cp jmebp/jme.ko .
       umount /dev/sdb1
       exit )
14) now select hardware detect. It's magic "found eth0..."
regards guzzi57

---

