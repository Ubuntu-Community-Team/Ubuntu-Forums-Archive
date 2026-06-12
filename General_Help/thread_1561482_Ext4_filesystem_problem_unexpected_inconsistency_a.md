---
title: "Ext4 filesystem problem: unexpected inconsistency and corrupted download"
date: 2010-08-26
forum: General Help
---

### Post by sberla54 on 2010-08-26
Good afternoon everybody,
i've just registered to the forum because i've a weird problem with Ubuntu 10.04 and the Ext4 filesystem.

I've already discussed it on the italian forum but nobody has been able to help me: [http://forum.ubuntu-it.org/index.php/topic,378428.msg2937151.html](http://forum.ubuntu-it.org/index.php/topic,378428.msg2937151.html)

The problem is this: my home and root partitions have started to give me an "unexpected inconsistency" problem sometimes (at random times) and Ubuntu isn't able to mount them. 
I have to manually do filesystem check (fsck) using a live distro to fix them. After that, i reboot to Ubuntu and so it's able to mount them again.
The problem come back randomly, as i've said: one time a week or one time a month...it depends...

Besides this, i'm experiencing a lot of problems of corrupted downloaded files: a lot of distributions' isos that i download come down corrupted (i check them with md5). That happens if i download'em by browser (with or without a download manager like DownThemAll for Firefox) but even by BitTorrent. I have to download them several times before i get one uncorrupted copy.

I'm having this problem also with the files that i download by eMule. They often give me CRC error and can't even be decompressed.

I'd say that it's a problem that affects every large file...i've experienced it with the rar of UrbanTerror too, that is 700 Mb large...

By the way, that's the inconsistency error at the mount moment:
```

UNEXPECTED INCONSISTENCY ; RUN fsck MANUALLY.

```and that's one of the outputs i receive from fsck:
```

Check and repair file system (ext4) on /dev/sda7  00:00:34    ( SUCCESS )
         
calibrate /dev/sda7  00:00:00    ( SUCCESS )
         
path: /dev/sda7
start: 275257344
end: 968943615
size: 693686272 (330.78 GiB)
check file system on /dev/sda7 for errors and (if possible) fix them  00:00:34    ( SUCCESS )
         
e2fsck -f -y -v /dev/sda7
         
Pass 1: Checking inodes, blocks, and sizes
Inode 19177982 has compression flag set on filesystem without compression support. Clear? yes

Error while reading over extent tree in inode 19177982: Corrupt extent header
Clear inode? yes

Inode 19177982, i_blocks is 134875914, should be 0. Fix? yes

Pass 2: Checking directory structure
i_faddr for inode 11534730 (/musica/punk/hardcore.melodico/Fingerbang - Fingerbanging!/Fingerbang - 06 - B.G.D..mp3) is 202309903, should be zero.
Clear? yes

i_file_acl_hi for inode 11534730 (/musica/punk/hardcore.melodico/Fingerbang - Fingerbanging!/Fingerbang - 06 - B.G.D..mp3) is 15, should be zero.
Clear? yes

Extended attribute block for inode 11534730 (/musica/punk/hardcore.melodico/Fingerbang - Fingerbanging!/Fingerbang - 06 - B.G.D..mp3) is invalid (218762754).
Clear? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Block bitmap differences: +78333442 +78333448 +78333450 +78333458 +78333464 +78333466 +78333472 +78333474 +78333482 +78333488 +78333490 +(78333496--78333498) +78333504 +78333506 +78333514 +78333520 +78333522 +78333528 +78333530 +78333536 +78333538 +78333546 +78333552 +78333554 +(78333560--78333562) +78333568 +78333570 +78333578 +78333584 +78333586 +78333592 +78333594 +78333600 +78333602 +78333610 +78333616 +78333618 +(78333624--78333626) +78333632 +78333634 +78333642 +78333648 +78333650 +78333656 +78333658 +78333664 +78333666 +78333674 +78333680 +78333682 +(78333688--78333690) +78333696 +78333698 +78333706 +78333712 +78333714 +78333720 +78333722 +78333728 +78333730 +78333738 +78333744 +78333746 +(78333752--78333754) +78333760 +78333762 +78333770 +78333776 +78333778 +78333784 +78333786 +78333792 +78333794 +78333802 +78333808 +78333810 +78333816 +(78333818--78333819) +78333824 +78333826 +78333834 +78333840 +78333842 +78333848 +(78333850--78333851) +78333856 +78333858 +78333866 +78333872 +78333874 +(78333880--78333882) +78333888 +78333890 +78333898 +78333904 +78333906 +78333912 +78333914 +78333920 +78333922 +78333930 +78333936 +78333938 +(78333944--78333946)
Fix? yes


/dev/sda7: ***** FILE SYSTEM WAS MODIFIED *****

442543 inodes used (2.04%)
1025 non-contiguous files (0.2%)
80 non-contiguous directories (0.0%)
# of inodes with ind/dind/tind blocks: 0/0/0
Extent depth histogram: 439224/403
79325170 blocks used (91.48%)
0 bad blocks
4 large files

403818 regular files
35811 directories
0 character device files
0 block device files
0 fifos
0 links
2903 symbolic links (2903 fast symbolic links)
3 sockets
--------
442534 files
e2fsck 1.41.9 (22-Aug-2009)
grow file system to fill the partition  00:00:00    ( SUCCESS )
         
resize2fs /dev/sda7
         
resize2fs 1.41.9 (22-Aug-2009)
The filesystem is already 86710784 blocks long. Nothing to do!

```After i do this manual fsck it seems that everything come back being ok.
I can't find deleted or disappeared files...

But, the problems always come back.
And when it comes back i see that my systems is really really slow...sometimes applications don't even start....my computer becames pretty hard to use...and so i reboot and i receive the same inconsistency error.

Obviously, i always shutdown my computer well...so it's not a shutdown related problem...it starts when my pc is running, and i keep it on for a lot of days...

I really don't know what it could be.
I've already done an health test to my hard disk, using the Western Digital tool, and it doesn't seem to have physical problems. By the way, it's a quite new hard disk...it has less than one year.

I've used for 5 or 7 years Slackware, with Reiserfs or Ext3 filesystems and i've never experienced nothing like this.
I've always used the same applications, too....
I've even formatted my Ubuntu one time, and reinstalled it, but the problem came back another time...

I've had the same problem with Ubuntu 9.10 and Ext4 too...

Do you have any ideas?
Could it be a problem related to my motherboard? Or maybe to my connection? Even if it seems strange to me...
Or to some other's hardware parts....

I really don't know how to fix this.

I'm thinking about buying a new hard disk and re-format, installing Ubuntu on an Ext3 partition...

I hope you can help me.

Thank you!

---

### Post by dabl on 2010-08-26
I would be worried about hardware -- could be as simple as the data cable being a little loose (you could swap in a different one to check).  But probably it's something more serious -- the hard drive or motherboard controller or something like that.  There's no reason to be suspicious of ext4 bugs at this point in time -- it has been long tested and all serious issues fixed long ago, else it would not be the default filesystem for all modern Linux distributions.

---

### Post by QLee on 2010-08-26
Just chiming in to state I pretty much agree with dabl, that I would also suspect hardware at this point. We'd likely see lots more reports of such corruption if it was a common fault of ext4. Are you currently running slack, using either reiser or ext3, on the same hardware. Even new drives can fail in one year of almost continuous use, also, how old is the rest of the hardware?


Edit: Have you run a memory check overnight? That is, if the system can be down for that long. I suppose a flaky memory location might mask as drive error or perhaps many other things. However, it might be reasonable to verify that the system will run successfully without the OS involved.

---

### Post by sberla54 on 2010-08-26
Thank you guys for your fast answers!

I do am worried about the hardware too. I'm also thinking about buying a brand new computer...

> could be as simple as the data cable being a little loose (you could swap in a different one to check)
Do you mean, the SATA cable? It' quite new, because the hard drive is new...by the way, i can check if it's correctly connected or even try to switch it with a brand new one...

Could it be a problem related to the network? 
Maybe the ethernet cable or even the switch i'm using to split my connection between the main pc and the laptop...
I remember i've had a download problem on my laptop too, once...

What do you think about the possibility of being a problem of the ethernet cable that bring the connection from living room to my room?
It's pretty old...i mean, at least 10 year...but it's pretty short too....if it was his fault it would be a really big problem to substitute it....

> There's no reason to be suspicious of ext4 bugs at this point in time --  it has been long tested and all serious issues fixed long ago, else it  would not be the default filesystem for all modern Linux distributions.
You're right. That's what i also thought the first times i've had these problems...

> Are you currently running slack, using either reiser or ext3, on the same hardware.
No, i don't.
I've quit slackware almost 6 or 7 month ago, when i switched to Ubuntu...

> Even new drives can fail in one year of almost continuous use, also, how old is the rest of the hardware?
But hardware test says that my hard drive is ok...that's strange...even Ubuntu smart monitor says so.

The rest of the hardware is way more old. I don't remember exactly but i think at least 2 o 3 years old...and i keep my computer running 24/7....

Thank you another time guys!

---

### Post by dabl on 2010-08-26
> **sberla54 said:**
> 

Do you mean, the SATA cable? 



Yes. Even if it's new, it can be loose in either the motherboard connector or the drive connector, or have a defect, etc. etc.

> 
Could it be a problem related to the network? 
Maybe the ethernet cable or even the switch i'm using to split my connection between the main pc and the laptop...



What you wrote does not sound like a problem with the networking, or the ethernet cable, or anything like that.  It sounds like some kind of hardware issue -- something that keeps the data from being "written" correctly on the hard drive, or keeps it from being "read" correctly from the hard drive.  But it could be PSU, motherboard (various possible components), even the PSU (low voltage on 12V line could affect drive performance).

---

### Post by sberla54 on 2010-08-28
> Yes. Even if it's new, it can be loose in either the motherboard connector or the drive connector, or have a defect, etc. etc.
Ok...i'll try to change it :)

  > It sounds like some kind of hardware issue -- something that keeps the  data from being "written" correctly on the hard drive, or keeps it from  being "read" correctly from the hard drive.
Understood. You're right.
Actually, the inconsistency and mount problem is crearly not related to the network...maybe the download one, but the mount one seems just related to the hardware...

> But it could be PSU, motherboard (various possible components), even the  PSU (low voltage on 12V line could affect drive performance). 	
Even the PSU?
My PSU is pretty cheap and poor...the low voltage on 12V line you're talking about could be related to a PSU that hasn't enought power and watt?

Thank you guys for your answers :)
Those have been the most interesting i've received...[IMG]http://www.google.it/images/cleardot.gif[/IMG]Visualizza caratteri romani

---

### Post by dcstar on 2010-08-28
Look in the syslog file for any issues.

---

### Post by sberla54 on 2010-09-07
I've looked in it but haven't found nothing strange :(

I've already ordered some new hardware...

---

### Post by andreaplanet on 2010-09-09
1. Run a memtest86+ for all the night. Make at least 2 full pass, will take some hours.

2. Run a full system stress tool, something that stress CPU, HD and GPU. Let's see if you have problems. Try to read & write very big files (just do a copy & paste) and check the md5 of each copy. You could create a batch file that does this automatically.

3. Place your system under a UPS, they are cheap today and will help you with electrical problems on your line. Do this in any case.

4. If it is not a memory problem then it's likely the PSU. Change the PSU.

Do you have random crashes? Or is it only a HD Write problem of (big) files?

You may can check the SATA Cable, it should be free, not damaged, far from electrical items. Change the cable, it's a easy and cheap task. But this is unlikely to be the cause.

Andrea

---

### Post by sberla54 on 2010-09-17
Grazie Andrea :)

> 1. Run a memtest86+ for all the night. Make at least 2 full pass, will take some hours.
Ok, i will!

> 2. Run a full system stress tool, something that stress CPU, HD and GPU. Let's see if you have problems. Try to read & write very big files (just do a copy & paste) and check the md5 of each copy. You could create a batch file that does this automatically.
I've never done this before.
By the way, i've always wanted to...
Could you suggest me a software to do it? I've only found "stress": [http://weather.ou.edu/~apw/projects/stress/](http://weather.ou.edu/~apw/projects/stress/)
Which kind of problems should i notice? 
Could you help me?

> 3. Place your system under a UPS, they are cheap today and will help you with electrical problems on your line. Do this in any case.
I already have an UPS :)


> 4. If it is not a memory problem then it's likely the PSU. Change the PSU.
My PSU it's pretty old, indeed. And it was a cheap one....
I didn't knew an old PSU could cause some serious problems...

> Do you have random crashes? Or is it only a HD Write problem of (big) files?
Nope.
I haven't any random crash.
Just the read/write, fileystem and random block problems i've explained...

> You may can check the SATA Cable, it should be free, not damaged, far from electrical items. Change the cable, it's a easy and cheap task. But this is unlikely to be the cause.
I don't think it's a cable fault, too. 
It sounds too simple and stupid :)

By the way, i've received my new hardware and i'm gonna assembly and start using it as soon as possibile.
I hope i'm gonna have the time to do the stress test on the old, just to understand what was causing the problem.

Thank you for all your tips.
I'll let you know if the problem continues :)

---

### Post by KirbySmith on 2010-09-17
I had a problem of this sort that got worse and worse over a period of two years under Windows.  I eventually noticed the swollen capacitors on the Abit motherboard I was using and realized that they had bought the Chinese capacitors that had (notoriously) been fabricated using stolen, but incomplete, Japanese formulas.  Unfortunately, the time period for getting compensation from Abit for this problem had just expired.  A new MB (asserted by DFI to be made with Japanese caps) solved the problem (at least until the RAID controller overheated, but that's another story).

kirby

---

### Post by andreaplanet on 2010-09-17
A memtest86+ is a must for every new system, especially if you assembled it on your own. On Lucid it's preinstalled at boot. Else download, burn the iso and boot from there. Will take several hours for a complete test. Let it run at least twice overnight.
It will test the RAM and it's configuration (setting too aggressive parameters in the BIOS will lead to a unstable RAM that only under a strong stress will be seen). But since you have only HD problems and no random crashes I think everything will be ok.

Take a big file and make many copies of it. For each copy calculate the MD5SUM and verify it with the original MD5SUM. After for example 10 copies delete all and restart again. You can run this in the background with a very simple script (cp and md5sum commands). 
Why this test? We try to replicate the problem...

A cable fault is stupid and unlikely.. but replacing one is a cheap and simple task.

---

### Post by sberla54 on 2010-11-23
Hi everyone, i post and update just in the eventuality that someone cames here with a similar problem.

At the end, i bought a brand new pc and i've never had the same problem.
So, i think it was not related to Ext4 or to the internet connection.

I think it was an hardware problem on the motherboard, as you suggested.

I'm still using the old hard disks as secondary ones and they never had any problem...so it wasn't their fault neither...

@ andreaplanet
I didn't had the time to do some hardware stress tests, before changing my computer :(
I would had been interesting...
Thank you anyway for your great help!

---

