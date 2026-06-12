---
title: "TRIM and SSD Support"
date: 2010-10-14
forum: General Help
---

### Post by Andy06 on 2010-10-14
Read through a couple of TRIM threads from before 10.10 was released and also this little bit over at omgubuntu from a poster:

> Here's what (I think) I know:

    *

      The kernel has TRIM support as of 2.6.33 (Maverick is 2.6.35).
    *

      EXT4 has TRIM support but only when journaling is turned off.
    *

      The way TRIM works in the kernel is very basic and quite slow. Disks following the specs can accept multiple ranges but the kernel currently can only do one range at a time. This comes from something I read perhaps a month ago. I wish I had the source as this might not be true or might no longer apply.

Journalling is what kills it for me. Data corruption is a PITA.

However the newer versions of hdparm (v9.25 - Maverick is at v9.27) come with a script called wiper.sh which performs a quick analysis of a drive and then trims all the empty space. Rather than lose features, I find it much easier to cron wiper.sh to run once a week (or once a day/month/whatever). SSD degradation for an OS drive doesn't happen that fast unless you're constantly tearing things up. You don't need realtime TRIMming.

There is also a GUI frontend called DiskTRIM which doesn't appear to be in the repos. Less experienced users might find this easier to use than setting up cron jobs.

There are PPAs for hdparm and disktrim and all can be run on Lucid (and further back) without need for 2.6.33+ kernels.

My question is if TRIM is now completely and optimally (as in, quite well) supported in 10.10? Should I wait for BTRFS? What are the effects of journalling? What will I lose if I go with non-journalled? Thanks

---

### Post by Techrocket9 on 2010-10-14
Well, I can attempt to answer the last part.

Journaling keeps track of read and write operations. This is good because in the event of a sudden system failure (power outage, kernel panic, etc), the system knows which operations were currently going on by looking at the journal and has a chance to try and complete them. Without journaling, the system has to go through the entire HD and look for broken files to fix whenever there is some sort of failure. And even then it has less of a chance of recovering them than if it knew exactly what was going on in the first place.

Journaling is a very standard feature. NTFS, HFS+, and EXT3 and 4 all support it.

If you've ever used a Microsoft OS on FAT32, you know how much of a pain running without Journaling is. Every BSOD=35 min disk scan before being able to use the computer again. :cry:

---

### Post by dcstar on 2010-10-14
> **Andy06 said:**
> Read through a couple of TRIM threads from before 10.10 was released and also this little bit over at omgubuntu from a poster:

Here's what (I think) I know:
.........
      EXT4 has TRIM support but only when journaling is turned off.


Rubbish.

*Some* people say that turning off journaling on  a SSD device is good because it simply reduces the overall quantity of writes to the device, it has nothing to do with TRIM mechanism which is allowing the SSD to know about unused data blocks so it can share the "wear" of writes more evenly over the device and therefore extend its operational life.

Trading off the ongoing operational benefits of journaling for the possibility of extending the life of a piece of hardware that may well be chucked out long before it does die is a dubious choice at best.

---

### Post by a-user on 2010-10-14
> **Andy06 said:**
> 
      EXT4 has TRIM support but only when journaling is turned off.
    
who did you tell this wrong stuff?
 that's simply not true. to have trim working with extX you need to add "discard" as mount option e.g. in your fstab.

it works without any problems with ext4 with and without journaling. i even made some test myself to verify trim works.

if you are already adding an option in fstab i recommend adding also "noatime" to improve lifetime and performance a bit.

edit: btw. most modern ssds also have garbage collection. this means they do not need trim support to "trim". it's done automatically during idle times. ofcourse os trim support makes it more effective.

---

### Post by Andy06 on 2010-10-14
> If you've ever used a Microsoft OS on FAT32, you know how much of a pain running without Journaling is. Every BSOD=35 min disk scan before being able to use the computer again.

Isn't that the case on NTFS too? If Vista shuts down unexpectedly due to power failure, it does a full 1 hour disk check (which can be skipped of course). Ubuntu's "disk check" is much faster. So does NTFS have journalling enabled?

> that's simply not true. to have trim working with extX you need to add "discard" as mount option e.g. in your fstab.

it works without any problems with ext4 with and without journaling. i even made some test myself to verify trim works.

if you are already adding an option in fstab i recommend adding also "noatime" to improve lifetime and performance a bit.

Wait, so I need to manually edit something? On 10.10, isn't it enough to just replace the drive and install as you would on an HDD?

---

### Post by a-user on 2010-10-14
so many wrong infos in this thread ;)

1. ntfs has journaling too BUT a somehow simpler one. that ntfs is one of the worst modern filesystems should not be the topic of this thread. anyhow it has journaling and it works.

2. as far as i know you must add the "discard" option. i know this for sure that it was needed before 10.10 (if you used a kernel with trim support). i am not sure if in the actual current release there has been add to detect it automatically.
**i did not tested if trim works without the discard option. but with it does 100%.**

trim has nothing to do with journaling. there are no restriction from ext-filesystem using journaling on trim support.

p.s. correct alignment of ssd partitions does the installer at least since lucid.

---

### Post by zaphod777 on 2010-10-14
here is some info on wiper.sh
[http://ubuntuforums.org/showthread.php?t=1532733&page=1](http://ubuntuforums.org/showthread.php?t=1532733&page=1)

But does it matter if the drive is mounted when it runs?

So if I understand correctly I should have all my bases covered if 1. I have 10.10 and "discard" option enabled in my fstab file
2. The SSD supports trim and has garbage collection.
3. Run wiper.sh once a week using a cron job.

Am I missing anything?

---

### Post by a-user on 2010-10-14
1. yes. that's all you need to do.
2. garbage collection is something you do not need to think about. it works automatically despite the operating system you use.
3. why you want to do this? i even do not know what it really does. it sounds quite useless and risky to me. the system will trim unused blocks automatically if you activated trim (discard) and if your ssd has garbage collection that it does it also during idle times without the help of the system.

hence brief: only put "discard" as mount option to your extX partition on a ssd drive (optionally also add also "noatime", what i recomend).

that's all.

---

### Post by zaphod777 on 2010-10-14
Any recommendations on SSD drives? I have been looking around and it looks like the drives get better performance the larger they are. But they get expensive pretty fast ideally I don't want to spend more than $200.

---

### Post by a-user on 2010-10-14
i searched a bit about wiper.sh related to ssds and it seems that this script was made to use it when you do NOT set "discard" as mount option for your ext4 ssd partition.

the reason is that in the early development stages of kernel trim support there was a performance drop using trim. this was because when something got deleted the kernel instantly invoked a trim. so if you deleted many blocks you got many trim commands that could impact performance.

witht his script you could drop the discard option and  trim a whole bunch of blocks at a time which is much more efficient.

but this seems to not be true anymore. when i used 2.6.35 develoment releases with my lucid install i saw trim not getting invoked instantly. it was delayed thus being able to group more than one block for trimming.

hence it seems that this script is obsolete now. just add discard in ext4 mount options and forget about it.

---

### Post by a-user on 2010-10-14
> **zaphod777 said:**
> Any recommendations on SSD drives? I have been looking around and it looks like the drives get better performance the larger they are. But they get expensive pretty fast ideally I don't want to spend more than $200.
their sequential speeds get better the larger they are but this is nothing you should care about. i doubt you will do extensive video processing on your ssd.

during normal usage more or less all current ssd drives the same. the new sandforce controllers are quite interesting and the intel ones are still very god performers.

search for some reviews, there are plenty of them. i have a nova 2 from corsair if i remember right =) its 64GB and i ahve 18GB in use. i think the most i had on it was 22GB. i have only ubuntu on it. it is in my htpc.

---

### Post by Andy06 on 2010-10-14
Re: the discard option, I am looking to switch about 3 dozen systems at once, manual tweaking or enabling of anything is a no go. It needs to either work perfectly out of the box fully supported or we can wait.

I have no problem waiting for BTRFS or 11.04 :)
Is that what you would recommend? Or should I go ahead and do it now?

---

### Post by a-user on 2010-10-18
@Andy06: sorry but i have to lough a bit. having a system wokring out of the box perfectly optimized is not existent! neither with linux nor with any other os or configuration.
this will allways be a rare situation.

i understand that you are administrator, right? this is you job: go on and insert this little option in fstab. you should know that there are tools to distribute such things among many computers in the network.

and btw. you should not wait for btrfs, especially not if you intend using it in a company with 3 dozens of computers. you shozuld rely on more stable technology! and as far as i have seen benchmarks btrfs isn't faster than ext4. ext4 is one of the best filesystem today.

---

### Post by zaphod777 on 2010-10-18
> **a-user said:**
> @Andy06: sorry but i have to lough a bit. having a system wokring out of the box perfectly optimized is not existent! neither with linux nor with any other os or configuration.
this will allways be a rare situation.

i understand that you are administrator, right? this is you job: go on and insert this little option in fstab. you should know that there are tools to distribute such things among many computers in the network.

and btw. you should not wait for btrfs, especially not if you intend using it in a company with 3 dozens of computers. you shozuld rely on more stable technology! and as far as i have seen benchmarks btrfs isn't faster than ext4. ext4 is one of the best filesystem today.

I will definitely wait for btrfs to be more stable. What are the Linux tools for managing multiple Linux machines over the network. I have been looking for how to do this. I am used to MS's Group Policy tools.

---

### Post by dcstar on 2010-10-18
> **zaphod777 said:**
> Any recommendations on SSD drives? I have been looking around and it looks like the drives get better performance the larger they are. But they get expensive pretty fast ideally I don't want to spend more than $200.

I currently use an IBM SSD as my boot device and it is lightening fast for loading various OSs (especially Ubuntu) but now I am awaiting delivery of one of these that should have all the start-up speed of a SSD and none of the downsides (and it won't need TRIM support at all):

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd)
[http://www.amazon.com/Seagate-Momentus-7200RPM-Hybrid-ST95005620AS-Bare/dp/B003NSBF32](http://www.amazon.com/Seagate-Momentus-7200RPM-Hybrid-ST95005620AS-Bare/dp/B003NSBF32)

---

### Post by zaphod777 on 2010-10-18
> **dcstar said:**
> I currently use an IBM SSD as my boot device and it is lightening fast for loading various OSs (especially Ubuntu) but now I am awaiting delivery of one of these that should have all the start-up speed of a SSD and none of the downsides (and it won't need TRIM support at all):

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd)
[http://www.amazon.com/Seagate-Momentus-7200RPM-Hybrid-ST95005620AS-Bare/dp/B003NSBF32](http://www.amazon.com/Seagate-Momentus-7200RPM-Hybrid-ST95005620AS-Bare/dp/B003NSBF32)

How much did that set you back? Let us know what your startup times are when you get it. Since my boot time is already around 30 seconds or less. Booting up with in seconds of a SSD could mean 3 seconds or 20 seconds. I know how clever those marketing guys can get.

---

### Post by leexgx on 2010-10-18
(You last visited: May 21st, 2008 at 08:40 AM, guess that's when i give up running ubuntu on my server and put win2003 x64 back on)

i thought GC only worked on an NTFS file system, GC works better on some then others (the SF based ones seems to work very well)

if its taking 1hr to do an scan its doing an Full disk check {has 5 stages not 3 that norm happens} (verifying the files and free space) if that happens on its own you may have hard disk failure going to happen (bad blocks) or some other hardware issue that made it do an full disk verify

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd)
is quite an good drive as it does not require or support TRIM as its 4gb cache is only used for Read boosting (uses LBA/Sector based read caching not file so does not care what file system is in use or OS just goes off the Most read parts of the disk and loads them into the cache these drives should be Very good in RAID setups as it can boot read access time speeds a lot more XT drives you get) technically the disk could do 2 I/O operations at the same time if the first read is in the flash cache and second one is an Write (as Writes will always be done to the disk not the flash cache) should be able to if NCQ is enabled (AHCI) but unknown
reboot your pc 2-3 times and the second or 3rd boot will be SSD like booting speeds, once the same sectors or LBA blocks have been read more then 2-3 times it will prefer it and copy that LBA block and remap to the cache on the XT drive
you get the best of both worlds (if they could put 8gb on it that be best case as all of my most used apps and files would fit in that but you could buy 2 of them to do that)


just come back to see how ubuntu has progressed (see if i can brake it in no less then 5-30 mins after install norm the updater gets Broken and does not Fix it self)

---

### Post by zaphod777 on 2010-10-18
> **leexgx said:**
> (You last visited: May 21st, 2008 at 08:40 AM, guess that's when i give up running ubuntu on my server and put win2003 x64 back on)

i thought GC only worked on an NTFS file system, GC works better on some then others (the SF based ones seems to work very well)

if its taking 1hr to do an scan its doing an Full disk check {has 5 stages not 3 that norm happens} (verifying the files and free space) if that happens on its own you may have hard disk failure going to happen (bad blocks) or some other hardware issue that made it do an full disk verify

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd)
is quite an good drive as it does not require or support TRIM as its 4gb cache is only used for Read boosting (uses LBA/Sector based read caching not file so does not care what file system is in use or OS just goes off the Most read parts of the disk and loads them into the cache these drives should be Very good in RAID setups as it can boot read access time speeds a lot more XT drives you get) technically the disk could do 2 I/O operations at the same time if the first read is in the flash cache and second one is an Write (as Writes will always be done to the disk not the flash cache) should be able to if NCQ is enabled (AHCI) but unknown
reboot your pc 2-3 times and the second or 3rd boot will be SSD like booting speeds, once the same sectors or LBA blocks have been read more then 2-3 times it will prefer it and copy that LBA block and remap to the cache on the XT drive
you get the best of both worlds (if they could put 8gb on it that be best case as all of my most used apps and files would fit in that but you could buy 2 of them to do that)


just come back to see how ubuntu has progressed (see if i can brake it in no less then 5-30 mins after install norm the updater gets Broken and does not Fix it self)

Thanks for the info if the cost is right I may have to grab one of these. 

A lot has changed since 2008 of course you can break Ubuntu intentionally pretty fast but under normal use the last 3 releases have been pretty solid. Everyones mileage varies but if it worked right after installation then chances are it will stay working now. 

I'm not sure if it is a case of just knowing more now than I did before but it is harder to bork a normal installation now. 

Anytime something has gone wrong I have been able to find an answer pretty quickly.

---

### Post by Andy06 on 2010-10-18
> @Andy06: sorry but i have to lough a bit. having a system wokring out of the box perfectly optimized is not existent! neither with linux nor with any other os or configuration.
this will allways be a rare situation.

i understand that you are administrator, right? this is you job: go on and insert this little option in fstab. you should know that there are tools to distribute such things among many computers in the network.

and btw. you should not wait for btrfs, especially not if you intend using it in a company with 3 dozens of computers. you shozuld rely on more stable technology! and as far as i have seen benchmarks btrfs isn't faster than ext4. ext4 is one of the best filesystem today. 

Windows 7 and OS X systems work quite beautifully and are rock solid out of the box :)
No disrespect intended, but Ubuntu (and most other common distros) have a tendency to drive themselves into a wall or just break spontaneously. The fabled Linux stability is something I have witnessed most often with large scale managed server installs, not small and medium general desktop usage.

I'm not an administrator (just a power user, never written a line of code), I live in a developing country where schools, NGOs and organisations tend not to be the most cash laden organisations. That is why they are ideal for FOSS, I help out for free so I can't be involved as much as an administrator can.

Windows 7 can handle a SSD without a single configuration change, OS X can't and I just wanted to ask if Ubuntu is at that stage yet. So I guess I will wait another release or so. 

BTW, BTRFS is not the fastest yet but eventually it will be right? As in it is the next gen system?

---

### Post by a-user on 2010-10-19
> **Andy06 said:**
> Windows 7 and OS X systems work quite beautifully and are rock solid out of the box :)
neither less does ubuntu. in my experience even by far better.
> 
No disrespect intended, but Ubuntu (and most other common distros) have a tendency to drive themselves into a wall or just break spontaneously.that's my experience with windows. 
it is even worse. you can rely on windows needing a new installation every half year cause it gets so slow. even worse it was with my win 7. it started to corrupt and delete sys files after 4 weeks. a new installation solved it.... at least till now. (edit: no, it was no maleware, i found out what it was, with mainreason being win7 itself).
> 
 The fabled Linux stability is something I have witnessed most often with large scale managed server installs, not small and medium general desktop usage.you are confusing top edge desktop stuff with linux. the in development desktop gimmicks never claimed to be rock solid stable.

I'm not an administrator (just a power user, never written a line of code), I live in a developing country where schools, NGOs and organisations tend not to be the most cash laden organisations. That is why they are ideal for FOSS, I help out for free so I can't be involved as much as an administrator can.
> 
Windows 7 can handle a SSD without a single configuration changenot true!

you need to configure even more than in ubuntu if you do not install win 7 directly on the ssd but install the ssd later. on the first win7 release there where even alignment problems when installing on the ssd. in fact, you are a bit unlucky you still get bad alignments with win7 installations on ssd.

oh and not to forget, we are talking here about a single option to set. if you consider how unoptimized win7 is, and how you have nearly no options to get it optimized.... it is loughable.

what is worse in different linux distros is grahics related desktop stuff. due to the known driver suport of  the different graphic card manufactor this is years behind windows. but that's a different story.

the day i see a windows system performing nearly as good as my worst linux system i will shut up.

---

### Post by leexgx on 2010-10-19
as long as you install windows 7 (partitioning using windows 7 or vista will normally give correct alignment) and do Not update the chipset/Sata drivers Trim works out of the box (the newer intel matrix From Intel website drivers do support TRIM as long as its not 2 ssds in raid) installing old chipset drivers (like from cd or motherboard website) will disable trim support as they will not pass the TRIM command to the SSD

guess due to me using an SSD any slowness most likely does not show, but any windows7 system i have used works fine no fuss as i deal with lots of user induced fake AV installs all the time (compared to Vista that drove me mad due to things it did that slowed it down when fixing virus or just installing things like printers)

stability is norm an issue with the user or hardware, this affects Linux and windows the the second post back about ubuntu hitting an wall but i do find windows bit better at handling unstable pcs and recovering from it later on like after the system was fixed depending on the issue (its normally the Update manager that brakes on me under ubuntu they really need to add some sort of auto heal to it, as i can Still see that users in here have got issue with it stopping from working)

all there options to there own i guess every linux install i have done has resulted in some permanent bug that would of forced me to goto command line and type an cryptic command to fix it

going to fireup ubuntu 10.10, also guess we should stay on topic (sure this forum has an flame subgroup somewhere) 

so if you want Trim support you need to edit 1 line in fstab to the mount point and put discard (and maybe noatime) seems easy to do

GC is not perfect on all types of ssds and should not work off it only (again i thought it only worked on an NTFS file system)

---

### Post by dcstar on 2010-10-20
> **zaphod777 said:**
> How much did that set you back? Let us know what your startup times are when you get it. Since my boot time is already around 30 seconds or less. Booting up with in seconds of a SSD could mean 3 seconds or 20 seconds. I know how clever those marketing guys can get.

Booting with my current SSD takes just a few seconds from Grub to the login screen, and then just a few seconds more to load my Gnome desktop, Evolution, Firefox and other things after I enter my password. I estimate 3-4 times faster than my "normal" hard drive.

I expect my hybrid device to be similar after about 10 boots - the hybrid device has to learn what files are used the most as it caches them in the SSD for rapid reads.

I also have /tmp mounted on my other drive so my SSD has less writes.

---

### Post by Unibrav on 2010-10-22
> **zaphod777 said:**
> I will definitely wait for btrfs to be more stable. **What are the Linux tools for managing multiple Linux machines over the network. I have been looking for how to do this.** I am used to MS's Group Policy tools.

[Puppet]("http://www.linux.com/learn/tutorials/325201-introduction-to-puppet-streamlined-system-configuration")

---

### Post by Sylslay on 2010-10-22
TRIM enables the SSD to handle garbage collection overhead, that would otherwise significantly slow down future write operations to the involved blocks, in advance.

from 
[http://en.wikipedia.org/wiki/TRIM_%28SSD_command%29](http://en.wikipedia.org/wiki/TRIM_%28SSD_command%29)

;-), from

Where TRIM is not automatically supported by the operating system, there are utilities which can send TRIM commands manually. Usually they list all free blocks as specified by the operating system and then pass this list as a series of TRIM commands to the drive.

THX for "and do Not update the chipset/Sata drivers" Online always better!!!

---

### Post by leexgx on 2010-10-30
you can update them (intel) just make sure its the intel matix drivers from intels web site from july onwards i think Trim is supported on Single disk modes only, i.e. Trim will not be passed to 2 ssds in raid 0 for example but it will send TRIM command if its just an single disk (if the BIOS is to raid mode single disks go into AHCI mode)

the above would only been needed if the HDDs is in raid and you had an single SSD, as simply installing with raid enabled by default would disable TRIM command, but would get enabled after once the up to date intel matix driver is installed

for linux just an matter of editing the fstab (question does it work under soft linux raid ? as it does not under windows yet)

---

### Post by dcstar on 2010-11-12
> **zaphod777 said:**
> How much did that set you back? Let us know what your startup times are when you get it. Since my boot time is already around 30 seconds or less. Booting up with in seconds of a SSD could mean 3 seconds or 20 seconds. I know how clever those marketing guys can get.

Ok, I have now had my Hybrid drive for a few weeks now in my desktop so I can give some information on how it performs. Firstly, it is not as fast as the SSD that it replaced, but it seems faster than a standard hard drive.

I say "seems" because you can't really benchmark these things because they constantly change what is actually cached in the SS cache, so if you repeat a benchmark that ends up putting the same files in the cache it is lightening fast (SSD speeds), but if you use a benchmark that uses random files each time it reports poor performance (like a normal 2.5" drive).

The reality is that the caching of the most used data blocks seems to work, so for "real world" use you **do** get a system that responds faster for disk I/O than a normal spindle drive, but a SSD is way faster for things like booting because the boot files just never make it into a Hybrid drive's cache.

Bottom-line is that a SSD will give you a fast system but at a price, and the better performing SSDs cost more but give you more "bang" than the cheaper ones for your buck.

A hybrid drive will give you a pretty good performance boost and you also have lots of storage and no SSD write performance issues, and they aren't that pricey so these things could well be the most cost-effective way of improving your hardware at this moment.

If you have a laptop/netbook that you want to inexpensively boost real-world performance (that means that it works quicker for you doing real things, not some esoteric benchmark program) then consider replacing the current drive with a Hybrid. It is also worth considering for a desktop system, and keep in mind that Hybrid drives do not need TRIM support.

If you have more money than you know what to do with, you'd get a top-shelf SSD to squeeze the maximum possible performance out of any system that supports TRIM.

My SSD is now in my HP netbook, and Ubuntu boots super fast (as it did when the SSD was in my desktop) and the battery life is longer because the SSD draws less power than the old spindle drive. My desktop with the Hybrid boots Ubuntu 10.04 slower than with the SSD but it is till pretty quick.

---

### Post by rre12 on 2010-11-13
I have been reading this whole thread and no one seems to explicitly show how to add discard and noatime in the fstab file. I checked inside and I had no idea where to put what. Can someone please give newb friendly instructions =)

---

### Post by zaphod777 on 2010-11-13
> **rre12 said:**
> I have been reading this whole thread and no one seems to explicitly show how to add discard and noatime in the fstab file. I checked inside and I had no idea where to put what. Can someone please give newb friendly instructions =)

Put it under options
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=211fb015-689f-484a-9b8f-b480c124334c /               ext4    errors=remount-ro,discard,noatime 0       1
# swap was on /dev/sda5 during installation
UUID=05c3e6d4-b624-48a8-8739-e74a5cce05d4 none            swap    sw              0       0

---

### Post by dcstar on 2010-11-13
One other thing people with **only** a SSD in their Linux system may do is change the scheduler from the default CFQ model.

This is done at the Grub boot and you edit the **grub.cfg** file with the following:
```
sudo gedit /etc/default/grub.cfg
```
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash elevator=noop"
```
Then:
```
sudo update-grub
```
and when you reboot your system will be using the scheduler that gives the best performance with a SSD.

I state **"only"** a SSD because the default CFQ scheduler still works ok with a SSD but very well with spindle drives, but the NOOP scheduler can cause your spindle drives to take a bigger performance hit than the small benefit the SSD gets, so it probably is not worth it in systems with mixed drive types.

---

### Post by rre12 on 2010-11-14
> **zaphod777 said:**
> Put it under options
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=211fb015-689f-484a-9b8f-b480c124334c /               ext4    errors=remount-ro,discard,noatime 0       1
# swap was on /dev/sda5 during installation
UUID=05c3e6d4-b624-48a8-8739-e74a5cce05d4 none            swap    sw              0       0

Is there a command that I can do to show that I am doing it right?

---

### Post by zaphod777 on 2010-11-14
> **rre12 said:**
> Is there a command that I can do to show that I am doing it right?

Not as far as I know. Have a livecd handy in case it won't boot.

---

### Post by dcstar on 2010-11-15
> **rre12 said:**
> Is there a command that I can do to show that I am doing it right?

```
mount
```

---

### Post by a-user on 2010-11-15
@[dcstar]("http://ubuntuforums.org/member.php?u=7532"):
don't use noop as schedular for ssds. test it yourself it is not faster than cfq.
instead you deadline. it is the only one that gives you a performance increase over cfq.

---

### Post by lightrush on 2010-11-15
> **rre12 said:**
> Is there a command that I can do to show that I am doing it right?

There is. It isn't exactly a command but rather several. Look here: [http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking](http://lightrush.ndoytchev.com/random-1/checkiftrimonext4isenabledandworking)

:)

---

### Post by dcstar on 2010-11-16
> **a-user said:**
> @[dcstar]("http://ubuntuforums.org/member.php?u=7532"):
don't use noop as schedular for ssds. test it yourself it is not faster than cfq.
instead you deadline. it is the only one that gives you a performance increase over cfq.

There are numerous posts on the 'net recommending **noop** for SSDs, including a university study proposing special schedulers for SSDs where noop was the next best thing in general performance benchmarks (although deadline can apparently work better in *some* circumstances).

Even the Ubuntu community documentation recommends it:

[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190](http://www.zdnet.com/blog/perlow/geek-sheet-a-tweakers-guide-to-solid-state-drives-ssds-and-linux/9190)

Anyway, some people are saying that newer kernels are detecting non-spindle drives automatically and adjusting to suit:

[http://ca.ubuntuforums.org/showthread.php?t=1601297](http://ca.ubuntuforums.org/showthread.php?t=1601297)

---

### Post by a-user on 2010-11-16
dcstar, i know. the point is, this are all OLD infos. cfq has changed a lot. despite of this deadline works by far better than noop. edit: i forgot where exactly i read this, but somewhere deep in the kernel sources there are comments regarding deadline as the recommended schedular for ssds.

i could make several test at my neighbors from the algorithm engineers ssds, using lucid. there was no performance increase using noop over cfq. in one case it even was slower.

on all but one tests deadline was faster than cfq.

well, nvm... it is easy enough to test it yourself. the simpliest way is using sudo hdparam -t /dev/sda

you know how to change the schedular before each test?

try it yourself and see that deadline works best and that there is no improvment using noop over cfq.

---

### Post by shimoda on 2010-11-16
Please, anyone can help me? :cry:
[http://ubuntuforums.org/showthread.php?t=1621592](http://ubuntuforums.org/showthread.php?t=1621592)

---

### Post by dcstar on 2010-11-17
> **a-user said:**
> d
.........
well, nvm... it is easy enough to test it yourself. the simpliest way is using sudo **hdparam -t **/dev/sda

you know how to change the schedular before each test?

try it yourself and see that deadline works best and that there is no improvment using noop over cfq.

That simple test does not give a comprehensive picture of SSD performance, and it does nothing to address the issues of write block performance. Better to use the Disk Benchmark in the Disk Utility.

And yes, some of the articles are old but some aren't, and you can find detailed studies that cover this issue far more thoroughly than using hdparm.

---

### Post by a-user on 2010-11-17
that simple test was just mentioned for a first impression. as i said before, we here at the university made a study over a week regarding this. well, to be honest it where my "neighbors" from algorithm engineering.

and no, they didn't just used hdparam -t.

well, you don't need to beleive it. it is simple enough to test it yourself with any benchmark you prefer. try it out and report your experience. we are sticking to deadline, especially as elevator. it shortens boot time a little bit compaired to noop and cfq. not much, but it is mesurable.

---

### Post by RJARRRPCGP on 2010-11-18
> **zaphod777 said:**
> the drives get better performance the larger they are. 

That's REAL true with HDDs. (My Barracuda 7200.12 500 GB beats the crap out of my 320!)

But, the read and random write on SSDs, not so much.

---

### Post by Skip Da Shu on 2010-12-05
Any comments on adding the commit=xx parm to fstab for SSD performance?  

I saw commit=120 suggested someplace went back to see if they were talking about SSD performance or just HDD performance in general but couldn't find it again.

---

