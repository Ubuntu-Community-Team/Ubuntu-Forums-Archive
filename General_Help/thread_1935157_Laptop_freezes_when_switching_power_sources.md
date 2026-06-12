---
title: "Laptop freezes when switching power sources"
date: 2012-03-03
forum: General Help
---

### Post by Bill Gates Foundation on 2012-03-03
[IMG]http://www.notebookreview.com/assets/28106.jpg[/IMG]

> **Technical Specifications:**

[LIST]
[*]Windows Vista Business (32-bit)
[*]Intel Core 2 Duo Processor T7500 (2.20GHz, 4MB L2, 800MHz FSB)
[*]Mobile Intel P965 Express Chipset
[*]Intel Wireless WiFi Link 4965AGN (802.11a/g/n)
[*]2GB 1GB x 2 PC2-5300 DDR2 SDRAM (maximum capacity 4GB)
[*]160GB Fujitsu MHW2120BH
[*]8x DVD (+/-R double layer) drive
[*]15.4" diagonal widescreen TFT LCD display at 1680x1050 (WSXGA+, Matte)
[*]**256MB NVIDIA Quadro NVS 130M (up to 255MB additional shared)**
[*]Bluetooth version 2.0 plus Enhanced [[COLOR=darkgreen]Data[/COLOR]]("http://www.notebookreview.com/default.asp?newsID=4071#") Rate (EDR)
[*]Type II PC-Card Slot
[*]5-in-1 media card reader
[*]VGA out, Mic/Headphone connectors, IEEE-1394 (FireWire), Three USB 2.0 ports, Serial Legacy Port, 1Gb LAN, Docking Connector
[*]Dimensions (WxDxH Front/H Rear): 13.2" x 11.1" x 1.43"
[*]Weight: 6.3lbs w/standard battery
[*]75W (15V x 5A) 100-240V AC adapter (15oz)
[*]5100mAh Lithium Ion battery
[*]3-Year Standard Limited Warranty
[/LIST]


11.10 worked like a dream, NVIDIA worked with i think 173-updates or 173-updated-dev(cant remember)
AC/DC worked 100%

12.10 clean install on XP......

Not sure if its related, but  on 12.10 NVIDIA drivers are causeing freezes at start splash screen, "nomodeset" bot working (ive tried everything under the sun trying to nvidia working....splash screen freezes with vertical lines.....
.

---

### Post by Bill Gates Foundation on 2012-03-04
nope, problem is back.......locks up when messing w/ power cord........

12.04, the degrade "pm-utils" trick from 1.4 to 1.3 did not work.in 12.04, syn app removed a lot of important files, and ubunut will not function with either 1.3 install or nothing install, it must have 1.4, it has a lot gnome stuff and if you get rid of 1.4, it will be stuck in the log in screen, when you log in, it just logs you back out 2 seconds later

My laptop does dim properly, so that is not the bug I have.

edit:

maybe this is the problem:
[https://wiki.ubuntu.com/Kernel/PowerManagementRC6](https://wiki.ubuntu.com/Kernel/PowerManagementRC6)

[http://www.kubuntuforums.net/showthread.php?57550-Freezes-after-latest-updates](http://www.kubuntuforums.net/showthread.php?57550-Freezes-after-latest-updates)
[TECRA A9 LAPTOP - UBUNTU on XP.  NVIDIA drivers now working (lockup on splash screen)

---

### Post by Bill Gates Foundation on 2012-03-06
post #50 worked


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745)

> [John Doeee (craigslist45414)]("https://launchpad.net/%7Ecraigslist45414")             wrote             4 hours ago:                                                            [ #155]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/comments/155")                                                               change this bug to critical.....12.04
 12.04 on Tecra A9 Toshiba with NVIDIA NVS 300
 I can't not beleive this is going on past two years.........THIS BUG IS CRITICAL!!!!!!!!!!!!!!!!!!!!!!!!  People want to unplu and plug in a laptop....This should not be a guessing game....
 ?-downgrade to pm 3.0
 ?- edit true) wireless_powersave off
 ?-laptop-mode-tools
 ?-adding to the etc/modprobe.d/blacklist.conf
 ?-echo powersave > /sys/module/pcie_aspm/parameters/policy
 btw, I want to add: nothing has worked but i put in "nomodeset" at  splash in grub boot......it stopped this problem but i am unable to get  the correct resolution......its stuck on like 800x600........a weird  thank that would happen is mouse laser light would turn off when on  battery power.....I would click the mouse and the mouse light would come  back on, and it does not crash.....
 but damn, i cant work on 800x600
CRITICAL CRITICAL CRITICAL!!!!!!!!!!
 c

              
                                                                                                                                     [John Doeee (craigslist45414)]("https://launchpad.net/%7Ecraigslist45414")             wrote             1 hour ago:                                                            [ #156]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/656745/comments/156")                                   
                            #50 worked for me.......about 20 hours of trial and error.........
 1. make sure the bit is not excutable
2. use terminal sudo commands becuase you wont have permission to cut and paste.....
 etc\lib does not excist on 12.10, so just do the path of /usr/lib/pm-utils/power.d/pcie_aspm.
 thank you, i am tired of staying up till dawn searching bugs.....
 i dont want to see this bug in 12.10 or beyond







.
actually, i just found out on a new install that #50 alone did not work,.,,,
**Nouveau firmware has to be removed from Synaptic**

---

