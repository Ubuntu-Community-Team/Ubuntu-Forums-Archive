---
title: "Dual monitors not work"
date: 2010-04-20
forum: General Help
---

### Post by octopus22 on 2010-04-20
Hello friends!

I have freshly installed kubuntu with dual monitor set up.
It doesn't work with binary and open-source video drivers. Monitors just get cloned!  
I remember it worked OK some time ago, when i tried Ubuntu Live CD on this computer.

2 Screens are totaly same LG Flatron L1933S

a part of lswh:
>       *-display UNCLAIMED                                                                                     
             description: VGA compatible controller                                                             
             product: Mobility Radeon HD 3600 Series                                                            
             vendor: ATI Technologies Inc                                                                       
             physical id: 0                                                                                     
             bus info: pci@0000:02:00.0                                                                         
             version: 00                                                                                        
             width: 64 bits                                                                                     
             clock: 33MHz                                                                                       
             capabilities: pm pciexpress msi bus_master cap_list                                                
             configuration: latency=0                                                                           
             resources: memory:c0000000-cfffffff(prefetchable) memory:dfff0000-dfffffff ioport:e800(size=256) memory:dffc0000-dffdffff(prefetchable)                


Please, tell me what to do.
Many instructions are totally outdates and many variant exist at this forum.

---

### Post by P4man on 2010-04-20
Using the opensource drivers, you should simply go to system > preferences > monitors. Then make sure both are "on" and unselect "same image on all monitors" in case it would be selected.

Cant give you instructions for the binary drivers, but it should be self explanatory in the catalyst control center I think, but perhaps an ATI user can chime in here.

---

### Post by octopus22 on 2010-04-20
i'm on kubuntu, so it's a bit other thing here. 

[IMG]http://img192.imageshack.us/img192/8439/snapshot1t.png[/IMG]

Binary drivers shows the same

---

### Post by P4man on 2010-04-20
oops, sorry, missed the little K :)
I have no idea then, but I suspect you're looking in the wrong place. Im guessing that app is just to configure how KDE handles multiple monitors, but you need to set them up first, probably elsewhere. If you got the binary drivers, it would be in the ATI catalyst control center.

---

### Post by Untitled_No4 on 2010-04-20
You have two options:
First option: Use the proprietary ATI drivers for your card and manage the screens from Catalyst.
1. To do that go to System -> Hardware Drivers from the menu and install the drivers from there. 
Due to a bug in Hardware Drivers, before you click Enable click somewhere on the window but not on the driver description itself, then select the driver and click Enable. Reboot.
2. Disable xrandr by following the details in this post: [http://ubuntuforums.org/showpost.php?p=7170485&postcount=2](http://ubuntuforums.org/showpost.php?p=7170485&postcount=2) and then reboot.
3. Run Catalyst. Press Alt + F2 and type 
```
kdesudo amdcccle
```
and enter your password when prompted.
From Catalyst you can set up your dual monitors. I don't have it installed on the computer I'm currently on but it should be pretty straight forward.

Second option: Use the open source drivers and let xrandr take care of your settings. This requires some more tinkering (creating xorg.conf file, editing it, running xrandr to determine your settings and then creating a script) and I have to leave now. If you want to follow this option let me know and I'll explain how it works when later today.

First option is better if you play games and don't like tinkering around with files, second options gives you better compositing and a more responsive KDE experience, but requires a little more work.

Finally, a note for the near future: Kubuntu Lucid Lynx, out in 9 days, has newer versions of both xorg and KDE which means that setting up dual monitors will work from System Settings without any tinkering at all. You will still be able to use the first method if you want to run the proprietary drivers, using open source will be much easier.

---

### Post by octopus22 on 2010-04-20
Untitled_No4 Thank you very much! You made my day!

All is working now, i have followed binary drivers way, enable multi-monitors mode and xinerama and reboot.

---

