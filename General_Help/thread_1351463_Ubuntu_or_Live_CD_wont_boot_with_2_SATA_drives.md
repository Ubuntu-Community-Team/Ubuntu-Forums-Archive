---
title: "Ubuntu or Live CD wont boot with 2 SATA drives"
date: 2009-12-10
forum: General Help
---

### Post by pentat0nicc on 2009-12-10
Hello
I have a bit of of weird problem with my desktop. its a old Dell Dimension 5150.
I have 2 SATA drives, (not set up in a raid, just 2 drives plugged in) i have my windows partition (Win7 and XP (for games)) on the first and data etc on the 2nd.
When they are both plugged into the motherboard everything is fine in windows, all works.
When i tried to install or use the live CD, i get the first menu, install ubuntu etc, then i get a flashing cursor for around 10 mins, then maybe i get the select language option etc, and it just hangs there forever. the live CD and my USB stick work fine on my netbook and laptop
After some investigation, i nailed it down to the 2nd SATA drive, i unplugged it and can use the live CD and install ubuntu fine, and boot back into XP and WIN7.
if i plug the drive back in, we are back to the flashing cursor and the drive just ticking over.
oddly, if i disable the drive in the BIOS it does the same thing, i need to unplug it to make it boot into ubuntu.
Windows works fine with it plugged in. i have run a chkdsk /f on 2nd drive.

Never tried to install Linux on this particular machine before, tried it with 8, 9.4 and 9.10

Any help please.........

---

### Post by pricetech on 2009-12-10
Run the Dell Hard Drive Diagnostic and see what you get.

---

### Post by oldfred on 2009-12-10
You mentioned raid. Were these drives ever in a raid configuration. New grub/Karmic find old settings and have issues.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

### Post by pentat0nicc on 2009-12-11
Hi 
the Dell diagnostic CD i have does not work, claims that my system is not support...not sure why that is, maybe been formatted, new hard drive etc....

I did mention RAID but the drives have not been set up in a previous RAID, ever. I have installed GParted, and ran the dmraid commands, but all i get back in "no raid disks with names SDA*, i tired all the partitions.

any more help would be great thanks

---

### Post by pentat0nicc on 2009-12-11
the second drive is a western digital drive BTW if that is of any use........

---

### Post by ST3ALTHPSYCH0 on 2009-12-11
I have heard of some reliability issues with WD drives. It might be an indicator that the drive is getting ready to fail. D/l and run WD's drive diagnostic software.

---

### Post by pricetech on 2009-12-11
> **pentat0nicc said:**
> Hi 
the Dell diagnostic CD i have does not work, claims that my system is not support...not sure why that is, maybe been formatted, new hard drive etc....



Doesn't your Dimension have a boot menu option for Hard Drive Diagnostic ??  Press (tap) F12 while the computer is posting to get the menu.

---

### Post by pentat0nicc on 2009-12-11
> **pricetech said:**
> Doesn't your Dimension have a boot menu option for Hard Drive Diagnostic ??  Press (tap) F12 while the computer is posting to get the menu.


ahh ha! thanks for the tip.
I get an error return code 7, and reason code h25bx1jrqfy

seems not to be a raid error, or 2 drive problem, the the live CD and installation boots as long as this drive it not connected.

but windows is fine.....why not Ubuntu? its not booting from it, just a secondary drive

Thanks
Chris

---

### Post by pricetech on 2009-12-11
Good luck getting this information from Dell Support, but Return Code 7 means that too many bad sectors have accumulated on the drive.  SMART would catch that but SMART is turned off by default in Dell's BIOS.  I like to think they do that on purpose, but that's just me.

Whichever drive failed is bad.  Hopefully you don't have any data that's not backed up elsewhere.

Once that's replaced things should start working normally.

---

### Post by pentat0nicc on 2009-12-11
> **pricetech said:**
> Good luck getting this information from Dell Support, but Return Code 7 means that too many bad sectors have accumulated on the drive.  SMART would catch that but SMART is turned off by default in Dell's BIOS.  I like to think they do that on purpose, but that's just me.

Whichever drive failed is bad.  Hopefully you don't have any data that's not backed up elsewhere.

Once that's replaced things should start working normally.

thanks for this info, very helpful. since i can still use the drive in windows, i have got all the data i need from it....
do you know why windows lets me boot/use it and Ubuntu wont?  i am not disputing that the drive in broken, or at least on its way to be being broken.......

---

### Post by pricetech on 2009-12-11
No I can't, but I've seen it before.  Computers that get replaced with brand new ones come back to me to be refreshed and the hard drive fails either while wiping the drive or while installing the OS.  I suspect winders is just using what the drive controller gives it and not complaining.  Once the drive is wiped though the installer finds a problem and installation stops.

---

### Post by pricetech on 2009-12-11
P.S.  Seagate seems to be my most problematic drive right now.  It was Western Digital, but I haven't had one of them fail in quite a while.

Not throwing off on either company.  Just speaking my experience.

---

### Post by pentat0nicc on 2009-12-16
New drive ordered, should be here any day, many thanks.........

---

### Post by pricetech on 2009-12-17
You are quite welcome.  Best of luck once the new drive arrives.

---

