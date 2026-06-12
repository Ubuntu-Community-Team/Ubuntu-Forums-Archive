---
title: "ethernet not detected"
date: 2011-01-11
forum: General Help
---

### Post by wilfredt on 2011-01-11
Hi All ,
         I was trying to get my wireless working after upgrading to 10.10 ,I somehow dont have wired connection too ,could be because of some things I tried 
I have no clue now How to get things up , I hate going back on XP
Please help

---

### Post by cogier on 2011-01-11
What computer are you using? Some laptops(e.g. Dell) switch off the ethernet connection if you are not connected to mains power. Does ethernet/wireless work with a live CD?

---

### Post by wilfredt on 2011-01-11
Hi Thanks for the reply 

This is a dell vostro 1320 , I am currently on direct power .
somehow the ethernet is not detected in hardware 
i tried lshw -C NETWORK but i dont see any entry for ethernet
also I tried demsg | eth which also shows no result 

I have a auto dhcp entry in /etc/network/interfaces

---

### Post by Hippytaff on 2011-01-11
Have you tried
```

sudo ifconfig eth0 up

```
eth0 being the name of your ethernet connection which you can find by doing
```

ifconfig

```
or
```

lshw -c network

```
the same for the wireless
```

sudo iwconfig iw0 up

```
where iw0 is the name of your wirless - found with iwconfig.
 
If none of the above works it may be something to do with your router, or drivers *for wireles
 
if you post the output of
```

lshw -c network

```
and
```

lspci -vv

```
and
```

ifconfig

```
We can try and see whats going on.

---

### Post by wilfredt on 2011-01-11
Thanks @Hippy 
sudo ifconfig eth0 up worked for me to get the wired connection up .
I am trying  for the wireless now 

here is the ouput of lshw -C NETWORK

wilfred@wilfred-laptop:~$ lshw -C NETWORK
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:9b:ad:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:46 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff
and if config 
wilfred@wilfred-laptop:~$ lshw -C NETWORK
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:9b:ad:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:46 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff


lspci -vv

wilfred@wilfred-laptop:~$ lshw -C NETWORK
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:24:e8:9b:ad:ed
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:46 ioport:3000(size=256) memory:f6004000-f6004fff memory:f6000000-f6003fff memory:f6020000-f603ffff
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0e:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:18 memory:fa000000-fa003fff

Thanks Again

---

### Post by wilfredt on 2011-01-11
@ Hippytaff Can you give me some pointers with wireless too ?

---

### Post by Hippytaff on 2011-01-11
Your wireless device is broadcom - BCM4312
 
There are some issues with the broadcom chipset, but they can be overcome. Try going to System -> administration -> recomended drivers. If there is a broadcom one there then install it. I'm going off my lunch break now, so if this doesn't work search for the chipset on the forums and google BCM4312. Others have fixed the issue...let me know how it goes :-)

---

### Post by wilfredt on 2011-01-11
Thanks @Hippytaff 
 You were right the new default drivers are working I just made new entries in /etc/network/intefaces 
 Last version I had to use a workaround with ndiswrapper .

Thanks for the help 
Have a good day ahead
Wilfred
BTW your blog if helpful too :)

---

### Post by Hippytaff on 2011-01-11
Just jumped on to see how your getting on, don't tell my boss ;-)
 
Glad you sorted it, feel free to leave a comment on the blog if you like ;-)
 
Remember to mark the thread as solved in the thread tools at the top of the page so others with the same problems can see how you fixed it :-)
 
Happy ubuntuing :-D

---

