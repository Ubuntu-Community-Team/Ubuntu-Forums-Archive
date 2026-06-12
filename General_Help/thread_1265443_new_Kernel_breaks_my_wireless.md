---
title: "new Kernel breaks my wireless?"
date: 2009-09-13
forum: General Help
---

### Post by ARhere on 2009-09-13
Hello All,

I installed Ubuntu 9.04-64bit addition and started downloading apps. at a hotel using a cheap wireless card I bought at Fry's.  I noted the download rates are high, around 180KBps to 500KBps.  I did this before doing updates so the Kernel is 2.6.28-11-generic.

I then updated the OS which loaded the new Kernel, 2.6.28-15-generic, and after rebooting my wireless cannot stay connected.  It keeps dropping out and when a connection stays alive long enough to download anything, it is around 15KBps.  If I reboot and select the old kernel in Grub, the connection is like before.  I am sure it is a driver issue because rebooting in Windows Vista gives me a consistent 50KBps.

I know someone is going to say, "so use the kernel that works for you" but I would like to learn more about the problem.  Has anyone else had similar issues?  Can someone clue me into how to find out what is going on?

**lspci of my NIC:**
04:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

-AR

---

### Post by beastrace91 on 2009-09-13
Just to be clear the Wifi card still works 100% fine in the older kernel correct? I know you want to debug the issues but regressions are not unheard of in kernel updates. Is there a specific reason you want to use the newer kernel?

~Jeff

---

### Post by ARhere on 2009-09-13
> **beastrace91 said:**
> Is there a specific reason you want to use the newer kernel?
~Jeff

Basically I have always upgraded whenever there are updates with Linux.  I have never had a problem like this before.  Unlike Windows where I check _every_ update.  ;-)

The interesting thing is I am unable to reproduce the problem now.  Both kernels are now behaving fine with the wireless.  
[QUOTE=RESULTS:] Linux Vortek 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
[www.speedtest.net](www.speedtest.net)
5.68Mb/s down
2.55Mb/s up
[www.ubuntu.com](www.ubuntu.com)
download from U-utah
>675KB/s with dips every 25 seconds

Linux Vortek 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
[www.speedtest.net](www.speedtest.net)
5.47Mb/s down
2.70Mb/s up
[www.ubuntu.com](www.ubuntu.com)
download from U-utah
>675KB/s with dips every 22 seconds[/QUOTE]

I don't understand it as this has been a problem for the past month I have been in this hotel.  But my results above prove it must be something else.  Maybe the hotel WiFi was recently upgraded?  Who knows.

Thanks anyways, -AR

---

### Post by Scombr0 on 2009-09-13
I have same problem as you (or almost same), and have same card. The difference is that when I want to connect using DHCP it says it can't assign IP. And when I configure IP it says it cannot stablish connection with the access point.

**lspci of my NIC**:

01:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)

I don't know what the problem is, i'm using wirc. Now i'm wired, it's the only way i can connect :(

---

