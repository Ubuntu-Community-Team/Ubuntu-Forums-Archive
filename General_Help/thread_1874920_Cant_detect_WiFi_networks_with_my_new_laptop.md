---
title: "Cant detect WiFi networks with my new laptop"
date: 2011-11-04
forum: General Help
---

### Post by Kitkin15 on 2011-11-04
Ok so i have Ubuntu 10.04 installed on my EXT HDD, on my HP Pavillion G6 i could detect WiFi, but on my new DV6. Im guessing its a Driver problem, does anyone know what driver i need or how i find out what driver ill need? Ive asked on other sites and no one seems to know what i need.

If you need more information ask and ill give it.

 Thanks

  -Kitkin15

---

### Post by docbop on 2011-11-04
Going to probably have to go to the HP website and see what wifi chip they are using.  Be sure to include the revision # of your computer because companies will change chips on same model if a cheaper one is available.

---

### Post by kurt18947 on 2011-11-04
If you'll open a terminal, type "lspci" then copy and  paste the output, that will be a start. Specifically, a line that looks like this:

03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

will tell us what wireless chip you have.  There'll likely be two lines of interest. One talking about ethernet controller which is the wired network controller and the above mentioned Network controller which is the wireless.  Of course to keep things interesting ;) a wireless connection may have a different name.

---

### Post by Kitkin15 on 2011-11-04
Ok so i ran the code, i decided to copy and paste all of it as a just incase, but the two lines your looking for are towards the bottom:

00:00.0 Host bridge: Advanced Micro Devices [AMD] Device 1705
00:01.0 VGA compatible controller: ATI Technologies Inc Device 9647
00:01.1 Audio device: ATI Technologies Inc Device 1714
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Device 1709
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Device 170a
00:06.0 PCI bridge: Advanced Micro Devices [AMD] Device 170b
00:11.0 SATA controller: Advanced Micro Devices [AMD] Device 7804
00:12.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:12.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:13.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:13.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Device 780b (rev 13)
00:14.1 IDE interface: Advanced Micro Devices [AMD] Device 780c (rev 40)
00:14.2 Audio device: Advanced Micro Devices [AMD] Device 780d (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Device 780e (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Device 780f (rev 40)
00:16.0 USB Controller: Advanced Micro Devices [AMD] Device 7807 (rev 11)
00:16.2 USB Controller: Advanced Micro Devices [AMD] Device 7808 (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Device 1700 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Device 1701
00:18.2 Host bridge: Advanced Micro Devices [AMD] Device 1702
00:18.3 Host bridge: Advanced Micro Devices [AMD] Device 1703
00:18.4 Host bridge: Advanced Micro Devices [AMD] Device 1704
00:18.5 Host bridge: Advanced Micro Devices [AMD] Device 1718
00:18.6 Host bridge: Advanced Micro Devices [AMD] Device 1716
00:18.7 Host bridge: Advanced Micro Devices [AMD] Device 1719
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
02:00.0 Network controller: RaLink Device 5390
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)

---

### Post by Kitkin15 on 2011-11-04
So i googled, and this is what i came up with:
[http://ubuntuforums.org/showthread.php?t=1645716](http://ubuntuforums.org/showthread.php?t=1645716)

Does this sound good to you guys? It looks good to me but id like to double check

Thanks

  -Kitkin15

---

### Post by Kitkin15 on 2011-11-04
Yeah.... Just tried this.... Its a little more complicated then they say because the file is now different, does anyone know how to do this?

Thanks :)

  -Kitkin15

---

### Post by Kitkin15 on 2011-11-06
UPDATE:

Ok so i got it to install, when i run Aircrack-ng i can use the Wireless Interface "ra0", but i cant see it on my panel so i cant connect to the internet, how do i fix this?

This is all i need, after this im set :)

  -Kitkin15

---

