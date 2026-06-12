---
title: "Network and wireless"
date: 2011-04-06
forum: General Help
---

### Post by Seav Er on 2011-04-06
I've just started with ubuntu 10.10 with the commands from my friends! Now i start to set up window 7 and the wireless in ubuntu doesnt work anymore! it seems like network manager doesnt work! 
when i go to terminal it shows:
seav1er@HUYSeavEr-HP-Pavilion-dv6500-Notebook-PC:~$ lspci  
 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)  
 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
 00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)  
 00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)  
 00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)  
 00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)  
 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)  
 00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)  
 00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)  
 00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)  
 00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)  
 00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)  
 00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)  
 00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)  
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)  
 00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)  
 00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)  
 00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)  
 00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)  
 02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)  
 06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)  
 07:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)  
 07:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)  
 07:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)  
 07:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)  
 
Moreover, i start with command *rfkill list* and the responses are all NO!!  Please help!!

---

### Post by matt_symes on 2011-04-06
Hi

Welcome to the forums :D

Please open a terminal and copy and paste, using the mouse, these two commands one after another.

```
sudo lshw -C network
lspci -nnk | grep Network
```

Enter your password. It will not be echoed to the screen. This is normal.

Post the response between code tags. To do this, copy the results from the terminal and paste into your reply. Highlight the text and press the # button above where you are typing the response. This will make the text much easier to read as you can see from my code tags.

Using copy and paste will help eliminate typing errors as Ubuntu is case sensitive.

I am going to be quite busy today but it will give a start to others to look at this if i do not get the time.

Kind regards

---

### Post by grahammechanical on 2011-04-06
Do you have a laptop? If so, make sure that the wireless adapter is switched on at the keyboard. Otherwise network manager will not find a working wireless adapter and so it will not work. Also, is it possible when using Windows 7 to switch off the wireless adapter? Have you done that? If so, then this could be the reason why network manager is not working. It cannot detect a switched on wireless adapter.

Do you see the network manager icon? Is there a red exclamation mark against it? When you right click the icon, is there a tick mark against the lines Enable Networking and Enable wireless? If not, then putting the tick mark there by clicking each line. This is how networking, including wireless is turned on and off. When you left click do you see any wireless networks listed as available?

All this type of information is useful to help us advise you on what you need to do to get wireless networking working again.

Regards.

---

### Post by jnorthr on 2011-04-06
Had headless ubuntu 10.04 desktop talking to internet using an ethernet cable into an Apple iMac 10.5.8, so all settings must have been ok. worked fine for weeks.

Now have applied latest patch set from ubuntu update manager. Can ping all IP addresses on my side of our router and can ping our router 10.0.1.1, but ubuntu cannot reach any ip addresses outside our net. also lost all local eth0 and DNS names but added these back in by updating /etc/networking/interfaces which was totally empty and /etc/resolv.conf

still no joy from ubuntu 10.04. Think the routing tables must be wrong but am out of ideas. :(

---

### Post by matt_symes on 2011-04-06
Hi

> **jnorthr said:**
> Had headless ubuntu 10.04 desktop talking to internet using an ethernet cable into an Apple iMac 10.5.8, so all settings must have been ok. worked fine for weeks.

Now have applied latest patch set from ubuntu update manager. Can ping all IP addresses on my side of our router and can ping our router 10.0.1.1, but ubuntu cannot reach any ip addresses outside our net. also lost all local eth0 and DNS names but added these back in by updating /etc/networking/interfaces which was totally empty and /etc/resolv.conf

still no joy from ubuntu 10.04. Think the routing tables must be wrong but am out of ideas. :(

Ideally you should start a new thread. It's not fair on the OP otherwise. Anyways...

I don't quite understand. Your Ubuntu server is plugged into your iMac and not your router ?

Please post the output of

```
route
```

and 

```
route -n
```

Kind regards

---

