---
title: "Ubuntu 10.10 Theme Problem?"
date: 2010-11-01
forum: General Help
---

### Post by 8jwong14 on 2010-11-01
Hi.  I recently built a new computer.  I just installed Ubuntu 10.10.  However, my eyes noticed something unappealing all of a sudden.  Right after the install, Ubuntu 10.10, I noticed that the Ambiance theme wasn't displaying properly.  The window had the proper borders but the other stuff are messed up.  Also, the panels were not using the Ambiance theme.  Third, Ubuntu does not use the normal icons that should come with a fresh install HP computer and it was fine.  Is the problem occurring because I built the computer myself?

I've tried changing things like background color in Windows but the windows still look the same except for when I change the window border.  Also, installing new themes only changes the window border.

Please help.  I can't use Ubuntu if it looks this ugly no offence!

---

### Post by garvinrick4 on 2010-11-01
The only way I know is to hit customize and go thru the tabs and select what I want.
Never has been a problem. Never heard of a problem.

---

### Post by coffeecat on 2010-11-01
Yes, there is something definitely wrong with the panels. But, no, building your own computer would not cause this.

It's possible the theme was corrupted on install. Perhaps there was a fault on the installation medium. Try reinstalling the package light-themes. That will cause the system to download the package from the repository and install from that.

---

### Post by MrRichard on 2010-11-01
A similar thing happened to me, except only one of the icons were corrupt, not to the extent of your incident. It turned out that not everything downloaded correctly when I downloaded the Ubuntu .iso . A simple re-download of Ubuntu and reinstalling it solved my problem.

---

### Post by 8jwong14 on 2010-11-01
Thanks for all the replies. As an extra information, Ubuntu seems really slow.  There is also quite some lag.  Logging in and out takes a long time.  So it may be a corrupt install?

---

### Post by coffeecat on 2010-11-01
> **8jwong14 said:**
> So it may be a corrupt install?

This is possible. Did you do all the usual things such as check the md5sum hash on the downloaded ISO and burn at a low speed? More here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also - when you ran the live CD, did the theme show OK in the live session?

---

### Post by Frogs Hair on 2010-11-01
Go to System > Administration > Synaptic Package Manager, use the search to locate light-themes . Right click and mark for reinstallation and select apply. This may help.

---

### Post by 8jwong14 on 2010-11-02
> **coffeecat said:**
> This is possible. Did you do all the usual things such as check the md5sum hash on the downloaded ISO and burn at a low speed? More here:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Also - when you ran the live CD, did the theme show OK in the live session?
Hey.  I'm not sure about the live session.  It doesn't seem to load.  I pressed "Try Ubuntu" but it it would show the button is pressed but nothing opens.  It just freezes forcing a reboot.  I burnt the disk at 1x speed.  From what I remember, the disk worked fine when I installed it on a HP PC.

---

### Post by 8jwong14 on 2010-11-02
> **Frogs Hair said:**
> Go to System > Administration > Synaptic Package Manager, use the search to locate light-themes . Right click and mark for reinstallation and select apply. This may help.
I'll try that after I reinstall Ubuntu.

---

### Post by mastablasta on 2010-11-02
What is your graphics card. it might not be using propper drivers. or this is some kind of low graphics mode.

---

### Post by 8jwong14 on 2010-11-02
> **mastablasta said:**
> What is your graphics card. it might not be using propper drivers. or this is some kind of low graphics mode.

Also, after trying to install Windows 7. when I try to install Ubuntu in its place, there is a message asking about whether something is a gpt partition ttable or not.  When I press yes or no, nothing happens.

Here is the graphics card:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130543](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130543)

I used another one of this card on my HP PC and it worked fine.

---

### Post by coffeecat on 2010-11-02
> **8jwong14 said:**
> Also, after trying to install Windows 7. when I try to install Ubuntu in its place, there is a message asking about whether something is a gpt partition ttable or not.  When I press yes or no, nothing happens.

[GUID Partition Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

That's very interesting. Windows 7, according to that link, will only work on a GPT table on a machine with EFI, not with a conventional BIOS. Linux is happy with either GPT or the commoner (?) MBR partition table.

Does your home-build machine use EFI or BIOS? You said you tried to install Windows7. Did you succeed? How did you partition and format the hard drive? Was it used one from another machine or a brand-new unused one? Did you create a partition table, and how?

---

### Post by srs5694 on 2010-11-02
> **8jwong14 said:**
> Also, after trying to install Windows 7. when I try to install Ubuntu in its place, there is a message asking about whether something is a gpt partition ttable or not.  When I press yes or no, nothing happens.

This almost certainly is not related to the graphics problem, since partitioning is a disk allocation issue, not a graphics issue. That said, this could be an indication of a serious problem. I recommend you open a console and type the following command:

```

sudo fdisk -lu

```

Post the output here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings for legibility. That will tell us what type of partition table you've got, and if there are any problems, it'll be a first step toward identifying them.

---

### Post by 8jwong14 on 2010-11-02
> **coffeecat said:**
> [GUID Partition Table]("http://en.wikipedia.org/wiki/GUID_Partition_Table")

That's very interesting. Windows 7, according to that link, will only work on a GPT table on a machine with EFI, not with a conventional BIOS. Linux is happy with either GPT or the commoner (?) MBR partition table.

Does your home-build machine use EFI or BIOS? You said you tried to install Windows7. Did you succeed? How did you partition and format the hard drive? Was it used one from another machine or a brand-new unused one? Did you create a partition table, and how?
Never mind, I chose another HDD to install Ubuntu on and the issue is gone.  I got confused which of my 2 HDD ahd Windows 7.

---

### Post by 8jwong14 on 2010-11-02
One other thing, Ubuntu seems slow.  Its not unusable slow but there is noticeable lag.  For example, after I lock my computer and log in, it takes about 10 seconds before actually taking me back to the desktop.  Lgoing in also lags.  Once I type in my password, it freezes for 20 seconds or so before logging in.  Even copying an dpasting into terminal lags.

Is my hardware compatible with Ubuntu?
Mobo: EVGA 13-GT-E767-TR
Processor: Intel i7 930
Memory: Patriot Viper II Sector 7 Edition 6GB
PSU: Antec NEO ECO 520C 520W
Storage:2 Western Digital Caviar Green WD20EARS 2TB
Graphics: EVGA 015-P3-N969-LR GeForce 9600 GSO
CD/DVD Drives: 2 ASUS DRW-24B1ST
Extras: Rosewill RCR-IC002 74-in-1 USB 2.0 3.5" Internal Card Reader

---

### Post by wakeupthesun on 2010-11-02
I had this issue on 9.4 wubi before I installed 10.10 with the live disk. I also had the problem occasionally until I logged out. I updated my graphics driver and it seemed to go away.

This is how I updated to the 260.XX.XX Drivers for NVIDIA cards.

Add the correct repo:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```
Update:

```
sudo apt-get update
```
Upgrade:

```
sudo apt-get upgrade
```
Reboot.

---

### Post by 8jwong14 on 2010-11-02
> **wakeupthesun said:**
> I had this issue on 9.4 wubi before I installed 10.10 with the live disk. I also had the problem occasionally until I logged out. I updated my graphics driver and it seemed to go away.

This is how I updated to the 260.XX.XX Drivers for NVIDIA cards.

Add the correct repo:

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
```Update:

```
sudo apt-get update
```Upgrade:

```
sudo apt-get upgrade
```Reboot.
Thanks but it didn't help =(  Doesn't work.  If I cant fix this, I will switch back to Windows.

---

### Post by mastablasta on 2010-11-03
> **8jwong14 said:**
>  
Storage:2 Western Digital Caviar Green WD20EARS 2TB

 
should be quite compatible. this disk however needs to have partitions "aligned" after format i believe. 
 
 
After nvidia driver update what doesn't work? did the update suceed?

---

### Post by coffeecat on 2010-11-03
> **mastablasta said:**
> should be quite compatible. this disk however needs to have partitions "aligned" after format i believe. 

I'm using a couple of the WD Caviar Green 'advanced format' drives in the machine I'm posting from. So long as you don't jumper it for XP-compatibility (that is, leave it unjumpered as per default) and use the version of Gparted in 10.10 for partitioning so that the partitions start at sector 2048, then it should work just fine. Gparted in 10.04 might be OK, it's just that I didn't use that for my WD drives.

---

### Post by 8jwong14 on 2010-11-03
> **mastablasta said:**
> should be quite compatible. this disk however needs to have partitions "aligned" after format i believe. 
 
 
After nvidia driver update what doesn't work? did the update suceed?
Have partition aligned?  How do I do that?

---

### Post by 8jwong14 on 2010-11-03
> **coffeecat said:**
> I'm using a couple of the WD Caviar Green 'advanced format' drives in the machine I'm posting from. So long as you don't jumper it for XP-compatibility (that is, leave it unjumpered as per default) and use the version of Gparted in 10.10 for partitioning so that the partitions start at sector 2048, then it should work just fine. Gparted in 10.04 might be OK, it's just that I didn't use that for my WD drives.
Ok.  But you lost me at jumper and xp compatibility.  I really need to brush up on technical terms.  also, I love the picture of the cat with headphones you used.  It's so cute!

---

### Post by 8jwong14 on 2010-11-03
I did the strangest thing.  For some reason, I decided to unplug my VGA cable and dig up my"lost" hdmi to dvi cable that came with my monitor.  I plugged it in and booted Ubuntu.  To my joy, every looked fine!  I don't know why but even  Ubuntu seems a little faster.  I hope this "fix" is permanent.  I'll report back here in a day on whether or not the issue is solved.

However, Ubuntu is still lagging in a very noticeable manner.  Copying and pasting into terminal, for example, still lags.  Logging in sill lags.  Youtube also lags.  MP3 playback has lag too.  Maybe I shoudl switch to Lucid for a while?  Any ideas why?

---

### Post by srs5694 on 2010-11-04
> **8jwong14 said:**
> Have partition aligned?  How do I do that?

See [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote on the topic a few months ago. It's best to do the alignment *before* creating partitions; otherwise you'll just waste time and risk data loss moving the partitions around after the fact.

The jumper to which coffeecat referred is specific to WD Advanced Format drives; it causes the firmware to change how the drive maps sectors so that a start sector value of 63 actually occurs on sector 64. This properly aligns that partition, which is a quick and *very* dirty way to achieve proper alignment with Windows XP or other OSes (partitioning tools, really) that start the first partition on sector 63 and that create just one big partition on the disk. IMHO, it's best to *not* set this jumper, and instead use modern partitioning software that aligns partitions on 1 MiB boundaries, which will be properly aligned for these drives (and for various other purposes, such as some RAID arrays and SSD devices).

---

### Post by 8jwong14 on 2010-11-04
> **srs5694 said:**
> See [this article]("http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/") I wrote on the topic a few months ago. It's best to do the alignment *before* creating partitions; otherwise you'll just waste time and risk data loss moving the partitions around after the fact.

The jumper to which coffeecat referred is specific to WD Advanced Format drives; it causes the firmware to change how the drive maps sectors so that a start sector value of 63 actually occurs on sector 64. This properly aligns that partition, which is a quick and *very* dirty way to achieve proper alignment with Windows XP or other OSes (partitioning tools, really) that start the first partition on sector 63 and that create just one big partition on the disk. IMHO, it's best to *not* set this jumper, and instead use modern partitioning software that aligns partitions on 1 MiB boundaries, which will be properly aligned for these drives (and for various other purposes, such as some RAID arrays and SSD devices).
Wow...That is a long article so I shall read it latter.  Thanks for the info.  Jsut os you know, I'm using Windows 7 and Ubuntu dual boot.  Do happen to know why Ubuntu 10.10 is so slow on my computer that I built myself, while it runs fast on an HP computer with the same graphics card(I upgraded it) and a WD drive?

---

### Post by Arsic on 2010-11-04
Here's a new angle.

I'm pretty sure it has something to do with gdm startup priory. Something else might be loading before gdm. I had this problem when I was using conky on startup. Ended up having to delay the startup using a script. Though I'm not sure how to lower the priority of gdm so it comes up first.

---

### Post by 8jwong14 on 2010-11-04
> **Arsic said:**
> Here's a new angle.

I'm pretty sure it has something to do with gdm startup priory. Something else might be loading before gdm. I had this problem when I was using conky on startup. Ended up having to delay the startup using a script. Though I'm not sure how to lower the priority of gdm so it comes up first.
Hey.  Are you referring to the slow boot times?  I don't know why but even a fresh install of Ubuntu 10.10 was slow.  If you look at my post somewhere above, you will noticed my specs are pretty decent.  Strangely the same install using the same disk on an older HP computer was perfectly fine and fast.  Maybe the issue is hardware compatibility.  do you know where I can check hardware compatibility with Ubuntu?

---

### Post by airplanesimen on 2010-12-05
what kind of computer-specs do you have? if you cant run ubuntu at LiveCD, you may have to install it using wubi in windows. (a trick: Try installing it from an usb --> [www.ubuntu.com/desktop/get-ubuntu/download](www.ubuntu.com/desktop/get-ubuntu/download), scroll down to "burn a cd or create a USB drive". Choose USB and click "show me how".) Or you can reboot your computer and start the recovery console, then a menu will pop up. Choose "repair packages" (im not really sure what is standing there)follow the instructions. good luck!

---

### Post by 8jwong14 on 2010-12-22
> **airplanesimen said:**
> what kind of computer-specs do you have? if you cant run ubuntu at LiveCD, you may have to install it using wubi in windows. (a trick: Try installing it from an usb --> [www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download"), scroll down to "burn a cd or create a USB drive". Choose USB and click "show me how".) Or you can reboot your computer and start the recovery console, then a menu will pop up. Choose "repair packages" (im not really sure what is standing there)follow the instructions. good luck!
THe thing is...I don't have Windows on my PC anymore.

---

### Post by carolinason on 2010-12-24
theme problem - confirmed here
system hangs - confirmed here

i built my system(specs in signature) too and the iso's sha256sum checked, i verified the burn in k3b and i have the disk check itself before an install.

i think these are for real bugs. 

i'm not sure why a graphics card [driver] would make the theme change to gnome's default minus metacity, which stays as selected in appearance control panel- it looks like debian's current theme, which i think is just gnome. compiz is working fine. sometimes cutting this off fixes issues. i'll have to do that i suppose.

i do think an ide controller bug in the kernel might explain these disk i/o fits i seem to get randomly, expect for the fact i have a specific cd that is very scratched and i can stick that in and cause the hdd led to go off for about half a minute and i really can't do much with the system. you'd think with 4 ht cores you wouldn't have that issue. i can repeat that hdd activity in windows with that disk, but don't experience any other odd waits just in ubuntu.

i have found ubuntu 32 bit more stable than ubuntu 64 bit, that goes for windows 7 as well. however, i must have the ram though to run virtual box, so i am running 64 bit.

---

### Post by zambizzi on 2010-12-24
> **Frogs Hair said:**
> Go to System > Administration > Synaptic Package Manager, use the search to locate light-themes . Right click and mark for reinstallation and select apply. This may help.

This works great, but only for *one* session.  I do this, log out, log back in, and the theme is correct again.  However, when I reboot...all is lost and I have to do the same routine again.

How can I permanently fix this annoying issue w/o creating a new profile or, as some have suggested, REINSTALLING Ubuntu?

Thanks!

---

### Post by Syed75 on 2010-12-24
First of all it depends on your graphics card. If you have a not so good one tough turkey. You could try getting a better graphics card.

---

### Post by johnny.n3xu5 on 2010-12-25
Same problem... sometimes ambiance theme is replaced by default gnome theme on startup.
I have customized the ambiance theme too... so the problem could be this one.
I never tried to leave default ambiance theme and have a look if the problem occurs...
HW : eeepc 900

---

### Post by 8jwong14 on 2010-12-28
I no longer run 10.10.  Im just using 10.04 now since it works fine with graphics.  However since someone else also has this problem, we might as well continue this thread.

---

### Post by 8jwong14 on 2010-12-28
> **zambizzi said:**
> This works great, but only for *one* session.  I do this, log out, log back in, and the theme is correct again.  However, when I reboot...all is lost and I have to do the same routine again.

How can I permanently fix this annoying issue w/o creating a new profile or, as some have suggested, REINSTALLING Ubuntu?

Thanks!
That happened to me too.

---

### Post by 8jwong14 on 2010-12-28
> **carolinason said:**
> theme problem - confirmed here
system hangs - confirmed here

i built my system(specs in signature) too and the iso's sha256sum checked, i verified the burn in k3b and i have the disk check itself before an install.

i think these are for real bugs. 

i'm not sure why a graphics card [driver] would make the theme change to gnome's default minus metacity, which stays as selected in appearance control panel- it looks like debian's current theme, which i think is just gnome. compiz is working fine. sometimes cutting this off fixes issues. i'll have to do that i suppose.

i do think an ide controller bug in the kernel might explain these disk i/o fits i seem to get randomly, expect for the fact i have a specific cd that is very scratched and i can stick that in and cause the hdd led to go off for about half a minute and i really can't do much with the system. you'd think with 4 ht cores you wouldn't have that issue. i can repeat that hdd activity in windows with that disk, but don't experience any other odd waits just in ubuntu.

i have found ubuntu 32 bit more stable than ubuntu 64 bit, that goes for windows 7 as well. however, i must have the ram though to run virtual box, so i am running 64 bit.
MY system is a bit similar:[SIZE=1]
[/SIZE][B][SIZE=1]EVGA 131-GT-E767-TR LGA 1366 Intel X58  | i7-930 (I made the stupid mistake of getting the 930 instead of the 950.) | [/SIZE][SIZE=1]Patriot Viper II Sector 7 Edition 6GB | EVGA 015-P3-N969-LR GeForce 9600 GSO 1536MB 192-bit DDR2 | 2x Western Digital Caviar Green 2 TB | 2 ASUS DRW-24B1ST | 680 W PSU | Ubuntu 10.04 64 bit
[/SIZE][/B]

---

### Post by Strange_Movement on 2011-01-12
Thought I'd just post on here in case anyone ever resolves this.

Occasionally my EEE901 messes up the theme when I first log in to 10.10, and mostly it corrects itself if I just log out and then back in again or restart. I'm using the default Ambiance theme. 

It never happens on my big box Xeon 3520 with 12GB of RAM and 10.04 64 bit and it never happened on my EEE901 with 10.04. Unfortunately I really don't want to revert my EEE901 back to 10.04 because I can't use the WiFi with the standard 10.04 kernel.

If anyone can resolve the (occasional) theme problem I'd be happy to apply any simple fix, I just don't want to do the kind of kludge job I had to do for 10.04.

---

### Post by ttbek on 2011-01-12
I'm also having issues with the theme, sometimes it's just the icons and sometimes it's everything.  Seems to occur about 50% of the time on boot.  Opening display manager will put back the window border and fix the panels, but the stuff in the nautilus window remains incorrect until I reboot.  The theme it displays instead is the same as is shown in the original posters screenshots.  I'm running ubuntu 10.10 on a Lenovo S10-3t, this did not happen for the first month or so, so I kind of suspect it's a new bug (there have been some gnome updates) that has been introduced, has anyone filed a bug report about this?

---

### Post by bwsmith25 on 2011-01-12
I'm having the same problem occasionally when I boot my computer. If I go to the "Appearance" menu, the icons and panel correct themselves, but the Nautilus menu stays screwed up. Sometimes when I reboot the problem goes away, but sometimes I have to reboot more than once to get it fixed. Any help in resolving this matter will be appreciated, because it is quite annoying, and I don't want to have to either revert back to 10.04 or switch to Mint, etc.

---

### Post by mercury80 on 2011-01-15
Same problem here! Sometimes just the panels, and sometimes "the everything". This is on a [ASUS U31F]("http://www.asus.com/product.aspx?P_ID=OV45sT3DY56akobY"). I don't believe this has anything to do with paritions or GPUs. If anyone have a better idea I'm all ears!

Used USB to install.

---

### Post by shadgr on 2011-01-17
I have exactly the same problem with the panel colors (ambiance theme is not showing correctly)... Re-downloaded the ubuntu iso, reformatted the whole disk partition and kept only ubuntu, I did all you mentioned above. And still nothing.. Allthough, when I tried to boot with the live dvd, it worked just fine..
Any other solutions please!

---

### Post by JECHO on 2011-02-18
> **shadgr said:**
> I have exactly the same problem with the panel colors (ambiance theme is not showing correctly)... Re-downloaded the ubuntu iso, reformatted the whole disk partition and kept only ubuntu, I did all you mentioned above. And still nothing.. Allthough, when I tried to boot with the live dvd, it worked just fine..
Any other solutions please!

Same problems here!!

---

### Post by pEscobar on 2011-02-27
Gettin' simmilar error - I have got the default os theme (old windows style) and i can't change it, some icons are missing. 
Running Lenovo w510 i7, installed from usb.

---

### Post by 8jwong14 on 2011-02-28
I no longer have this issue as I'm using Natty 11.04 now.  We should try to keep this thread open for those who have the issue though.  It would also be a good idea to list some computers specs because some hardware may not be compatible.

---

