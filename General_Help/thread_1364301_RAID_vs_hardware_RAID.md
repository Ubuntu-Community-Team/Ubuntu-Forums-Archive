---
title: "RAID vs hardware RAID"
date: 2009-12-25
forum: General Help
---

### Post by blueshiftoverwatch on 2009-12-25
My [MSI 790FX-GD70]("http://us.msi.com/index.php?func=proddesc&maincat_no=1&cat2_no=&cat3_no=&prod_no=1740") motherboard's  manual says that SATA ports 1-6 support "RAID" but SATA ports 7-8 ones support "Hardware RAID".

When I looked up the specific type of RAID ports 7-8 support it said "*- SATA II 7~8 support RAID 0, 1, or JBOD mode by JMicron® JMB322*".

I'm assuming that hardware RAID is the superior option and that I should go with that.

I checked the specs and it doesn't actually mention having a RAID controller. I'm guessing that means this is what is referred to as "fake RAID" since real RAID controllers are only found on really expensive motherboards. Just out of curiosity, if the "hardware RAID" is fake RAID what are the other RAID supporting SATA ports called?

I'm guessing this means I should use the [JMicron IDE/SATA RAID (with AP)]("http://www.msi.com/index.php?func=downloaddetail&type=driver&maincat_no=1&prod_no=1740") driver.

I plan on triple booting Windows 7 (x86_64), Windows XP (x86), and Linux (x86_64 OpenSUSE) using RAID0. Along with 2 backup/storage partitions which I also plan on RAID0ing. So I want to make sure that I'm doing everything right. Right now my objective is just to get Windows 7 and XP setup. I'll figure out Linux after that's done and the 2 backup/storage partitions after that.

---

### Post by blueshiftoverwatch on 2009-12-25
I just looked at the BIOS and it looks like SATA ports 7-8 are pre-RAIDED. Because it shows both ports as one in the BIOS (ports 1-6 are listed separately but 7-8 are listed as 1) and only shows 1 HD hooked up to them. You have to select SATA ports 7-8 and it brings you to another screen that shows ports 7 and 8 and the devices hooked up to them separately.

Since nobody responded I'm just going to assume right and attempt to go ahead with the installation process.

---

### Post by blueshiftoverwatch on 2009-12-25
When I went to download the JMicron RAID drivers I realized that Windows 7 is not officially supported. So I used the 64 bit Vista driver instead. Before loading the driver the Windows installation only detected 1 hard drive and only had the amount of space that 1 of the 2 I'm using had. After loading the driver it detected two hard drives. They were labled drives  0 and 4. When I went to create a partition to install Windows 7 on I created a partition on drive 0 (it wouldn't allow me to touch drive 4) and also didn't ask me what kind of RAID I wanted to setup. The installation process is copying the files right now. But I don't know if it's going to install on both drives or just drive 0.

Anyone know what's going on? If this were working correctly wouldn't it have asked me how I wanted to setup RAID (it supports RAID0 and 1) during the partitioning phase of the installation?

---

### Post by cariboo on 2009-12-25
You don't need any drivers for Linux, just enable raid in the bios, and you should get a prompt to set up raid before any os's start up.

Have a look at [FakeRaid]("https://help.ubuntu.com/community/FakeRaidHowto") howto.

---

### Post by blueshiftoverwatch on 2009-12-25
Apparently I forgot to enable RAID0 in the BIOS. But I still might have more questions later on.

/facepalm/

---

### Post by Exodist on 2009-12-25
If its anythign like my mobo, You have to turn the SATA from IDE to RAID mode. Which strangley doesnt effect other IDE drives. Then right after the initial boot screen before the hard drives are looked at. You have another screen that you choose the drives you want to be in the RAID array and what type.

If you can go hardware raid without requiring drivers for linux. Go for it. It will offload the disc I/O functions off the CPU. But if you got a really good dual core or a quad core it will not be that noticeable for the average user over software raid. Server PC would be diferent story though.

I have two WD Raptors setup as Stripping (RAID0 Performance) and an additional WD Caviar for holding my files.

---

### Post by blueshiftoverwatch on 2009-12-25
> **Exodist said:**
> If its anythign like my mobo, You have to turn the SATA from IDE to RAID mode.
I just went into the BIOS and changed one setting from "normal" to "RAID0" mode and saved the changes.
> **Exodist said:**
> If you can go hardware raid without requiring drivers for linux. Go for it. It will offload the disc I/O functions off the CPU. But if you got a really good dual core or a quad core it will not be that noticeable for the average user over software raid. Server PC would be diferent story though.
It doesn't seem like I need any drivers at all. Everything sees the RAID0 array. I loaded the driver for Windows 7 just to be safe. But Windows XP requires me to load the RAID driver off of a floppy drive. The only problem besides the fact that I'd have to take my old computer apart and put the drive into this one is that a floppy disk is 1.44MB and my RAID driver is almost 11MB. I'm sure theirs a way to spoof a floppy drive and have it read off a flash drive or CD rom. But if it works this way I'm not going to bother.

What was Microsoft thinking when they released XP and didn't allow for any other option to load RAID/SCSI drivers other than by floppy disk? I know it came out in 2001, but even then floppy disks had pretty much fallen into disuse.
> **Exodist said:**
> I have two WD Raptors setup as Stripping (RAID0 Performance) and an additional WD Caviar for holding my files.
I have two 1TB Samsung Spinpoint F3's. According to a review I read it's the fastest 1TB drive currently on the market in every category except random read and write times.

---

### Post by lukeiamyourfather on 2009-12-25
Whatever performance you think you'll get out of the RAID 0 is not going to happen from that controller on the motherboard. Even if you had a higher end RAID controller with a dedicated processor, RAID 0 is nothing but trouble unless you ***must*** have the extra bandwidth. You'd be much better off just installing the operating systems on the drives without RAID and just use them as regular disks. Cheers!

---

### Post by falconindy on 2009-12-25
> **blueshiftoverwatch said:**
> Windows XP requires me to load the RAID driver off of a floppy drive.
Use nLite to make a slipstream install disc. It'll load the driver at the start of the install process and remove the need for a floppy drive. You can automate the entire install via nLite if you wish.

---

### Post by blueshiftoverwatch on 2009-12-25
> **lukeiamyourfather said:**
> Whatever performance you think you'll get out of the RAID 0 is not going to happen from that controller on the motherboard. Even if you had a higher end RAID controller with a dedicated processor, RAID 0 is nothing but trouble unless you ***must*** have the extra bandwidth. You'd be much better off just installing the operating systems on the drives without RAID and just use them as regular disks. Cheers!
I'm not calling you a liar but that seems highly unlikely. How do you figure?
> **falconindy said:**
> Use nLite to make a slipstream install disc. It'll load the driver at the start of the install process and remove the need for a floppy drive. You can automate the entire install via nLite if you wish.
If I ever need to install RAID/SCSI drivers on an XP system that doesn't recognize my RAID array in the future I'll do that.

---

### Post by lukeiamyourfather on 2009-12-26
> **blueshiftoverwatch said:**
> I'm not calling you a liar but that seems highly unlikely. How do you figure?

On my home system I've got two 150GB Raptors on RAID 0 with the Silicon Image controller on the motherboard. It performs ***barely*** better than a single drive, which is a big disappointment considering its half as reliable as a single drive and makes installing operating systems more difficult.

At work I use a 3ware 9650SE (with dedicated processor for RAID calculations and dedicated buffer memory) with two Barracudas on RAID 0 and it outperforms my setup at home by quite a bit (125 MB/s instead of 85 MB/s like at home for sequential reads). The RAID controller is what makes the difference and people don't always get that at first. The RAID controllers that come on motherboards are mostly a marketing gimmick to get the attention of gamers, but in reality they don't perform. By the time everything goes through the CPU for calculations and system memory for the buffer its not that much faster.

For my home system I'm either going to use the two disks independent for Windows and Ubuntu next time I have to reinstall, or buy a better RAID controller because it was a waste of time to set it up as RAID 0 with the crappy motherboard controller. My point is the performance you think you'll get from a RAID 0 using the cheap motherboard RAID chipset isn't going to be worth the trouble and compromised reliability. Do it if you want but you'll probably come to the same conclusion as I already did. Cheers!

---

### Post by blueshiftoverwatch on 2009-12-26
> **lukeiamyourfather said:**
> The RAID controllers that come on motherboards are mostly a marketing gimmick to get the attention of gamers, but in reality they don't perform. By the time everything goes through the CPU for calculations and system memory for the buffer its not that much faster.
My computer seems noticeably faster now that I'm using RAID0. But it could very well be the placebo effect. I forgot to time how long applications took to open on my old HD before RAIDing it with the new one. 

If nothing else, I wanted to create a 1.5TB partition to keep some stuff on instead of having to manually separate my files out over two 750GB partitions on two separate drives. So the RAID does simplify things by having it show us as one 2TB (1.8TB in reality) HD's instead of 2 1TB (933GB in reality) hard drives.

As far as reliability, I've been using computers since 1997 and I've only ever encountered 1 bad HD. And that was due to it coming that way (bad sectors, not even a full crash) because the computer was bought refurbished. So either HD failure isn't nearly as common as it's made out to be or I've been very lucky and I'm way overdue. It's not like millions of dollars worth of stock exchanges will be lost if I have to reload my OS.

What kind of RAID controllers would you recommend for a home user? Meaning something that's pretty good, but nothing crazy.

---

### Post by falconindy on 2009-12-26
> **blueshiftoverwatch said:**
> What kind of RAID controllers would you recommend for a home user? Meaning something that's pretty good, but nothing crazy.
A cheap RAID controller will bring you nothing but pain and data loss. Don't go down that road. Plan to spend at least $200-300 on the controller alone if you want to be safe. In general, you don't need RAID as a home user.

---

### Post by blueshiftoverwatch on 2009-12-26
> **falconindy said:**
> A cheap RAID controller will bring you nothing but pain and data loss. Don't go down that road. Plan to spend at least $200-300 on the controller alone if you want to be safe. In general, you don't need RAID as a home user.
For that price, I sure don't. Maybe at some point in the future if I have tons of disposable income.

---

### Post by lukeiamyourfather on 2009-12-26
If you're using RAID 0 just to get a larger partition out of two drives, there are better ways. Use symbolic links in one location that point to directories on each disk, or use spanning instead of striping so if you lose one disk you don't lose everything (I think LVM can do this, but I haven't tried before). Cheers!

---

### Post by falconindy on 2009-12-26
> **lukeiamyourfather said:**
> If you're using RAID 0 just to get a larger partition out of two drives, there are better ways. Use symbolic links in one location that point to directories on each disk, or use spanning instead of striping so if you lose one disk you don't lose everything (I think LVM can do this, but I haven't tried before). Cheers!
RAID 0 is a stripe, not a span (which isn't really RAID at all). The resultant size of a true RAID array will **always** be less than the sum of the associated individual drives.

For a number of drives (n) all of size (m):
RAID 0 = n * (m/2)
RAID 1 = n * (m/2)
RAID 5 = (n - 1) * m
RAID 6 = (n - 2) * m

---

### Post by lukeiamyourfather on 2009-12-26
> **falconindy said:**
> RAID 0 is a stripe, not a span (which isn't really RAID at all). The resultant size of a true RAID array will **always** be less than the sum of the associated individual drives.

For a number of drives (n) all of size (m):
RAID 0 = n * (m/2)
RAID 1 = n * (m/2)
RAID 5 = (n - 1) * m
RAID 6 = (n - 2) * m

I'm aware of what RAID is and what it does. Which is exactly why I suggested using disk spanning (***which is of course not RAID***) if the goal is to get a larger single partition for the end user to store data.

---

### Post by falconindy on 2009-12-26
Sorry, I must have misread the part where you said: "If you're using RAID 0 just to get a larger partition out of two drives..."

---

### Post by CharlesA on 2009-12-26
> **falconindy said:**
> A cheap RAID controller will bring you nothing but pain and data loss. Don't go down that road. Plan to spend at least $200-300 on the controller alone if you want to be safe. In general, you don't need RAID as a home user.

I'm quite happy with the RAID controller I got for close to $200. It's a cheaper card, which doesn't have a onboard processor or memory.

---

### Post by blueshiftoverwatch on 2009-12-26
Well even if I don't get any performance increase (which I haven't verified), I'm still doubling my bandwidth.

---

### Post by lukeiamyourfather on 2009-12-26
> **blueshiftoverwatch said:**
> Well even if I don't get any performance increase (which I haven't verified), I'm still doubling my bandwidth.

Not with that RAID controller, which is what several users have been trying to share in this thread. :rolleyes:

---

### Post by blueshiftoverwatch on 2009-12-26
> **lukeiamyourfather said:**
> Not with that RAID controller, which is what several users have been trying to share in this thread. :rolleyes:
No, you contradicted yourself here when you said that even with fake RAID0 I'd still benefit from the extra bandwidth.
> **lukeiamyourfather said:**
> RAID 0 is nothing but trouble unless you ***must*** have the extra bandwidth.

---

### Post by lukeiamyourfather on 2009-12-26
> **blueshiftoverwatch said:**
> No, you contradicted yourself here when you said that even with fake RAID0 I'd still benefit from the extra bandwidth.

You didn't quote all of what I posted. That's under the assumption of using a higher end RAID card, which is the sentence right before that.

[QUOTE=lukeiamyourfather]Even if you had a higher end RAID controller with a dedicated processor, RAID 0 is nothing but trouble unless you must have the extra bandwidth.[/QUOTE]

In this case its a cheap motherboard RAID. I feel like this is taking two steps forward and three steps back. Do whatever you want with your disks if you don't care what others have to say.

---

### Post by blueshiftoverwatch on 2009-12-26
> **lukeiamyourfather said:**
> In this case its a cheap motherboard RAID. I feel like this is taking two steps forward and three steps back. Do whatever you want with your disks if you don't care what others have to say.
I never said that I don't care what others had to say. I started this thread because I had questions and people attempted to answer them. Instead of taking people's answers at face value I probed a little deeper and asked more questions about why something is a certain way. Because I want to learn and that's the only way to learn. After hearing what people had to say I've decided that for various reasons I've listed and ones I haven't I'm going to keep my current fake RAID0 setup, that's it. Your the one that's being rude.

---

### Post by lukeiamyourfather on 2009-12-26
> **blueshiftoverwatch said:**
> I never said that I don't care what others had to say. I started this thread because I had questions and people attempted to answer them. Instead of taking people's answers at face value I probed a little deeper and asked more questions about why something is a certain way. Because I want to learn and that's the only way to learn. After hearing what people had to say I've decided that for various reasons I've listed and ones I haven't I'm going to keep my current fake RAID0 setup, that's it. Your the one that's being rude.

:popcorn:

---

### Post by cascade9 on 2009-12-27
> **blueshiftoverwatch said:**
> Well even if I don't get any performance increase (which I haven't verified), I'm still doubling my bandwidth.

If you've doubled your bandwidth, you should get something.....unless its got major issues. 

I am not quite a negative as other people inthis thread are about motherboard raid. Some of them are not bad. But the JMicron JMB322 controller is flaky, at best. As to how much of this is due to drivers, and how much better the drivers are on linux compared to windows, is debatable. But check these few links- 

[http://www.hardocp.com/article/2009/05/06/msi_eclipse_sli_x58_motherboard/3](http://www.hardocp.com/article/2009/05/06/msi_eclipse_sli_x58_motherboard/3)
JMicron JMB322 in RAID mode _slower_ than a single drive!

[http://benchmarkreviews.com/index.php?option=com_content&task=view&id=270&Itemid=38&limit=1&limitstart=2](http://benchmarkreviews.com/index.php?option=com_content&task=view&id=270&Itemid=38&limit=1&limitstart=2)
Major issues with drivers are apparent. 

> JMicron JMB322 had only a 16Kb cache! To put things into perspective both the Indilinx Controller, and Intel Controller sport 256Kb of cache (16 times the cache!).

[http://www.ssdflashdrivereviews.com/flash-drive-article/JMicron_JMB322_Performance_Issues.php](http://www.ssdflashdrivereviews.com/flash-drive-article/JMicron_JMB322_Performance_Issues.php)
Awful cache levels. 

You would be better off with a cheap PCI-E raid card, or even a normal PCI-E SATA card and fakeraid.

---

