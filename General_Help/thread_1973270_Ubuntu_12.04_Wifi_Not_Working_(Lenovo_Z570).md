---
title: "Ubuntu 12.04 Wifi Not Working (Lenovo Z570)"
date: 2012-05-04
forum: General Help
---

### Post by sam4 on 2012-05-04
I recently Upgrade my Ubuntu 11.10 version to 12.04
But now wifi is not working on my Ubuntu 12.04 .

Some Info :
PC : Lenovo Z570 
Network Adapter : Atheros AR9285

$ iwconfig
> 
lo    no wireless extensions.

wlan0  IEEE 802.11bgn   ESSID: off/any
    Mode:Managed Access Point : Not-Associated   Tx-Power=off
    Retry long limit:7   RTS  thr:off   Fragment thr:off
    Power Management:off

eth0  no wireless extensions..    [FONT=Verdana]
[/FONT]$ sudo ifconfig    > eth0      Link encap:Ethernet  HWaddr f0:de:f1:54:34:a2  
          inet addr:192.168.2.2  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fe54:34a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:44257 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:43571495 (43.5 MB)  TX bytes:4926319 (4.9 MB)
          Interrupt:42 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5977 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:708983 (708.9 KB)  TX bytes:708983 (708.9 KB)

wlan0 is not showing in thils , but now when i try to use.    [FONT=Verdana]

[/FONT]$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Operation not possible due to RF-kill


  Now when i use this :$ sudo rfkill list all
 

> 1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

    Then :$ sudo rfkill list all
    > 1: phy0: Wireless LAN     Soft blocked: no     Hard blocked: yes 2: ideapad_bluetooth: Bluetooth     Soft blocked: no     Hard blocked: no 4: hci0: Bluetooth     Soft blocked: no     Hard blocked: no   Here **phy0 Hard blocked = yes**
  *Result was the same (then i again try to switch on/off wifi from keyboard by pressing Fn+F5* )


$ sudo rfkill list all
    > 1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

Now this time **phy0 Soft blocked = yes as well as hard blocked : yes**
  Here is hardwares specs :
     $ sudo lshw -class network
> *-network DISABLED      
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 68:a3:c4:9a:7e:62
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:f1900000-f190ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 05
       serial: f0:de:f1:54:34:a2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8105e-1.fw ip=192.168.2.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:2000(size=256) memory:f1804000-f1804fff memory:f1800000-f1803fff

---

### Post by chili555 on 2012-05-04
What is the position of the switch on the front? Please see attached.

---

### Post by sam4 on 2012-05-06
> **chili555 said:**
> What is the position of the switch on the front? Please see attached.

Thanks for your reply sir. By the way 2 option in the picture is for on/off wifi , i already put this in right side. (that means wifi is on from keyboard).

---

### Post by hrvooje on 2012-05-16
I'm also having this problem on Lenovo Ideapad Z570, Ubuntu 12.04. The switch on the laptop is on the right side, bluetooth is working so the switch is on. In the Gnome3 panel it says "Wireless hardware disabled". 

I tried downgrading intel driver, tried to remove n speed support, tried to blacklist acer_wmi  ... nothing helped.


```

iwconfig

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.


```

```

rfkill list all

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
5: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```

This line is confusing me phy0: Wireless LAN Hard blocked: yes
There is one more strange thing - I can't turn off 'Airplane Mode'. It is always turned on.

---

### Post by chili555 on 2012-05-16
> **hrvooje said:**
> I'm also having this problem on Lenovo Ideapad Z570, Ubuntu 12.04. The switch on the laptop is on the right side, bluetooth is working so the switch is on. 

<snip>

This line is confusing me phy0: Wireless LAN Hard blocked: yes
There is one more strange thing - [COLOR="Red"]I can't turn off 'Airplane Mode'. It is always turned on.[/COLOR]I am googling this and suggest you do the same. 

Is the key combination Fn+F4, or whatever it is for wireless on your Ideapad, sequential? That is, is one press wireless on, bluetooth on; second press wireless on, bluetooth off, etc., etc.? Please try and run:```
rfkill list all
```Is there any change in state?

Will you try a driver parameter?```
sudo modprobe -r ideapad-laptop
sudo modprobe ideapad-laptop no_bt_rfkill=Y
sudo rfkill unblock all
rfkill list all
```Any change?

---

### Post by hrvooje on 2012-05-17
You were right. Alt + F5 does change the state. Before I pressed Alt+F5 *rfkill list all* looked like this:

```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


```

After I pressed the output looked like this:

```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: ideapad_wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: yes
	Hard blocked: yes


```

After I tried what you suggested driver parameter, *rfkill list all* gave me:

```

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no


```

But unfortunately, nothing changed. Still, I can't turn off 'Airplane Mode', and gnome network applet still says 'Wireless hardware disabled'

---

### Post by chili555 on 2012-05-17
Please try: ```
sudo modprobe -r ideapad-laptop
sudo rfkill unblock all
sudo rfkill list all
```Can you you please double- and triple-check the switch on the front? See post #2 above.

---

### Post by hrvooje on 2012-05-17
I tried what you wrote and the output is:

```

3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


```

Still, hardware disabled. I triple-checked it. Please see the picture attached.

---

### Post by chili555 on 2012-05-17
I'm sorry, I have but two suggestions remaining. I suggest you search here for 'airplane mode' and Network Manager and file a bug report. [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

Second, I'd try the live CD for older versions of Ubuntu, Mint, Fedora et al and if you find one that works, install it.

I wish I could be of more assistance.

---

### Post by randomerror on 2012-05-28
I ran into the same problems as above. Only thing that worked for me was using the 3.0.0-19-generic-pae kernel from the older 11.10 release of ubuntu. I seem to have a Broadcom controler in my laptop though... 

```

#> rfkill list all
0: ideapad_wlan: Wireless LAN
        Soft blocked: no
        Hard blocked: no
1: brcmwl-0: Wireless LAN
        Soft blocked: no
        Hard blocked: no
#> lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 540M] (rev ff)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)

#> uname --kernel-release --kernel-version 
3.0.0-19-generic-pae #33-Ubuntu SMP Thu Apr 19 20:59:10 UTC 2012

```
________________________________________________________________________________________

I could resolve my issues wich where related to kernel driver issues using the following description:
[http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working](http://askubuntu.com/questions/38327/how-can-i-get-broadcom-bcm4311-wireless-working)

Now my wifi is also running with 3.2.0-24-generic-pae kernel
```

#> uname --kernel-release --kernel-version 
3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012

```

So it seemed to be some driver and driver blackist issue for me. I hope that gives you some new hints as swell...

---

