---
title: "Two problems with 9.10"
date: 2010-02-05
forum: General Help
---

### Post by DrDaveyAtoms on 2010-02-05
I am experiencing two problems with Ubuntu 9.10 which I installed on my brand-new Dell Inspiron 1545 just yesterday. 

The first is that my wireless network card is not working and I cannot see the wireless signal coming from my router. The symbol to show how strong/weak the signal is is simply grey. The card is a Broadcom BCM4312 which I determined from running lshw -C network. The output of this command showed two devices:
```
 *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:f6cfc000-f6cfffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: a4:ba:db:96:f4:9e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.23 firmware=N/A ip=192.168.1.5 latency=0 multicast=yes
       resources: irq:30 memory:f6bfc000-f6bfffff ioport:ce00(size=256)
```I have read multiple posts in an attempt to solve this problem but none of the suggestions work. In particular I have tried to activate Broadcom STA proprietry drivers from System>Administration>Hardware Drivers but have had no luck and receive this message > Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log Can anyone point me in the right direction? 

The other issue is a repeating whooshing sound coming from what I assume is my HDD. It sounds like my disk drive is constantly writing. Also, the fans seem to be on constantly, albeit at a low rotation speed. These problems do not occur when using my Windows 7 OS on the same system. Has anyone encountered this before? Does anyone know how to solve this issue?

I am blown away by how good and easy-to-use Ubuntu is. But if these issues cannot be solved I am going to have to go back to Scientific Linux which seems like a step back.

Sorry for the long post.

---

### Post by saif_held on 2010-02-05
> **DrDaveyAtoms said:**
>  The other issue is a repeating whooshing sound coming from what I assume is my HDD. It sounds like my disk drive is constantly writing. Also, the fans seem to be on constantly, albeit at a low rotation speed. These problems do not occur when using my Windows 7 OS on the same system. Has anyone encountered this before? Does anyone know how to solve this issue?

Well I might tell you something about the second issue, which is based on a personal experience. I used to format my HDD a lot and messing with it in the stupid Windows tool and since then and it, sometimes, produces bad noises which can be justified; the bloody disk is messed. Your case? I don't know maybe broken?

The issue with the fan could be due to dust or probably something faulty in the inside. You did say that your Dell is new, so you might wanna check from where you bought it. Of course wait for some other opinions those are only some personal thoughts and I might be wrong.

Sorry I couldn't help in the 1st issue I'm no expert in the networks thing, my wireless card was instantly identified and is working fine.

---

### Post by dvlchd3 on 2010-02-05
For the wireless, try the following command:
```

sudo apt-get install b43-fwcutter

```
Select yes when it asks whether you'd like to download and extract the firmware.

This is the package that contains the drivers and firmware for Broadcom BCM43xx cards.

---

### Post by DrDaveyAtoms on 2010-02-07
Thanks for the advice. Downloaded the drivers as you suggested. However, this has not been successful. Still does not recognise the wireless network.

Does anyone have any other suggestions? If not think I might uninstall Koala and try Jaunty.

---

### Post by ShinHadoken on 2010-02-07
Strange... there were a lot of wireless drivers added to the kernel when Jaunty was released, I don't understand why yours is having such trouble. Have you considered ndiswrapping a Windows driver for your card? This may not be an exact fit, but here's the link for the Broadcom BCM4311 ndiswrapper page:

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)")

And here's the ndiswrapper page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

As for your hard drive, I suggest going into the System Monitor and see if your hard drive is being accessed by anything. Something may be writing or reading from it in the background. You did say this does NOT occur in Windows?

And the fans, I'd go into BIOS and see what they're set at. They may be set to run constantly at a specific speed. If so, your BIOS might have a "Smart fan" option or something to the like. This allows BIOS to dictate how the fan runs based on the temperature. It uses the fans only when needed.

Hope this helps!

---

### Post by Ginsu543 on 2010-02-07
Try this:

1) Connect your computer to the Internet through the ethernet port
2) Open Synaptic Package Manager
3) Type "bcm" in Quick Search
4) Click to install "bcmwl-kernel-source" package
5) Reboot and see if your wireless is recognized

When I got my Dell Mini 9 and Vostro A90, in both the wireless worked out of the box in Jaunty but not in Karmic. Installing the bcmwl-kernel-source package fixed the problem and the wireless works fine now in Karmic. If the above method doesn't work, you may want to check out the Broadcom.com website at [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and download their STA drivers directly. It specifically states that the STA drivers support BCM4312.

---

### Post by DrDaveyAtoms on 2010-02-08
Thanks for taking the time to reply. This is a very helpful community.

I have tried all of the suggestions provided thus far. Even some others on other threads. However, so far nothing has been successful. 

I will keep trying but it looks like I will not be able to roam with Ubuntu 9.10. I would like to uninstall 9.10 and install Jaunty but it seems like a big job to revert to an earlier version.

---

### Post by wojox on 2010-02-08
I have the same laptop and card. Like Ginsu543 stated:

```
sudo apt-get install bcmwl-kernel-source
```

Reboot and make sure your Ethernet cable is unplugged. ;)

---

### Post by DrDaveyAtoms on 2010-02-08
I have some new information to report.

I have finally been able to get the STA proprietary wireless driver to be activated. Yeah!

But this has not solved the problem. I still cannot detect any wireless networks in the vicinity of the laptop. This is strange as there should be many wireless networks including the one I am currently connected to on another machine and my Xbox.

Now that I have the proprietary drivers properly installed and activated, does anyone have any suggestions as to how to proceed?

---

### Post by DrDaveyAtoms on 2010-02-08
I have solved my wireless woes and I am now posting without the need of an ethernet cable.:D

The solution to this is not straightforward but I will try to explain what I (think I) did so that anyone else reading this thread may find some help. 

As posted above, the Broadcom wireless card requires Broadcom STA proprietary drivers installed and activated. However, I found I could not activate the drivers using the suggestions provided by others in this thread. 

Therefore I uninstalled all Broadcom drivers present on my system: bcmwl-kernel-source and b43-fwcutter.

I found another thread useful which pointed to the Broadcom website and a hybrid driver [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php). I used these files to create a wl.ko file which did not exist prior to download. 

After creating this file I then proceeded to reinstall bcmwl-kernel-source. I proceeded to reboot and found to my delight that my driver was activated, hence, above post.

This did not solve my problem, however, and I still could not detect any wireless networks. I noticed that on my network manager, while I had specified a wired interface eth0 I did not have a wireless interface specified. After finding that my wireless card is called eth1 I typed this into my network manager and hey presto.

Thanks to everyone who helped with this problem. It can now be marked as solved.

---

