---
title: "wireless not connecting, hpG62 laptop."
date: 2011-02-01
forum: General Help
---

### Post by abhilashm86 on 2011-02-01
I can see the connections in the above network, but if i click on that, it does not connect, but keeps on trying??
My system configration of wireless is as follows, 
```
abhilash@abhilash-G62:~/Documents$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 70:f3:95:6f:f7:85
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.35-24-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:16 memory:d3000000-d300ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 60:eb:69:1b:74:04
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:44 ioport:2000(size=256) memory:d1010000-d1010fff memory:d1000000-d100ffff memory:d1020000-d102ffff

```
My iwconfig is as follows, 

```
abhilash@abhilash-G62:~/Documents$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=18 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
ppp0      no wireless extensions.


```
What may be the exact reason and how to resolve?? In my workplace there is dns, i should give the dns setting, even then it won't connect??

But my laptop connects to Wired auto eth0 and usb internet(Tata photon+). 
Help me with wireless!!

---

### Post by darkfena313 on 2011-03-01
i have the same problem

---

### Post by abhilashm86 on 2011-04-27
> **darkfena313 said:**
> i have the same problem

I finnaly able to solve wireless problem, just needed to compile and run the proprietary driver, more information about solving wireless here [http://srikrishnadas.wordpress.com/2011/04/06/wi-fi-on-hp-dm1/](http://srikrishnadas.wordpress.com/2011/04/06/wi-fi-on-hp-dm1/)

---

### Post by Zero++ on 2011-04-27
I'm having the same issue on 2 of my laptops. I have an HP Mini duel booting Ubuntu 10.10 with windows 7 and a Toshiba booting only Ubuntu 10.10. Occasionally when they wake up from  sleep mode the Wireless Icon is gone. The hardware is still working on both systems. I know this because I have installed Cnetworkmanager and am able to establish a connection from terminal right away.

Could this be an issue with the Gnome network manager not reloading?

---

### Post by abhilashm86 on 2011-04-28
> **Zero++ said:**
> I'm having the same issue on 2 of my laptops. I have an HP Mini duel booting Ubuntu 10.10 with windows 7 and a Toshiba booting only Ubuntu 10.10. Occasionally when they wake up from  sleep mode the Wireless Icon is gone. The hardware is still working on both systems. I know this because I have installed Cnetworkmanager and am able to establish a connection from terminal right away.

Could this be an issue with the Gnome network manager not reloading?

You can try ```
sudo /etc/init.d/network-manager restart
``` to restart network manager. Sometimes it works:)

---

### Post by gauth91 on 2011-04-28
Hai i have a lenevo g560 at the beginning my lap was unable to detect the wireless network.I finally find the solution:Use lan card to connect to theinternet.Then,System->Administration->Additional drivers.This will install the required drivers.But be clear this drivers are not provided by ubuntu so they cannot able to fix if there are any errors.Try it let me know it works?

---

### Post by abhilashm86 on 2011-04-29
> **gauth91 said:**
> Hai i have a lenevo g560 at the beginning my lap was unable to detect the wireless network.I finally find the solution:Use lan card to connect to theinternet.Then,System->Administration->Additional drivers.This will install the required drivers.But be clear this drivers are not provided by ubuntu so they cannot able to fix if there are any errors.Try it let me know it works?

I'm able to connect to wireless, needless to say I tried above method long back, but it was unable to install device driver for my card. 

I had to manually install drivers from source, then it worked.

---

