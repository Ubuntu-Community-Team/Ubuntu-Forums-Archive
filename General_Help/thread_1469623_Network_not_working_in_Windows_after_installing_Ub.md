---
title: "Network not working in Windows after installing Ubuntu 10.04"
date: 2010-05-02
forum: General Help
---

### Post by stanl8 on 2010-05-02
Hi,

I was using before in dual-boot both Win7 and Ubuntu9.10. I've upgraded yesterday Ubuntu to v. 10.04 and since then a strange thing happened. My (wired) network works fine under Ubuntu. Internet connection is all right, download speeds seem normal,etc. I booted back into Win, and it informed me that my cable is not plugged in. Very weird, because in Ubuntu I had no problems. I disabled the device, rebooted, Windows re-installed the driver for me, but still, the same problem. As I was planning to do it, I even re-installed Win, but STILL, the same problem.

So now, I'm in the strange situation that I have internet connection under Ubuntu and a "please plug in your cable" message under Windows.

Please help

---

### Post by KingGuru on 2010-07-17
Did you figure it out?
After installing 10.04 on my computer in a dualboot with windows 7 no network was working in ubuntu. this morning I booted into windows and it says "network cable unplugged" I have tried a couple  of cables, that work in other computers but they don't work in the computer with dual boot. 
it's a realtek RTL8160D/8111D family card (P55 chipset)

Anyone have seen and fixet this?

KG

---

### Post by Adam1902 on 2010-07-27
Hey :),

***TLDR version below if you wish***
I'm having the exact same problem as you guys. After installing Ubuntu 10.04, first thing I did was booted under Windows (7 Professional) a couple of times to make sure everything was functioning properly, and it was (including my network and the internet). Rebooted under Ubuntu (10.04), and it worked flawlessly right out of the box, I was pretty chuffed. Later on I rebooted under Windows again, and my network logo in the system tray had the red 'X' on it, after troubleshooting apparently their was no Ethernet cable connected (and it was acting just as though that was correct, even their was a cable connected obviously and it should of worked just fine).
So I booted back under Ubuntu to try and find a solution on the web, only to discover that Ubuntu couldn't connect either! So I booted up my second PC, and that had no connection to the internet (Not the "no Ethernet cable error, it connected locally, just not to the Internet). And my third machine had the same result (both second and third machines on a legit version of Windows 7 Pro).

Basically, Windows in my machine had ZERO connectivity. Ubuntu had a local connection (could connect to router control panel through the browser), and my other PCs also only had local connection.

So I was looking for a solution myself, tried all obvious steps such as resetting the router and all network cards, Checked my router control panel to see if Ubuntu had automatically changed any settings (it hadn't), checked my DNS addresses on all machines, they were fine. Everything was setup as it should of been. Even the "Check connectivity to the Internet" in my routers control panel was showing: "DSL-Green, ATM-Red, and PPP-Red". (Obviously green meaning OK and Red meaning there's a problem)
After about 3 hours of this I gave up and went for a jog. Got back (5 hours after the problem began now?) to find that I had connectivity to the internet once again on all machines _except_ the one with Ubuntu installed on it. Windows still thought there was no network cable, and Ubuntu only had a LAN connection, but all other machines connected fine.

First I got started on Ubuntu (Windows had no hope thinking their was no cable) which was a pretty simple fix to be honest. Instead of of using DHCP I set it up manually, and pointed my DNS address to the router's LAN IP (and changed /etc/resolv.conf to point to the routers LAN IP), and now Ubuntu connects just fine. :)

Oh, also I don't think my entire internet dropping was coincidence either. Because Counter-Strike was being played on one of the other machines, and as soon as I booted into Windows and discovered the "No network cable" error, his connection dropped. It could of been coincidence but I highly doubt that.

***TLDR version starts here :)***
Now enough of my life story (well... day story),
currently all my machines are working fine, however only Ubuntu can connect to the net on this machine. Windows still thinks there's no network cable there. Any help would be massively appreciated, I've tried all possible simple solutions (rebooting router, leaving cable out of network card, updating network card drivers through windows...) which yielded no success.

I'm dual-booting Ubuntu 10.04 with Windows 7 Pro. (Let the Live CD do it's thing, I didn't create the partition before installing)
it's a wired (EDIT: On-board, attached to my GIGABIT mobo)  network card:
lshw
> product: RTL-8110SC/8169SC Gigabit Ethernet
vendor: Realtek Semiconductor Co., Ltd.From what I can see around the net, tends to have problems with Ubuntu.
The light on the card its self is constantly green, and always has been. Even when I'm in Windows, it's green, and showing every sign that it should be working correctly. Windows doesn't agree though. :P

I'm going to continue searching for possible solutions, if I find one that works I will post here. Thanks in advance for any replies, and especially if you took the time to read my entire freaking post. :popcorn:

Peace.

---

### Post by dsfargeg on 2010-08-20
I have the exact same problem! Installed Ubuntu 10.04 from Wubi, booted into it and LAN didn't work, figured it was a driver issue, rebooted into windows 7 and still not connecting just like you guys. Also using P55 motherboard (p7p55d) 

Have found no way to fix this.. Starting to think that Ubuntu destroyed the onboard network card. Anyone managed to solve this yet? :eek:

---

### Post by anirudhtomer on 2010-08-20
what kind of internet connection are you using? (Dial up or wat?)

---

### Post by dsfargeg on 2010-08-20
> **anirudhtomer said:**
> what kind of internet connection are you using? (Dial up or wat?)

We're obviously talking about LAN connectivity, how many motherboards today come with on-board dial up connectivity?

Anyway, it seems the fix is to plug your computer out of the socket for a couple of minutes, there's a long thread (with solutions) about the exact problem here: [http://ubuntuforums.org/showthread.php?t=1436667&page=1](http://ubuntuforums.org/showthread.php?t=1436667&page=1)

Short version: Ubuntu loads firmware for the wrong chipset onto the card, which can only be cleared with loss of electricity for a few minutes. It worked for me. Still a pretty horribly bug on Ubuntu devs part.

Cheers!

---

