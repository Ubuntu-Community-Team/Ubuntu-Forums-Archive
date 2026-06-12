---
title: "Help urgently needed :(My laptop cant use its wireless(at all) in ubuntu"
date: 2011-06-08
forum: General Help
---

### Post by whoopwhoopgod on 2011-06-08
hey guys , i would really appreciate help,something seems to be wrong with my laptop,the wireless does not work at all in ubuntu.

i dual booted it and it works fine in windows.perhaps its due to the fact that i accidentally deleted my panel bar this morning and went online and just copied in some codes to get it back ? i really need help guys please , i have college soon and i need to get it running or my parents might force me to shift back to WINDOWS :(

this is what i think might be the problem or some indicator of it.should i try to change it as a super user ?(what is that by the way ?) 


-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:c9dfc000-c9dfffff
i'm using a ideapad z470 if that is any help

---

### Post by mike555 on 2011-06-08
You will probably need to connect to an ethernet connection to download the drivers for the wireless Internet.......... just connect ,then click on System> Administration > hardware drivers ..

---

### Post by whoopwhoopgod on 2011-06-08
ok i tried that but it says there is an error and it asked me to check my var/log which came up with this

2011-06-08 09:36:05,327 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa084aec>
2011-06-08 09:36:06,363 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-06-08 09:36:07,180 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-06-08 09:36:07,251 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-06-08 09:36:07,290 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-06-08 09:36:07,347 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-06-08 09:36:07,505 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

what can i do ?(this part ame up highlighted so i'm assuming its the problem ?)thank you so much for trying to help me :) i really appreciate it ,i'm a realy computer noob

---

### Post by astrobob.tk on 2011-06-08
> **whoopwhoopgod said:**
> ok i tried that but it says there is an error and it asked me to check my var/log which came up with this

2011-06-08 09:36:05,327 DEBUG: updating <jockey.detection.LocalKernelModulesDriverDB instance at 0xa084aec>
2011-06-08 09:36:06,363 DEBUG: reading modalias file /lib/modules/2.6.38-8-generic-pae/modules.alias
2011-06-08 09:36:07,180 DEBUG: reading modalias file /usr/share/jockey/modaliases/b43
2011-06-08 09:36:07,251 DEBUG: reading modalias file /usr/share/jockey/modaliases/disable-upstream-nvidia
2011-06-08 09:36:07,290 WARNING: Could not open DriverDB cache /var/cache/jockey/driverdb-OpenPrintingDriverDB.cache: [Errno 2] No such file or directory: '/var/cache/jockey/driverdb-OpenPrintingDriverDB.cache'
2011-06-08 09:36:07,347 DEBUG: loading custom handler /usr/share/jockey/handlers/broadcom_wl.py
2011-06-08 09:36:07,505 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

I suggest that you first reboot your system.
After rebooting, recheck the "Hardware Drivers" & post here what it lists. Sometimes you will find 2 drivers for the the same device.

> 
what can i do ?(this part ame up highlighted so i'm assuming its the problem ?)thank you so much for trying to help me :) i really appreciate it ,i'm a realy computer noob

We all were at first. don't be discouraged by a few problems here & there, coz we are here to help, unlike Windows.

---

### Post by whoopwhoopgod on 2011-06-08
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers) 

oh god , i feel like crying right now,i feel kind of proud and happy as well,i looked it up and foundout lots of other peoples STA thing wasnt working so i followed the steps and voila ! i have it working now

god i love using ubuntu,it may be more difficult sometimes than windows but it comes along with a sense of achievement and being able to say you did something by yourself(sorta)without sending it to the shop

thank you to the both of you for caring enough to try and help :) i love the ubuntu community and shall try to help out others as well :D

---

### Post by astrobob.tk on 2011-06-08
> **whoopwhoopgod said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing%20STA%20drivers) 

oh god , i feel like crying right now,i feel kind of proud and happy as well,i looked it up and foundout lots of other peoples STA thing wasnt working so i followed the steps and voila ! i have it working now

god i love using ubuntu,it may be more difficult sometimes than windows but it comes along with a sense of achievement and being able to say you did something by yourself(sorta)without sending it to the shop

thank you to the both of you for caring enough to try and help :) i love the ubuntu community and shall try to help out others as well :D

though I have the STA on my Studio XPS, but what mike555 suggested was the only thing i did to make it work.

anyways, Great :D & Congratulations :guitar:

P.S.: Please mark the thread as solved for others to find the solution.

---

### Post by whoopwhoopgod on 2011-06-08
hey guys i cant seem to put the thread as solved :/ i tried out theread tools but its not working :(

---

### Post by astrobob.tk on 2011-06-09
> **whoopwhoopgod said:**
> hey guys i cant seem to put the thread as solved :/ i tried out theread tools but its not working :(

Did you try loging out & int again ?

---

