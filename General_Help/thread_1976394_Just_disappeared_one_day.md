---
title: "Just disappeared one day"
date: 2012-05-08
forum: General Help
---

### Post by maverick75 on 2012-05-08
Hello guys, new to the linux scene.

I got ubuntu 10.10 installed a while back on my computer(tried the new ones but liked maverick the best)

it was running fine for two weeks then one day I boot it up and it gives me something that said "NTFS partition not recognized" or something along those lines cant remember it clealy.


So I shut it off and try again, then it gave me a grub 2 error, I put in the live CD and ran the master boot fix.


After that the computer booted up fine. But just into WinXP, it wont give me the option to choose between OS anymore.

Also now I cant see the Ubuntu partitions in windows anymore, they just show up as "unknown partitions"

I tried searching before posting and found nothing here or on google.

any help is appreciated, thanks!

if I wanted to reinstall do i just delete the partitions and install again? or if there's a fix that would be awesome since I got a couple of CD iso files stored on there that i would love to keep.

---

### Post by Enigmapond on 2012-05-08
Well if I were you...I would use the LiveCD to access the files you want to keep...move them off and then do a fresh install of either 10.04 or 12.04. 10.10 is no longer supported. So rather than installing something that's outdated, install one of the LTS's. 10.04 has another year of support...12.04 has 5 years.

---

### Post by codingman on 2012-05-08
I can see why your username is what it is. It doesn't give you any options on boot at all? Had you been playing in root [-X ?

---

### Post by Baldrick_NZ on 2012-05-08
> **Enigmapond said:**
> Well if I were you...I would use the LiveCD to access the files you want to keep...move them off and then do a fresh install of either 10.04 or 12.04. 10.10 is no longer supported. So rather than installing something that's outdated, install one of the LTS's. 10.04 has another year of support...12.04 has 5 years.

+1. Best to use either 10.04 or 12.04 LTS versions at this point of time. There's no point in using 10.10 now as it's no longer supported, meaning no security or essential updates are provided.

---

### Post by maverick75 on 2012-05-08
How do i mount the partition to copy the files?

in WinXP it shows up as an "unknown partition" and on ubuntu live disc it only shows the windows part of the drive.

> **codingman said:**
> I can see why your username is what it is. It doesn't give you any options on boot at all? Had you been playing in root [-X ?

Actually that's my screen name because I own a 1975 Ford Maverick. I've been using that screen name ever since 2005 on about 40 forums.

I didn't mess with the boot at all, it just worked one day then turned it on the next and it gave me that error. I don't even know how to mess around with the boot lol

It gives me no options it just boots up into WinXP, I didn't like Win7 so I installed Winxp as the dual boot option because there's some programs that I have that require windows and I didn't want to run virtual.

XP was installed on a fresh drive, then 10.10 was installed as a second operating system. I let it update always. Worked perfectly for 2 weeks. Then the last time I used it all I did was browse the internet and I shut it down correctly. Then the next day it went SNAFU.

wouldn't boot into anything, so i went online from my phone and i found some info on this:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
(I used option 2)


After that it booted up into windows but it doesn't give me a choice it just automatically boots into windows.

oh yeah it also gave me a paste bin after the boot repair, I attached it. i have no clue what a paste bin is so i'm hoping you guys do.

---

### Post by maverick75 on 2012-05-11
I guess even the experts are stumped!


should I try this?

[http://www.ehow.com/how_6522043_recover-lost-linux-partition.html](http://www.ehow.com/how_6522043_recover-lost-linux-partition.html)

---

### Post by birdzhavefangs on 2012-05-11
Just throwing this out there, but having my Ubuntu boot disappearing was one of the first signs of my failing harddrive (my windows partition started having major problems too very shortly thereafter). 

I haven't had any experience with doing exactly what was done in your link, but I did something similar to recover my files.  

I used an 8 gig flash drive with the 'ubuntu trial' on it.  A bonus of using a flash drive is it will let you "install" programs (they disappear if you turn it off through.. there might be an option to prevent that, but I never figured it out).

Also, Windows is very grumpy about doing dual booting- I'm surprised it didn't complain about an OS being installed after it- usually you have to do the partitioning and install of Ubuntu before you put Windows on (and the Ubuntu partition should remain hidden to Windows).

---

### Post by maverick75 on 2012-05-11
I installed Ubuntu AFTER windows, I heard all the horror stories about installing it before.
The hard drive  was purchased from Newegg back in February, it still under warranty(3year) so if it goes I'll just get a replacement. It was a new unit not a refurbished.

Like I said it worked perfectly for 2 weeks then out of nowhere I had the issue,
I'm switching over to linux mint now. They have huge tumblr support following. Unlike 10.10 which has virtually none now and I don't like the newer versions of ubuntu at all.

---

### Post by Miykel on 2012-05-11
G'Day, Sounds like a major drama, if you have files you want to save in the ubuntu partition you could download one of the recent distro's, 12.04 or 12.10, burn a disc then boot into it, go to "try ubuntu" option, that will run ubuntu off the disc without installation and should allow you to access the files and transfer them to xp, then boot into xp, install easeuse partition manager, it will see all the partitions on your drive, get the home (free) version, wipe the drive where ubuntu is installed and leave it as "unallocated" then reinstall whatever distro you want, wiping the partition will clean it up, makes for a better install, and, if you have the option with the distro choose the  "ext4 with journaling"  format.
  Hope this helps
 Regards Miykel 

[http://www.partition-tool.com/download.htm](http://www.partition-tool.com/download.htm)

---

### Post by maverick75 on 2012-05-11
> **birdzhavefangs said:**
> 

I used an 8 gig flash drive with the 'ubuntu trial' on it.  A bonus of using a flash drive is it will let you "install" programs (they disappear if you turn it off through.. there might be an option to prevent that, but I never figured it out).



if you look up a couple of post up I mention where I have tried this already, ubuntu just wont show the linux side of the partition. I tried using the live CD.

even ubuntu shows it as "unknown" :D

[[IMG]http://img402.imageshack.us/img402/923/screenshotxzr.png[/IMG]]("http://imageshack.us/photo/my-images/402/screenshotxzr.png/")

---

### Post by wilee-nilee on 2012-05-11
Down load the bootscript, extract it to your desktop and run this command and post the results.txt.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)     

```
sudo bash ~/Desktop/bootinfoscript
```This script was also on the boot-repair app, but we need a fresh copy of where you're at now though.

Kind of hard to exactly tell where you're at now, so if you can definitively tell us it would help.

---

