---
title: "Boot resumes after keypress?"
date: 2009-07-15
forum: General Help
---

### Post by Kredible on 2009-07-15
Hello everyone, I am new to the whole linux system and the community forums aswell, I have had some issues in the past regarding dual boot with Windows / Ubuntu 8.04, and I gave up on it, but I decided to give it another go, this time with a pre-made partition created bymyself and all went fine, and as for now I do like Ubuntu 9.04 quite much. I've been peeking the forums for a couple of weeks and I see this is a somewhat different community when it comes to help the newbies :) so here's the thing:

Whenever I startup my computer (Laptop ACER Aspire 5920G) and after going into the GRUB boot selection to boot Ubuntu, sometimes (most of the times) it starts loading and I see the HDD led turning on and off which means data is being red/transferred but for like 3,4 or maybe 5 times (rare) it just stops but comes back on after I press anykey, so basically to boot my Ubuntu I have to stick around with it and it's like those classic cars engine hehe.
Anyway, in my low-computer hardware skills I googled for an issue I had on Windows Vista right when the laptop came out of the box: The HDD led was going crazy as long as the disk activity which led to a 2min. computer freeze, and I came across this article that solved it with some registry tweaking 


 > I recently ran into this issue at work. As far as I can tell Intel's new SATA controller requires very special hardware that supports some new special power mode for hard drives (Link Power Management or LPM). If your hard drive doesn't support LPM then, by default, Intel's controller still attempts to send LPM commands to the drive which causes the computer to freeze for 10 - 30 seconds and it creates two events in the event logs. You should see Event ID 9 from Source iaStor and Event 51 from source Disk (See below for full event log text). Intel has an article about his issue (See Below), but they seem to only acknowledge this issue with Windows Vista. I experienced this issue on two brand new Panasonic Toughbooks that were running Windows XP Pro SP2. Apparently if your hard drive is new enough or if you update the firmware to support LPM, then this won't be a problem for you.

[HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\iaStor\Parameters]
 
 to
 
 [HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\iaStor\Parameters.Bad]
 
 Then reboot and see if that fixes your problem. Good Luck! 
Could this be related? Since it locks-up the HDD?

Can one come up with any idea to solve this?

Thanks :)

---

### Post by Kredible on 2009-07-21
Well, that was...disappointing. :confused:

---

### Post by Kredible on 2009-07-23
I still have faith in this thread :) so I got an update: when I was messing with Usplash themes to change the boot loading appearence, not knowing why I chose one that wasn't working, which made the boot show up as text loading with the [ OK ] brackets, so I am guessing there's this list of Start-up applications that are being loaded before I get to the GNOME Desktop, but the load cycle doesn't seem to be correct. 

Why does this happen aswell when Ubuntu does the check disk? 

I got to the point where I fold my mouse (it's an arc mouse so it folds lol) and drop it on top of the space bar.

Please someone with this issue, or ANY idea in mind so I can google something specific, because this is the only big issue that bothers me about ubuntu, it's that my other Vista partition is loading much faster than Ubuntu :\

Thanks

---

### Post by crazy dave on 2009-08-01
There seems to be a problem with the proprietary graphics card drivers which are non open source.

I had problems with freezes on startup (i needed to hold a key down to get it going) in Jaunty and after a bit of searching found advice in the forums suggesting that the Nvidia drivers (in my case) should be disabled.

Go to System, Administration, Hardware Drivers and disable the proprietary driver for your graphics card.

It worked for me and reboot was fine.  Good Luck.

---

