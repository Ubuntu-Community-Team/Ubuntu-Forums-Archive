---
title: "GRUB with a 2 partitioned windows"
date: 2009-10-24
forum: General Help
---

### Post by hogman500 on 2009-10-24
Okay so grub will not simply boot a 2 partitioned windows. It is not a hardware problem it is simply that grub just cant boot a 2 partitioned windows. If you have recently installed windows (i believe only vista and 7 do the 2 partitioned thing but not sure) and have reinstalled GRUB and cannot boot windows this should make it possible to boot windows again and still be able to boot your favorite Linux (Ubuntu :)). even though i don't like Microsoft specifically i do like that i can just go to a store and pick up games without worrying about compatibility.so anyway i just 2 days ago did a windows 7 install and realized that i wasent able to use grub to boot it and i spent 2 days figuring it out so hear you go a tutorial in all its glory.

**_ things you will need **_
a legal install of windows that wont boot through grub (and admin privileges)

a Ubuntu live CD

super grub disk

and a installed version of Ubuntu
**_ what you need to do **_

**step 1**

Using your super grub disk **remove** grub from your MBR (or master boot record) so windows will boot but not Linux 

**step 2**
 
Boot into windows Go **Start->Control panel->System and security->Administrative tools->Create and format hard disc partitions** once in there you will be able to modify partitions of your hard drive now you will see a partition called System reserved rite click it and select **change drive letter and paths...** and assign it a letter like i chose s: it wont matter which one.

**step 3**

Okay now that we've made it accessible you need to boot your Ubuntu live CD and go to file browser and mount ststem reserved and copy its contents to your windows 7 of vista partition excluding the temp file if it asks weather to overwrite or skip just skip it

**step 4**

Boot your super grub disk and restore grub to your MBR you should now be able to boot **Linux**

**step 5**

Boot into Linux and run the command ```
gksu nautilus
```
this should give you a root file browser so go to the file /boot/grub and open menu.lst you should have root privileges to edit this file so change your windows entry to look like this ```

title windows {7 or vista which ever one you have}
root ({hd0 for hard drive 1 hd1 for 2 and so on},{the partition what ever the number says after the ada or hda so 0 = sda 1 or hda 1 and 1 = hda 2 or sda2})
chainloader +1

```
Mine looked like
```

title windows 7
root (hd0,3)
chainloader +1

```

**step 6**

Boot up into windows 7 or vista if it diden't work make sure you have set the second part of root to the larger of the 2 windows partitions and you should now be able to dual boot Linux and windows 7 or vista and all your other operating systems.

**_Disclaimer: I am not liable for any damages or errors caused to your or anyone elses computer by this tutorial**_

---

