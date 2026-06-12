---
title: "HELP! Switch to XP"
date: 2009-09-06
forum: General Help
---

### Post by BarefootSoul83 on 2009-09-06
I have just bout a Toshiba laptop.  It came with Vista and I got rid of it by installing Ubuntu.  However, I need XP on this machine.  Every time I try and boot from the XP cd it starts up fine but eventually gives me the "blue screen of death"... I've been reading and it seems I need to format the whole drive to NTFS.  How do I do this? I really need XP on this machine!

Thanks

---

### Post by NoaHall on 2009-09-06
Yes, you need to format it to either NTFS or FAT . Ext3 and 4 can't be used by Windows without buggy external apps.

---

### Post by wojox on 2009-09-06
You don't need to format the whole drive, just the partition xp will reside on. Boot a Live Ubuntu CD and make or find the partition for xp and format it to ntfs. Using G-Parted.

---

### Post by BarefootSoul83 on 2009-09-06
what if I decide I really just want to format the whole drive? how do I do that? (If it were me I'd leave Ubuntu on it...but this is for a lady @ work who needs her Quickbooks and is ...well...computer illiterate)

---

### Post by NoaHall on 2009-09-06
Then everything on the drive will be wiped, and it will be replaced with the format you choose. To do this, go to System -> Admin -> Partition Editor and find the right partition.

---

### Post by scrooge_74 on 2009-09-06
> **BarefootSoul83 said:**
> what if I decide I really just want to format the whole drive? how do I do that? (If it were me I'd leave Ubuntu on it...but this is for a lady @ work who needs her Quickbooks and is ...well...computer illiterate)

If you really need to trash your Ubuntu, put the Ubuntu Live CD on it again and boot from CD, use Gparted to format the drive back to ntfs, you could even make a second partition, you put ntfs (and XP) on the first one and put ext3 (and Ubuntu) in the second one.  That way you could dual boot and have both systems

---

### Post by BarefootSoul83 on 2009-09-06
there is no partition editor in there...this computer is BRAND new...nothing on it...I just used Ubuntu to kill Vista...

---

### Post by NoaHall on 2009-09-06
oh, use "sudo apt-get install gparted" in the terminal then.

---

### Post by falconindy on 2009-09-06
This might help...

I just ran into this issue at the end of this past week with a client who wanted me to downgrade her HP Pavillion dv7 from Vista to XP. Even an XP SP3 CD would blue screen on the installer. The issue was that the SATA controller was not being properly recognized and in turn, neither was the hard drive.

Solution was to create a slipstream XP install disc with nLite and include the proper SATA driver.

---

### Post by Lucky75 on 2009-09-06
This has nothing to do with ubuntu.

I'm guessing your computer has a SATA drive. XP doesn't have the drivers for SATA by default.

**OPTION 1**
You need to go into the bios, switch to compatibility mode (disable ACHI), and THEN try installing XP. You also need to download the SATA drivers and install them.

Once you do all this, you can switch out of compatibility mode. 

To download, you want the intel matrix storage driver: [http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17882&strOSs=44&OSFullName=Windows%20XP%20Professional*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2101&DwnldID=17882&strOSs=44&OSFullName=Windows%20XP%20Professional*&lang=eng)


**OPTION 2**
You can also use a floppy disk (if you have a drive) to install the sata drivers.

Edit:

**OPTION 3**
Or you can do what falconindy said above with creating an install cd of XP WITH the drivers already loaded, but if your bios has a compatibility option, look at doing this instead. It's much easier than creating another install cd with nLite.

---

### Post by P4man on 2009-09-06
either something is wrong with the machine (despite being new), like bad ram? or perhaps you're having trouble with the sata drive. The original XP doesnt like sata. You may have to slipstream SP2 or 3 into your XP cd (google for it).

Of course, you could always reinstall ubuntu, and install XP inside a virtual machine :)

---

### Post by BarefootSoul83 on 2009-09-06
Thanks guys! What Lucky said about the bios in compatibility mode worked like a charm...and it was easy.

---

### Post by scrooge_74 on 2009-09-06
Nice to hear you got it solve, mark this as solved so others know.

I had that problem with a SATA drive the other day, I was helping a friend and only had an old XP CD, it could not figure out what tha heck that HD was, got me a SP3 ver and manage to install with no problems (besides the fact that I had to install XP which I consider it a problem)

---

