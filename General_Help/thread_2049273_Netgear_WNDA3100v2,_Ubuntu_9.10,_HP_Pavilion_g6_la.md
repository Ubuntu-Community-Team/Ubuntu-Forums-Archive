---
title: "Netgear WNDA3100v2, Ubuntu 9.10, HP Pavilion g6 laptop"
date: 2012-08-28
forum: General Help
---

### Post by pr0gramr7 on 2012-08-28
Hello, 

I recently installed Karmic Koala from liveCD and removed Windows 7 (At least, I believe it is erased). However, it is not recognizing wireless signals. That is, the LED button on the keyboard for the internal WIFI (RaLink 5390; driver: rt2x00) just stays red. I bought an external USB adaptor (Netgear WNDA3100v2; driver: ar9170), but Karmic is not recognizing it. I am sure I need a driver somewhere. Or maybe more than that. I am not familiar with how to add the Harware Drivers in the system. And I can imagine this is more complicated because I have no internet connection on the HP. (neither Ethernet nor WIFI). 

I have provided info below and the commands connected with them for much more specific details of the problem for my more experienced readers.

1.  lspci

01:00.0 Network controller: RaLink Device 5390 

2.  lsusb

Bus 002 Device 004: ID 0846:9011 NetGear, Inc.  
Bus 002 Device 003: ID 058f:a001 Alcor Micro Corp.  
Bus 002 Device 002: ID 8087:0024   


3. lspci -nn | grep 'Wireless Brand'  

(no response. returned to prompt.)


4.  ifconfig

lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


5.  iwconfig

lo        no wireless extensions. 
 
eth0      no wireless extensions. 

6.  lsmod

Module                  Size  Used by 
usbhid                 43968  0  
binfmt_misc            10220  1  
ppdev                   8232  0  
uvcvideo               65260  0  
lp                     11908  0  
iptable_filter          3872  0  
psmouse                57124  0  
ip_tables              21200  1 iptable_filter 
videodev               43360  1 uvcvideo 
v4l1_compat            16804  2 uvcvideo,videodev 
v4l2_compat_ioctl32    13344  1 videodev 
x_tables               25832  1 ip_tables 
parport                40528  2 ppdev,lp 
serio_raw               6596  0  
r8169                  38884  0  
mii                     6368  1 r8169 
video                  23612  0  
output                  3680  1 video 


7.  dmesg 

(VERY LONG; AM NOT SURE WHICH INFO / LINE IS USEFUL; MAYBE YOU CAN HELP!)


8.  sudo lshw -C network

 *-network UNCLAIMED      
       description: Network controller 
       product: RaLink 
       vendor: RaLink 
       physical id: 0 
       bus info: pci@0000:01:00.0 
       version: 00 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress bus_master cap_list 
       configuration: latency=0 
       resources: memory:c2500000-c250ffff 
  *-network DISABLED 
       description: Ethernet interface 
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 05 
       serial: 44:1e:a1:d6:47:89 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s 
       resources: irq:33 ioport:3000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable) 



9. iwlist scan

lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning. 



10.  lsb_release -d

Description:	Ubuntu 9.10 


11.  uname -mr

2.6.31-14-generic x86_64 


12.  sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...                               [ OK ]  


As you can tell, except for number 7, I have provided all the info I thought was pertinent for the problem. Please suggest for number 7 the line of the output that would be useful.

By the way, i am a newbie. This is my second post. I think my first post might not have been detailed enough so I am trying again with specific detail.

To sum up: I want to use the Netgear adaptor, not the RaLink that came with the computer. Also, I DO NOT HAVE ANY internet access on the HP, so please, if you would be so kind, let me know STEP-BY-STEP how to download, copy and install all potential info I will have to hunt from another computer. I am prepared to hunt, but I know I lack certain techniques / know-how regarding how to check for files, memory, checksums, etc. But I will learn.

P.S. I suppose if I could access the internet from the HP I would not need to write this thread.

P.S. #2  Just a side note, could you give me an opinion about whether or not this computer is good for installing / running Ubuntu distros or any Unix distro for that matter?

Thank you in advance.

---

### Post by bart.a on 2012-10-09
check out this post.. [http://ubuntuforums.org/showthread.php?t=1383708]("http://ubuntuforums.org/showthread.php?t=1383708")

maybe it will work for you too..

---

### Post by bart.a on 2012-10-17
I have a question..

Your notebook seems fairly new, why don't you install ubuntu 12.04?
I have it running on my HP dv6 notebook and it works perfectly.. 
And I run Xubuntu 12.04 on my old HP nx9010 notebook with a netgear WNA3100 usb wifi-adapter.. That also works (a bit slow, but it's usable), the netgear adapter works with [ndiswrapper and it's windows driver]("http://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

maybe upgrading to the latest version will solve your problems..

[This]("http://http://ubuntuforums.org/showpost.php?p=10796508&postcount=44") might also be helpfull on getting it running on your current (or new) install..

---

### Post by pr0gramr7 on 2012-10-24
Thank you bart.a for your response.

I actually did install ubuntu 12.04 a couple of months ago.

It worked perfectly from day one.

Also, i was able to access the internet from day one, but only with the installed ralink WNIC.

I have not been able to get the external WNDA to work so far.

But, I was able to install the drivers and now the system recognizes the WNDA external card.

I am still working on it, along with some other projects.

Like I wrote somewhere some time ago now, Bill Gates is my enemy and I shall not
support him as long as I am conscious and as long as I can help it!

In conclusion, I think I will close the thread with a [SOLVED] label since I was able to get everything
up and running. Even though it was not with the WNIC that I wanted.

The reason I want to use the Netgear WNDA3100 v2 is becasue it is more usuful for my
security analysis needs/profession.

You probably knew that.

Thanks again for your response.

---

### Post by kurt18947 on 2012-10-24
There is another thread about the same adapter.  I believe NDISWrapper is the only way right now.

---

### Post by danielbauwens on 2012-10-24
Or maybe you should just update to 12.10
Maybe it solves your problems.

---

### Post by bart.a on 2012-10-24
So the ndiswrapper and the windows driver are installed, but it does not work?

Try booting the laptop **without** the USB adapter in a port. Log in, wait a minute and plug in the adapter..
I have this with my xubuntu and the wna3100, sometimes it can not logon to the wifi but when I reboot as discribed it works everytime..

side note:
The bottom link in my previous post did not work.. [this should]("http://ubuntuforums.org/showpost.php?p=10796508")..

---

### Post by Joseph Rinaldi on 2012-10-24
I spent hours on this but found a simply way to get this working flawlessly.
1. From the Ubuntu Software Centre, install Windows Wireless Drivers (NDISWrapper) and the two add-ons, ndiswrapper-dkms and ndiswrapper-source.
2. I installed the latest drivers from Netgear on a Windows XP computer. (Just a VM will do, can be on a Linux Box).
3. This creates a folder in C:\Program Files\NETGEAR\WNDA3100v2\Driver, called WinXP2000. This contains the latest drivers for this adapter. The .sys file should be version 5.100.68.46.
4. Copy the folder to your Ubuntu (or Xubuntu) computer.
5. Run the Windows Wireless Drivers software and point to the inf file in this folder.
6. Reboot. All done!
(Tested on 12.04)

---

