---
title: "Ubuntu 9.10 upgrade stopped touchpad functionality"
date: 2009-10-31
forum: General Help
---

### Post by samasat on 2009-10-31
Hi,

  I am newB to Ubuntu. I earlier was using Ubuntu9.04 and recently upgraded to the 9.10 using Update manager. However, after restart my touchpad has stopped working totally. :( . Being GUI user, zow I can't do anything except hitting Alt+Ctrl+Del in order to shut down.
My laptop details are :

Make: HP Pavillion dv5-1233se
Processor: Intel Core 2 Duo, 64 Bit
RAM: 4Gb
Graphics Card: Intel Graphics Media Accelerator 4500MHD

I have set up dual boot for Windows Vista and Ubuntu. I had to do some Alsa tweaking on Ubuntu 9.04 since sound was missing when I installed it which is a known problem for Ubuntu on HP laptops. 

I will appreciate if someone can suggest me way out !
TIA,

-Samasat

---

### Post by girto on 2009-10-31
Check mouse options in preferences.
IIRC, the touchpad click was disabled at some point during Karmic development.

---

### Post by ^_Pepe_^ on 2009-10-31
Hi!

In my friend's Toshiba Satellite 9.10 upgrade, we found that touchpad was disabled automatically after restart with Fn+F8 option. We just only had to reactivate it.

If not, you can also install GSynaptic to manage the touchpad closely.

Good luck

^_Pepe_^

---

### Post by samasat on 2009-11-01
Thanks Girto and Pepe  ..

 However, problem is that I can not use touchpad for mouse movement to go to any preference setting and I am not a skilled user of the command prompt.

Also,  Fn + F8 key does not work for me as it is for display settings in my HP laptop and I don't see other key combinations for touchpad or input settings.

 I can use arrow keys to get at command prompt somehow. After looking at some other threads I did attempt some commands like :

[COLOR=Blue]xinput -list   [/COLOR]           <Gave me one 'mouse' type of input device that said something           
                                like 'machintosh emulation of mouse' , all others in list were of type 'keyboard' >

[COLOR=Blue]synaptic[/COLOR]                   <warned i cannot save change since not a administrator ... though i am the only user login for ubuntu and it opened up a window and threw a message that E: driver version mismatch 
       E: failed to open() . please report >

[COLOR=Blue]synclient [/COLOR]                < ***********   No drivers installed ?>

Somehow I get the filling that the drivers are not updated....am i right ? 

 Wht commands i should use after that ?

TIA, :)

-samasat

---

### Post by girto on 2009-11-01
Connect an external mouse so that you are able to navigate.

This shows as well the importance of keyboard navigation knowledge.
- Alt+F1 opens the main menu
- TAB changes the focus to the next control (button or other)
- SHIFT+TAB changes the focus to the previous control (button or other)
- SPACE BAR clicks the focused (highlighted) button
- ESC is used as cancel button in some cases
- ENTER is used as OK button in some cases
- ALT+TAB to switch windows

Go to System / View Log Files and inspect Xorg.0.log
It will most probably show what is going on with your touchpad

---

### Post by Plumtreed on 2009-11-01
I had a similar thing but I was able to navigate with an external mouse. Hope you have one or can borrow one.

When you can navigate, check  system>administration>system monitor
to verify that you are using kernel 2.6.31 -14

My problem resulted from grub using the old 9.04 kernel in a confusing mix-up with this Grub/Grub2 business.

You could also just check what kernel grub boots into.

---

### Post by samasat on 2009-11-01
Thanks Plumtreed,

I am finding that my kernel is 2.6.28-11-generic.
Wht can i do to make it 2.6.31-14 ? ...will it affect the dual boot I set up to use windowsXP?

-samasat

---

### Post by Plumtreed on 2009-11-01
I am not sure if you are aware that when you upgrade you go to Legacy Grub but when you do a clean install you go into Grub2.

The following will give the steps needed to go into Grub2
[URL="http://https://help.ubuntu.com/community/Grub2"/URL]
You should end up with a dual boot situation but when you are able to boot into the correct kernel 9.10 should improve, of course!

---

### Post by samasat on 2009-11-01
Thanks Plumtreed. 
I hope my problem is the grub2 affair. A new problem surfaced when I was following the instruction in the suggested link. I found that the internet wireless connection is turned off in my HP laptop after I boot in Ubuntu. And its not getting back to ON state even if I try to make it ON manually the way I do in windows by touching a tower like symbol on keypad. Without internet I am not able to do anything. 
Any suggestions ?
TIA,
-Samasat

---

### Post by samasat on 2009-11-01
just to add to my struggle so far I looked in some other threads and commented out the the last 'blacklist ***' line in /etc/modprobe.d/blacklist**pci.conf file. It did NOT help me to restore internet !

-samasat

---

### Post by Plumtreed on 2009-11-02
I don't know where you have got to......can you describe what is going on?

Do you boot via Grub Legacy into 9.10 and the right kernel. Do you have 'touch-pad' control?

---

### Post by Plumtreed on 2009-11-02
You could try right & left Clicking on the network symbol next to the battery indicator and setting up your network.

On my laptop the network icon sits between the battery and the envelope!

---

### Post by samasat on 2009-11-02
I could establish wireless internet by downloading the drivers using a wired connection. SUmmarizing my recent thread learnings -  Following could be useful if you too have broadcom card. to check for that :
```
sudo lshw -C network

```if you have Broadcom it will list the network card here and its details e.g.
```
$ sudo lshw -C network
 password for XXXXX: 
  *-network               
       description: Wireless interface
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:7f:48:ba
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 ip=128.237.248.238 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:16 memory:db600000-db603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:52:8d:32
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:6000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)

```1) Connect wired connection using NIC ethernet

2) do update and upgrade:
        Code:
     sudo apt-get install update 
3) System>>Administrator >>Hardware Drivers 
select Broadcom STA and BoadCom fwcutter and activate and restart

For more information see: 
[http://ubuntuforums.org/showthread.php?t=1309760&highlight=samasat](http://ubuntuforums.org/showthread.php?t=1309760&highlight=samasat) 

-Samasat

---

