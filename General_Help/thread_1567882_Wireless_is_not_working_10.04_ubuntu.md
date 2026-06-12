---
title: "Wireless is not working 10.04 ubuntu"
date: 2010-09-04
forum: General Help
---

### Post by safety280 on 2010-09-04
Good day guys :D

I installed Ubuntu 10.04 desktop version but I have wireless problem after Installing the hardware at hardware manager. no wireless networks appears when i click on network manager. I tried to find out a solution before I post this thread, I'm sick of this problem :popcorn:   so please help !

thanks for cooperation..

---

### Post by safety280 on 2010-09-04
BTW:

```
 
lshw -C network 
```

that's what I got from Terminal:

>   ~$ lshw -C network
WARNING: you should run this program as super-user.
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
       resources: memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:23:ae:3b:9d:96
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.100 latency=0 multicast=yes
       resources: irq:28 memory:f68fc000-f68fffff ioport:de00(size=256)
 

---

### Post by kja999 on 2010-09-04
Hi,

I think you need to provide some information about your wireless card so people can advise on possible issues.
Do you know the make/model?

---

### Post by safety280 on 2010-09-04
> **kja999 said:**
> Hi,

I think you need to provide some information about your wireless card so people can advise on possible issues.
Do you know the make/model?


Hi, ):P

i'm not sure how to show my wireless card, so if you know or any one knows how to show it and fix it please tell.

thank you

---

### Post by hrickh on 2010-09-04
> **kja999 said:**
> Hi,

I think you need to provide some information about your wireless card so people can advise on possible issues.
Do you know the make/model?

It's listed right in his output - BCM 4312.  It's a Broadcom card.

R.
==

---

### Post by juil on 2010-09-04
Try these troubleshooting tips:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)

---

### Post by safety280 on 2010-09-05
> **juil said:**
> Try these troubleshooting tips:
[https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html)


thanks for helping but it did not work and i tried this website before i even wrote this thread..

i'm waiting for an affective solution

---

### Post by coffeecat on 2010-09-05
@safety280, you have a....

> description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation.... BCM4312 Broadcom wireless card. The problem with Broadcom is that, because of licensing issues, the firmware and/or the proprietary driver (I can't remember which) cannot be included in a default installation of Ubuntu. Blame Broadcom.

Anyway... it's not clear whether you've tried this, but try this first (if you can). Connect your computer to your router with an ethernet cable and boot up Ubuntu. Go to System > Administration > Update Manager and click on the 'check' button. It will download some information and may offer you updates. Don't update just yet. Close Update Manager and now open System > Administration > Hardware Drivers. Does this offer you a driver for the Broadcom card? If so, install it and you should be OK.

If that doesn't work, have a look at this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Installing the driver from the live CD should be the way to go. Boot into your installed Ubuntu (not the live CD) and set the live CD as a repository as explained in that link.

**Edit:** a friendly word of advice. I don't know whether English is your first language or not, but this...

> **safety280 said:**
> i'm waiting for an affective solution

... sounds rude and impatient in English. I'm sure you didn't mean to be but you don't want to put people off from helping you.

---

### Post by safety280 on 2010-09-05
> **coffeecat said:**
> @safety280, you have a....

.... BCM4312 Broadcom wireless card. The problem with Broadcom is that, because of licensing issues, the firmware and/or the proprietary driver (I can't remember which) cannot be included in a default installation of Ubuntu. Blame Broadcom.

Anyway... it's not clear whether you've tried this, but try this first (if you can). Connect your computer to your router with an ethernet cable and boot up Ubuntu. Go to System > Administration > Update Manager and click on the 'check' button. It will download some information and may offer you updates. Don't update just yet. Close Update Manager and now open System > Administration > Hardware Drivers. Does this offer you a driver for the Broadcom card? If so, install it and you should be OK.

If that doesn't work, have a look at this link:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Installing the driver from the live CD should be the way to go. Boot into your installed Ubuntu (not the live CD) and set the live CD as a repository as explained in that link.

**Edit:** a friendly word of advice. I don't know whether English is your first language or not, but this...



... sounds rude and impatient in English. I'm sure you didn't mean to be but you don't want to put people off from helping you.

I installed my driver from system>>admin>>hardware manager

I did it and I updated my system.. 

thank you very much for you help :D coffeecat ....

you got it right, I'm not native English and I AM SORRY if what i said offense any one..

thanks again

---

### Post by safety280 on 2010-09-05
BTW: my wireless connection is still not working..

---

### Post by coffeecat on 2010-09-05
> **safety280 said:**
> I'm not native English and I AM SORRY if what i said offense any one..

No problem. The trouble with conversing on a forum is that you don't get the facial clues and body language you need to see what the other person is feeling. Even people posting in their own language can get it wrong. I just wanted to make sure you get the help you need. :)

> **safety280 said:**
> BTW: my wireless connection is still not working..

Sorry to hear that. Did you try any of the fixes in the link I posted? Describe what you have and haven't done and hopefully someone with experience of Broadcom cards can see what the problem is.

---

### Post by safety280 on 2010-09-07
> **coffeecat said:**
> Sorry to hear that. Did you try any of the fixes in the link I posted? Describe what you have and haven't done and hopefully someone with experience of Broadcom cards can see what the problem is.


I tried all what posted but I just can't figure it out.. I Installed another network manager as well.. However, It's not working yet :/..

---

