---
title: "USB Flash Drive Not Recognized - Soultion, Anyone?"
date: 2011-02-03
forum: General Help
---

### Post by Heliophion on 2011-02-03
The hard drive on my desktop recently failed, so I ended up getting a new computer. I put a fresh install of Ubuntu 8.04 on the new computer but it doesn't auto-detect my USB flash drives. They only show up if I plug them in and then type 'lsusb' in terminal. Have been using Ubuntu since 6.06. My previous system, using the same 8.04 release, simply auto-detected the drives when I plugged them in. This is not the case with the new system. I've included the terminal messages below. Any help would be appreciated. 

```
 lsusb

Bus 005 Device 004: ID 154b:0041  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 006: ID 04b3:301b IBM Corp. SK-8815 Keyboard
Bus 001 Device 005: ID 04b3:301a IBM Corp. 
Bus 001 Device 004: ID 04b3:310c IBM Corp. 
Bus 001 Device 001: ID 0000:0000  

```

```
 sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000628a4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38539   309564486   83  Linux
/dev/sda2           38540       38913     3004155    5  Extended
/dev/sda5           38540       38913     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 4009 MB, 4009754624 bytes
145 heads, 48 sectors/track, 1125 cylinders
Units = cylinders of 6960 * 512 = 3563520 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1126     3915752    c  W95 FAT32 (LBA)

```

---

### Post by Kirboosy on 2011-02-03
Hi,

If I may ask, why exactly did you install such an old version of Ubuntu on your computer?

Anyways back to the topic on hand.

open a terminal and run
```
[B]gconf-editor
```

[/B]Then navigate to the following...**/apps/nautilus/preferences/media_automount**.

Please check to see if that key says true or false.


~Caboose

---

### Post by Heliophion on 2011-02-03
> **Caboose885 said:**
> Hi,

If I may ask, why exactly did you install such an old version of Ubuntu on your computer?

Anyways back to the topic on hand.

open a terminal and run
```
[B]gconf-editor
```

[/B]Then navigate to the following...**/apps/nautilus/preferences/media_automount**.

Please check to see if that key says true or false.


~Caboose

Thanks for your reply. In nautilus, auto-mount is checked so I assumed that means true. To answer your question, I just prefer 8.04 to later versions - its a less bloated and very stable release, plus I hate the boot-up graphics for later releases. I have an aversion to unnecessary change. In short, 8.04 just works for me and has since its release.

Any other suggestions on getting these USB drives to work? Thanks!

---

### Post by Kirboosy on 2011-02-03
Fair enough. I can understand you not liking the changes made to Ubuntu. There are some changes I don't like but I deal with...


There is another key **/apps/nautilus/preferences/media_automount_open**

If this is set to true the window will come up every time you plug in a new drive.


Or if you can't read any data off the drive you can try formating it with gParted. (This will wipe everything out so if it has important data don't do it)

---

### Post by Heliophion on 2011-02-06
> **Caboose885 said:**
> Fair enough. I can understand you not liking the changes made to Ubuntu. There are some changes I don't like but I deal with...


There is another key **/apps/nautilus/preferences/media_automount_open**

If this is set to true the window will come up every time you plug in a new drive.


Or if you can't read any data off the drive you can try formating it with gParted. (This will wipe everything out so if it has important data don't do it)

Both the keys you mention are set to true. Formatting with Gnome Partitioner doesn't help either. I mean, it formats the drive but it still isnt recognized by my system. I also formated it in Windows, that doesnt help either. Any other suggestions?

---

### Post by marshag63 on 2011-02-06
Do you have other USB ports to try - I have a laptop where one USB port will power devices, but cannot access info - realized it when another USB port worked.

So, if you have a free USB, try it. You can use the Disk Utility (palimpsest) to verify if the USB is seen by the system and try mounting it from there as well.

Hope this helps.

MDG

---

### Post by Heliophion on 2011-02-13
> **marshag63 said:**
> Do you have other USB ports to try - I have a laptop where one USB port will power devices, but cannot access info - realized it when another USB port worked.

So, if you have a free USB, try it. You can use the Disk Utility (palimpsest) to verify if the USB is seen by the system and try mounting it from there as well.

Hope this helps.

MDG

I have a total of 6 usb ports. My keyboard and mouse make use of two of them. They work fine. It just seems to be a problem with usb flash drives.

So, as of yet, I have not got this issue resolved. Any other suggestions?

---

