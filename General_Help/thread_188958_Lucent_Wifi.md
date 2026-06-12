---
title: "Lucent Wifi"
date: 2006-06-04
forum: General Help
---

### Post by kop316 on 2006-06-04
Hello everyone

I just got an old laptop and put Xubuntu on it. All works fine, except for my Wifi card. It is a Lucent Technologies card, and the odd thing is, the Live CD sees it and even connects to the internet, but when I install it into my system, there is no trace of my card.
How can I try to reconnect it?

Thanks
Chris

---

### Post by dipswitch on 2006-06-04
I had the same problem except my card is a Linksys WPC54G. It worked fine with the live CD but I couldn't see my card after fresh installation. I searched around and found that when I installed bcm43xx-fwcutter from the repositories I could see and configure my card but my problem is that it always shows that its disconnected.

edit:  Here's the thread where I got the info for my card but as you can see at the last post I'm still stuck. Maybe this info will help you with yours.

[http://www.ubuntuforums.org/showthread.php?t=186538]("http://www.ubuntuforums.org/showthread.php?t=186538")

---

### Post by grsing on 2006-06-04
No guarantees, but [http://www.ubuntuforums.org/showthread.php?t=185174&](http://www.ubuntuforums.org/showthread.php?t=185174&) might help.  It's not for your specific card, but it's had some success with random ones, and, especially for dipswitch, since bcm43xx-fwcutter already seems to have done something, it's definitely worth a shot.

---

### Post by kop316 on 2006-06-04
I would try that, except for there is no trace of the card, as if it isn't even plugged, in. I have tried to detect it (using the lspci and the lshw), but I do not see how I can.
Speaking of which, does anyone know a GUI way on Xubuntu to look through the devices connected?

---

### Post by kop316 on 2006-06-04
ok well on the live CD i used the "sudo lshw -C network" command and it gave me the following.

*-network
        description: WaveLAN/IEEE
        product: Version 01.01
        vendor: Lucent Technologies
        physical id: 0
        slot: Socket 0
        resources: irq:3
*-network
        description: Wireless interface
        physical id: 1
        logical name: eth0
        serial: 00:02:2d:53:6f:a9
        capabilities: ethernet physical wireless
        configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Lucent/Agere 7.28 link=no multicast=yes wireless=IEEE 802.11b

---

### Post by kop316 on 2006-06-04
Ok I figured out the problem. It was not the Card, but it was the PCMCIA Card drivers that were to blame. Once I reinstalled them (I got them from the debian repositories), I had no problems.

---

### Post by jackparcel on 2006-06-20
hI,

  Recently i bought a LUcent Technologies Orinoco Silver Wlan pcmcia for my laptop... I've already intstalled the driver but my i couldn't connect to the router  because the ip was not configure automaticallly by DHCP. THe ip should be 192.168.8.***  but it was 169.**.**.** and the subnet mask 255.255.0.0

Anyone here can help me with this matter..??? Really appreaciate..Tq. currently i'm using Win XP Pro

---

