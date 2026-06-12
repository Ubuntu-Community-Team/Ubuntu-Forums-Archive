---
title: "Please help, newb needs help with detting rid of ubuntu"
date: 2010-07-02
forum: General Help
---

### Post by birdie_in_texas on 2010-07-02
my friend has a laptop that came with windows media center.

it had some issue and he let one of his fellow workers take it home to try and help and this guy ended up putting ubuntu on it but also tried to load XP Home as I guess they did not have the actual media center disk, but it does have the windows ID code sticker thing on it..

So I am trying to see exactly what is on the drive but do not know how in ubuntu..

what I am hoping is that the laptop manufacturer left a "rescue" partition on the drive and that I can simply try and boot to it and "restore" windows..but I am a total n00b and have no idea how to get rid of the ubuntu partition that is on here..

Can anyone help me please?

Thank you very much..

birdie

---

### Post by CharlesA on 2010-07-02
You can try to see what is on the drive by using gparted:

Hit alt+F2 and then type in gksu gparted.

If there is an NTFS partition, then that's probably got Windows on it.

Gparted will also tell you the label of the partitions, so hopefully there is a recov ery partition that you can use to reinstall Windows.

---

### Post by birdie_in_texas on 2010-07-02
thank you very much..

i try that and it is asking for a password..

no one knows what the password is..

it says i cannot run it from root with a password..

holy frijoles batman..this is seeming to be a mess..

---

### Post by Linux&amp;Gsus on 2010-07-02
You could try then with a GParted LiveCD, or any Ubuntu Install CD for that matter.
E.g. if you have a Install CD around you could boot from a Ubuntu Install CD and go up to the point where it's asking you to partition the HDD. There you choose to do it manually and so you can look at the partitions. Just don't change anything or the mess might be even bigger.

Though better might be to make yourself a GParted LiveCD.


Cheers,
L&G

---

### Post by Don1500 on 2010-07-02
You can use G-Parted from the live CD (That's the CD you use to load Ubuntu) just open a live session (do not install Ubuntu) and hit ALT-F2 and type in gparted. You will not be asked for a password.

By the way, the password Ubuntu is looking for is the user password, not the "root" password as it would be in Fadora

---

### Post by birdie_in_texas on 2010-07-02
I will attempt to do these things..

thank you all very much for y our help..!

---

### Post by louieb on 2010-07-02
What release of Ubuntu? Knowing that will help us know what tools a available. 

```
cat lsb-release
```

Try this to see the disk layout -  System> Adminstration > Disk Management

Your not going to get far without knowing the users  password - reset it [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Don't know if windows is fixable without an install cd - once you find the users password -  download and run this script - [Boot Info Script: SourceForge.net:]("http://bootinfoscript.sourceforge.net/")  - instructions on how to use are on the page.

---

### Post by birdie_in_texas on 2010-07-02
9.1 Karmic Koala

---

### Post by louieb on 2010-07-03
9.10 has Disk Management - You can use it to see the partition layout of the hdd. 

Did you get the password or reset it.

If you need more help - really need the output from the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  With a password it can be run from the hdd install (preferred)  - or no password  -  you'll have to get and run it from  a live CD.

---

### Post by birdie_in_texas on 2010-07-03
I made the live cd and it boots to the menu just like the pictures show it should, and I just leave it on the "Try Ubuntu without Installing" and hit enter, and it just makes a little beep noise and sets there..

It will not do anything..but I can use the arrow keys to move up and down the list, but no matter what I select with the enter key, nothing happens..

So I removed the Live CD and tried to boot back up and try to reset the password, but this is what I get on the screen after about 5-10 seconds of the machine booting..

this is what it says:

Booting from local disk...
GRUB loading.
error:  no such partition
grub rescue>

that is it..it will not boot to ubuntu anymore..

it just sets there with the cursor flashing after the grub rescue> line

I have no idea what has happened..

So I broke out an old bootdisk from like win98 that has fdisk on it..

I run fdisk and it shows that there is no active partition on disk 1

but there is something there..

I have tried to format, but it says it is unable to format..

I am totally confused and lost at this point..even more so than last night..as last night at least it would boot up..

Could the live cd have done this?  I put the live CD in one of my test boxes here and it worked flawlessly..played with 10.04 for an hour..

Is there a way to just completely bring this hard disk back to a new/never formatted state at this point?

---

### Post by johnuk09 on 2010-07-03
You can just put a Windows setup CD in, wipe the partitions (even if they're in an unknown file system format) and then install Windows from fresh...right? You don't need to go into Ubuntu at all...

---

### Post by freundfire on 2010-07-03
If you run fdisk and it shows that there is no active partition on disk 1, there must be something missing..

---

### Post by birdie_in_texas on 2010-07-03
yep..there is something there or else it would show it as "disk 0" and not disk 1 like it does now..

I downloaded the live CD again and it is now booting on the laptop..

no idea why the other disk would not work..

so in a few minutes I hope to have this resolved..

will gparted allow me to delete the linux partition while the live CD is running on the machine..?

---

### Post by birdie_in_texas on 2010-07-03
well..now I am confused again..

gparted shows that under the "partition" tab at the top..everything is "greayed" out..it will not let me select "new", or "delete" or any other command..

on the machine itself, it only shows this:

/dev/sda  (111.79GiB)

and in the main part of the screen it shows "unallocated" under "partition", "unallocated" under "File System" and 111.79 under  "Size"

so I don't get it..

where is the partition that had the GRUB thing on it..?

the way it looks, there is nothing on here..yet I still am not able to format from the windows XP install disk (he has to have XP due to his work software only operating on XP)

Any clues here fellas?

Thank you for all the help and ideas so far..  :)

Maybe this drive has taken a dump..?

---

### Post by birdie_in_texas on 2010-07-03
under "Device Information" is shows:

Model: ATA WDC WD1200BEVS-0
Size:  111.79 GiB
Path:  /dev/sda

Partition table:  msdos
Heads:  255
Sectors/track:  63
Cylinders:  14593
Total sectors:  234436545

Why would the partition table be "dos"..?

---

### Post by birdie_in_texas on 2010-07-03
ok..

I have found an issue..

this crappy old XP disk he has is only SP2 and will not see the SATA hard drive.

I am going to have to slipstream SP3 onto and create a new boot disk..this should allow me to finally reformat and install from the disk.

I will post results..

Thank you all very much for the help..

I am also going update my laptop to the new 10.04 and continue my endeavor to never have to use windows again..

---

### Post by louieb on 2010-07-03
> **birdie_in_texas said:**
> 
Why would the partition table be "dos"..?

99% of the PC's out there use the old msdos partition table. Probably will be that way until hdd sizes regularly get above 2TB - thats the msdos size limit.  

If you suspect the drive - might want to use the Disk utility  and check the smart status. Most drives made in the last 10 years have smart diagnostics built-in - not perfect but it can give you an indication that the drive is good or has problems and probably should be replaced.

---

### Post by birdie_in_texas on 2010-07-04
Well..I feel very foolish..

There was no "problem" at all..

I did not realize that with the age of this laptop, it had a SATA hard drive and I only needed to slipstream updated drives and create an XP SP3 disk and all was well..

Thank you all for the help, it is much appreciated!

---

