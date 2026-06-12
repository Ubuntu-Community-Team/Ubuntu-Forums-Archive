---
title: "Uninstallation! Warrenty Problems!"
date: 2006-04-24
forum: General Help
---

### Post by asusrules on 2006-04-24
hi

i am very sad:-#  to say this those, but i would like to know how to uninstall unbuntu without any traces of it and allowing only windows to boot.
i have to return my laptop due to warrenty reasons and i dont think they will fix the problem if it has linux on it. they might blame the problem on ubuntu and i dont want to have a broken notebook. i want to make sure that i am doing the right steps instead of screwing it up even more when i just pop in the cd. So could someone please tell me how to unitstall the entire operation system?

Thanks

---

### Post by delta32 on 2006-04-24
You can format the Ubuntu partition. If you've got a bootloader like grub or lilo when you boot up, make sure to fix the mbr while you're at it.

Honestly, I wouldn't worry about it unless you signed something saying that you would not install another OS on your laptop. :P

---

### Post by asusrules on 2006-04-24
[QUOTE=delta32]You can format the Ubuntu partition. If you've got a bootloader like grub or lilo when you boot up, make sure to fix the mbr while you're at it.

Honestly, I wouldn't worry about it unless you signed something saying that you would not install another OS on your laptop. :P[/QUOTE]


how do you format the ubuntu partition? is the partition type called ext3?

thanks

---

### Post by arathorn2nd on 2006-04-24
[QUOTE=asusrules]how do you format the ubuntu partition? is the partition type called ext3?

thanks[/QUOTE]

Your best shot is getting your laptop's recovery CD and reinstalling windows, removing all partitions during the process. It'll fix everything including the bootloader.

Check your warranty details, there's hardly any concern over software, just hardware.

---

### Post by Zorro on 2006-04-24
Yes, it usually is.

I would suggest though, if you have no other file system on the laptop, i.e. only ubuntu. I would install windows, it has a format option on install.  Although in saying this I recall I had issues with the mbr after I did the same thing once, all I had to do was do a ***fixmbr*** from the windows recovery console and away it went....

---

### Post by rabidphage on 2006-04-25
Boot from the xp cd if your laptop company gave you the one with out the partitioning tools, borrow an xp cd from someone. This is the easiest method. Once the boot process is done, read the onscree info on how to access the recovery console. If my memory serves me right it is the r key. Do the need ful. You'll be taken into a command prompt. type fixmbr and press enter accept the warning and reeboot now hopefully grub will be gone. boot into windows go to device manager (right click my computer and click manage)and on the left pane click disk management. Right click the unknown partition which would be the linux partition and format or delete or whatever. find your way through. 

If you don't have the windows xp bootable rescue cd. install windows from the laptop rescue cd. beware youll lose all the data in c drive. backup if necessary before you go about doing tinkering. boot into windows and delete the partition as stated above. 

Whew that should be it. if you haven't signed anything, you'll be just fine. no bother

---

