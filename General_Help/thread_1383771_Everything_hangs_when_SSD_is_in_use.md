---
title: "Everything hangs when SSD is in use"
date: 2010-01-17
forum: General Help
---

### Post by Jarige on 2010-01-17
Edit:
This problem is now solved. I made a howto on solving this problem, which you can see on page 9: [http://ubuntuforums.org/showthread.php?t=1383771&page=9]("http://ubuntuforums.org/showthread.php?t=1383771&page=9")
I would like to hear your reactions to the howto :)

This was the original first post:

I'm having a problem. Every program stops responding, including the gnome panels. Nothing will produce output when my SSD led light is on. This is especially annoying when watching Youtube since its writing and reading the SSD a lot and it will interrupt the film. 
Installing a program from the Ubuntu Software Center makes everything crash so I just have to wait and let it finish installing.
I did make some changes to /etc/fstab though. I added noatime and nodiratime and it speeded up my boot process a lot.

I don't know what to do about it, and I read somewhere that it's a kernel bug. So it might have been fixed already in a newer kernel.

Does anyone have a workaround or does anyone know something about a bug that does this? And whether it will be fixed soon?

---

### Post by Jarige on 2010-01-18
BTW, my swap space is almost never in use. So it can't be that problem. I made Ubuntu disencourage the usage of the swap file.

---

### Post by Jarige on 2010-01-22
BUMP. Damn I hate this bug. I've also noticed that one of the two CPU cores (Intel Atom N270,  1.6GHz) is in use all the time while reading or writing to the SSD. The other one is doing nothing as it seems...

---

### Post by crom.osec on 2010-01-22
I didn't invested yet in a SSD, but from what I've read it seems that SSD are good for reading, not so good for writing.
My suggestion would be to use another drive for writing (especially the temporary files which are created on updates or on flash play).
If you don't want another drive (for example you have a notebook and you want portability) I would recommend to create a memory drive to keep the temporary files (if you have enough memory).

---

### Post by Jarige on 2010-01-23
Ah finaly, a reply, thank you :D
I know SSD's are slow on writing, but it doesn't appear to be writing only. The problem is that every program crashes when the SSD is in use. I do think it should not be like that. If one program uses the SSD (for instance the update-manager, which is reading package info) it should NOT crash Firefox. But this is the case currently :(
I plan on buying a faster SSD when they are cheaper, but I guess that would take some time...

---

### Post by Jarige on 2010-01-23
btw, I've already changed some stuff. /tmp is stored in RAM currently, and so are other files. Firefox's temp files are also in RAM. I only have 512MB, its barely enough, but it works.

---

### Post by Jarige on 2010-01-27
Bump. Doesn't anybody know whats going on here?
I removed Firefox' cache from RAM again, as there was some memory leak (I think) that caused RAM to be full after using the netbook for some hours.
I'm really getting freaked out by the constant interrupts caused by the SSD. Sometimes not even the mouse moves! The SSD should NOT at ALL times do hardware interrupts! Right?
What can I do to fix this?! Its a very serious problem!

---

### Post by happyhamster on 2010-01-27
> **Jarige said:**
> BTW, my swap space is almost never in use. So it can't be that problem. I made Ubuntu disencourage the usage of the swap file.
You lowered the swappiness value? Is the swap partition on the ssd?

> 
/tmp is stored in RAM currently

This could cause trouble because some applications can fill up /tmp rather suddenly. You can watch it using:

watch df

- How did you create the ramdisk (and what's it size)?

> 
If one program uses the SSD (for instance the update-manager, which is reading package info) it should NOT crash Firefox.
Perhaps the infamous OOMkiller in action? Take a look at your memory usage while running update manager. For example, in a terminal:

watch free -m

- then start update-manager.

---

### Post by Jarige on 2010-01-27
I've read about OOMkiller but this isn't the case. When I started update-manager while that other command was running I noticed nothing extraordinary. RAM use went up a little, and after it finished and I closed the menu, it went down again. As it should be.

I think there has been a little miscommunication. When I said crashed I meant stopped responding. Every program does that. Even the mouse won't respond while the SSD is in use. The only program that still seems to respond is the program that's using the SSD. If the SSD is not in use, the programs start responding again. Downloading a file with a high speed will use the SSD a lot, and thus causes the download to stop while writing, then go further while not writing. Very annoyingly. All other programs stop responding while writing the file. But it doesn't only appear on writing. 
While executing update-manager as you said everything went laggy, and I was only able to move the mouse in the short times that the SSD LED was off. So this does happen when writing AND reading!

'swappiness' is 1 atm. Changed that in /etc/rc.local

In /etc/fstab I added the following lines:
```
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0
```

Swap partition is on the SSD... hardly in use.

Thanks for your reply. Do you recommend me to remove those lines from /etc/fstab again? I did have a problem once that the swap space was suddenly half full after the system stopped responding for a minute, but it didn't seem to use the swap after that because the SSD wasn't in use more than normally.

---

### Post by happyhamster on 2010-01-27
> **Jarige said:**
> 
In /etc/fstab I added the following lines:
```
tmpfs /var/log tmpfs defaults 0 0
tmpfs /tmp tmpfs defaults 0 0
tmpfs /var/tmp tmpfs defaults 0 0
```

Swap partition is on the SSD... hardly in use.

Thanks for your reply. Do you recommend me to remove those lines from /etc/fstab again? I did have a problem once that the swap space was suddenly half full after the system stopped responding for a minute, but it didn't seem to use the swap after that because the SSD wasn't in use more than normally.
/var/tmp should not be in RAM, because its contents shouldn't be deleted every reboot (see link below). /var/log might be fine in RAM (you won't have any logs after a crash/lockup of course), but those logs can grow *huge*. I would test with only /tmp mounted in RAM (or without any ramdisk at all).

For an interesting discussion on the matter:
[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/18661)

What is your setup like? In my case / and swap are on an ssd, /home is on a regular drive, and only /tmp is mounted in RAM (8GB).

---

### Post by Jarige on 2010-01-27
I've commented the lines in fstab regarding tmpfs.

My current setup I think is as when I installed Netbook Remix. I've got a netbook with 512MB RAM, 8GB SSD. Both partitions are on the SSD (Swap and / ).
I tried to add elevator=noop to /etc/default/grub to the GRUB_LINUX_COMMAND_LINE_DEFAULT section, but as that is currently suffering some kind of bug I quickly removed that one. Bug report here:
[https://bugs.launchpad.net/linux/+bug/445852]("https://bugs.launchpad.net/linux/+bug/445852")
I replied there that this bug was fixed when removing 'elevator = noop' from /etc/default/grub. I don't know if that bug is related to the problems I've got here, but removing 'elevator = noop' agan did improve performance by a lot.

In short: everything is on the SSD again. I didn't reboot yet after that change. I will do so now.

---

### Post by Jarige on 2010-01-27
Rebooted succesfully. Did notice that it boots a bit longer now. I don't know if the SSD is in use more now. It feels as if its in use more, but I might be fooling myself.

---

### Post by anaconda on 2010-01-27
sounds like you have the older 8.9" 
acer aspire one
with the Really really really slow (and cheap) 8gb SSD disk.

(I have one of those And the same problems too eg. if I try to open nautilus the computer hangs for about 35seconds, and then it opens.. etc.) 

I booted the machine a few times from external USB harddisk, and it was really responsive and "fast" compared to running from SSD.

1,8" hard-disks (preferable) or faster SSD disk are way too expensive for this machine, so..

I am planning to upgrade the RAM to 1-1.5GB And then running the whole OS from RAM. That should solve the problem. except that boot time will be longer, because the whole system needs to be copied to RAM. 
I dont know yet what OS I am going to put in it, but I have previous experience from DamnSmallLinux and puppy, which both can be run from RAM even with only 512MB of ram...



Dont blame ubuntu. Blame the cheap and slow SSD disk. And Acer for putting those to your machine.

PS. I used to think that SSD-disk are faster then normal hd:s.. what a joke. Is is about as slow as a old floppy disk, except the floppy disk would propably be faster.

---

### Post by Jarige on 2010-02-02
bump

---

### Post by 3rdalbum on 2010-02-02
The SSDs in netbooks are absolutely shocking. Very slow for writing. My netbook's SSD has a write latency of up to 9 seconds - it can take up to 9 seconds to start writing a piece of data to this SSD. By comparison, hard disks have a write latency that is measured in milliseconds.

There are two things you can do:

1. Format your SSD as ext2 and run Lucid Lynx (it's in alpha but it's stable enough for a netbook, and it feels much faster than Karmic)
2. Or, modify your netbook so that it uses a hard disk (only attempt this if you're confident with hardware and you have a HOWTO).

I do the former.

---

### Post by ericface on 2010-02-20
I am having the same issue. I hate to say this but i'm thinking i should have stuck with linpus.... 

btw i have the same acer model and 8gb ssd. there has got to be a fix for this. its like ever since i put ubuntu netbook remix on here my netbook has been slowly dying. i can't run firefox anymore. it wont even open. i run the janitorial tools and it hangs a rediculous amount. and sometimes it bombs so bad that i have to run a rediculous amount of disk commands to get it up. thats what she said. LOL but seriously. help?

---

### Post by ericface on 2010-02-20
nevermind. mount of filesystem failed. i dont know if its worth fixing. does crunch eee ubuntu work with acer aspire one's?

---

### Post by Jarige on 2010-02-20
Well I kinda gave up on this SSD and ordered an other one right here from eBay:
[http://cgi.ebay.nl/Super-Talent-32GB-SSD-for-Acer-Aspire-One-FEM32GF13M_W0QQitemZ380197031566QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item5885824e8e#shId]("http://cgi.ebay.nl/Super-Talent-32GB-SSD-for-Acer-Aspire-One-FEM32GF13M_W0QQitemZ380197031566QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item5885824e8e#shId")

This SSD is said to be compatible with the AAO. I'm still waiting on it though, they had a little delay because some plane crashed and the power went down. [http://www.cnn.com/2010/US/02/17/california.plane.crash/index.html?iref=allsearch]("http://www.cnn.com/2010/US/02/17/california.plane.crash/index.html?iref=allsearch")
Thats just my luck -.-
Three people died, I feel sorry for the families...

But I don't know whether this will be fixed with eeebuntu. I didn't try it. I'm not going to either. After some research I found out that Windows XP had the same problems, so its probably the SSD. I also found out that this upgrade fixed the problem, and made the netbook a lot faster. It is said to make it so much faster that it's a 'new computer' all of a sudden. So I'm waiting anxiously... 

I do recommend a RAM upgrade. If you can get a 1GB RAM thingy, I'd recommend to put it in at the same time you're gonna put the new SSD in it. You won't have to open up your AAO two times. I'm gonna place the results of my upgrade right here as soon as possible.

---

### Post by jpl888 on 2010-02-20
In answer to the original post, and I'm sorry I know this is a complicated answer but getting your SSD to run (and write) as fast as possible is all about partition alignment.

Cutting a long story short if you make sure that every partition starts and finishes on a 1MB boundary i.e. a sector divisible by 2048 your SSD will work better.

For instance I have a first generation SSD (OCZ Core V2 64GB) and with that alignment I don't get any hanging when the disk is under heavy use (well maybe a second or two).

I did a review of a Photofast Monster G5 and to be honest with the correct alignment the computer didn't feel any slower, day to day, with the OCZ, so it does make a lot of difference. 

Of course YMMV.

Let me know if you want to know how.

---

### Post by ericface on 2010-02-20
ya i upgraded the ram to a gig. but i still have the hd. kinda. ive been running fsck for every boot now. i think it just blew up tho. i can't even install moblin because of some sda junk. i think my hd just died. I can run live oses from usb's with no problem. its actually kick me in the nuts fast when i do. im gonna order me a new ssd and chalk this one up to inexperienced netbook designers. its not their fault. it was brand new technology so really i guess i cant complain. just replace. i do hate taking these things apart tho.

thanks for replying so quick guys. helped me to keep my sanity. i think im going to have a ssd burning party after work and light the mother effer on fiah.

thanks again.

---

### Post by jpl888 on 2010-02-20
BTW using an SSD for swap is bad.

Here is my layout for the craic!

```
Model: ATA OCZ CORE_SSD (scsi)
Disk /dev/sda: 125206528s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End         Size        Type     File system  Flags
 1      2048s      309248s     307201s     primary  ext2         boot
 2      311296s    17577984s   17266689s   primary  ext3
 3      17580032s  125204480s  107624449s  primary  ext3

```

---

### Post by ericface on 2010-02-20
unfortunatly im a noobasaurus hex with linux unless im running sudo commands through telnet lol. so i dont know what you just posted but it does look useful and i do appreciate it.

---

### Post by jpl888 on 2010-02-20
Well it would involve completely repartitioning your system and either reinstalling or copying back the data from your partitions.

---

### Post by ericface on 2010-02-20
this might sound crazy... 
I hooked up an external optical drive and ran a low level format utility in a preboot environment. I rebooted and am now able to not only use the ssd but i am almost done installing moblin and it is great success. going really fast too. Im starting to think that this isn't a hardware problem at all. I'll keep this thread updated with my successes or epic failures.

---

### Post by Jarige on 2010-02-20
If you could already give out a guide on how to partition the drive I ordered (32GB) that would be very nice :) I'm not gonna repartition this 8GB crap drive when the 32GB could be here any day :P

I do like precise instructions though. I know how to boot from a USB drive, so no need to explain that. I've got a spare 2GB USB drive for booting :P And I'm going to install 9.10 on the 32GB. I'd be most grateful if you'd write a step by step guide on how to do so with the sector size dividable by 2048 stuff. I know a little about the theory behind that, but I don't know how to partition it that way.

Thanks for your reply, jpl888, and good luck ericface :) You were the guy that made jpl888 reply here :)

---

### Post by ericface on 2010-02-20
lol it worked!!! and moblin is running ritarded fast. GREAT SUCCESS! i got scared of the 120 bucks that replacement hd would cost. but this is amazing. i am not only on facebook and youtube but i am on them both at the same time! and my computer hasnt flipped me off yet! i know its probably bad etiquette to talk about how great another os is on a ubuntu forum but really moblin fixed it after a low level format. maybe it just needed a fresh os install.

---

### Post by jpl888 on 2010-02-20
> **ericface said:**
> this might sound crazy... 
I hooked up an external optical drive and ran a low level format utility in a preboot environment. I rebooted and am now able to not only use the ssd but i am almost done installing moblin and it is great success. going really fast too. Im starting to think that this isn't a hardware problem at all. I'll keep this thread updated with my successes or epic failures.

I've read somewhere that low level formatting does help SSDs but I expect that once you've been using it for a while the performance will degrade again unless you have good alignment (hee sounds really fung shway huh?)

Jarige I can't really give precise instructions until you can tell me how many sectors your 32GB drive has so we will have to wait.

Here is some reading in the mean time [http://www.johnlewis.ie/2010/02/17/a-note-about-ssds-and-partition-alignment/](http://www.johnlewis.ie/2010/02/17/a-note-about-ssds-and-partition-alignment/)

Alternatively you can use the entire drive without a partition table on it and then alignment becomes irrelevant. Then you would be restricted to only one file system on the drive, which may not be what you need.

---

### Post by Jarige on 2010-02-20
Well I'm very happy for you :D
I did order the 32GB drive though, I might as well put it in anyway. And I don't want Moblin (no offence, its Linux either :)) so I'll stay with Ubuntu. It would probably very fast with the new drive, and with the tips I hope to get from jpl888 :D
I'm looking forward to be happy too :P :)

---

### Post by jpl888 on 2010-02-20
Yes well Moblin (or should we call it Meego now?) is a lovely looking OS, nice and funky. I just find it a little inflexible.

For instance I didn't want to use DHCP with the wireless connection but Moblin won't allow you put a static IP config in :(

It is very nice though.

---

### Post by Jarige on 2010-02-20
You replied exactly while I was typing my reply to ericface :P

Well I don't need multiple partitions I guess. I'm not sure why I would want that. And with 1.5GB (I really hope the 1GB RAM would fit in the slot btw, I don't even know if it fits :| ) I hope I won't need a swap partition.

So no partitioning seems fine to me.

And ericface, I might question you about the RAM upgrade tomorrow. My brother's got an older broken laptop (motherboard broke down, repair costed about as mch as a new laptop) and I hope to take out the RAM of that laptop, and put it in my netbook. I'm not a hardware guy, but I do know that the slots might not always be the same. What type of slot is in our AAO? I'll hope to get more info tomorrow about the type of slot in the old laptop.

---

### Post by jpl888 on 2010-02-20
Well I haven't tried it myself but I know it is doable in theory.

I would say speculatively that you would create a file system on /dev/sda before you start the Ubuntu installer, then choose manual partitioning when in the installer so it get's left intact. Whether Ubiquity will let you select just /dev/sda as the root partition is a question we won't get answered until somebody tries it.

I'm also not sure how the automatic creation of the grub config file will cope with that either, so it may be necessary/wise to check grub.cfg before rebooting.

---

### Post by Jarige on 2010-02-20
Will there be any difference between /dev/sda1 and /dev/sda then?
I don't quite get this all, to be honest. Is there no way of selecting the sector size whilst/before installing? I have to repartition the drive anyway when it arrives, its probably a FAT32 partition.

---

### Post by jpl888 on 2010-02-20
sda1 won't exist only sda.

Sorry I'm confusing you.

I think the best way for you to do this is to create one partition on the drive when you get it. Then there won't be much calculation to do.

So you would boot off the live CD and run ```
sudo parted /dev/sda
``` from the terminal.

Type ```
unit s
``` to change the units parted accepts as input to sectors.

Then type ```
mkpart
``` choosing primary and partition one, start sector would be 2048 and we don't know the end sector yet because you haven't got the drive. We would want to make sure that the last sector is divisible by 2048 and change it if necessary.

Exit from parted and then type ```
sudo mke2fs -j /dev/sda1
```

Then you will be able to start the installer normally albeit choosing manual partitioning, making sure to select /dev/sda1 to be mounted as root.

Is that clearer?

---

### Post by Jarige on 2010-02-20
Well that made it more clear, thank you. I just don't get why the partition should start at 2048. I know its a binary number, but why not let it start on 0? I've seen this before btw, I know there's probably a good explanation to this :)

And I hope the new SSD will be here soon. But I haven't heard of it for a day now. It's probably on board some ship. I've got some track and trace number, I can easily track down my package. I geuss you already know that exists :P It has to come from California to the Netherlands, so... Its gonna take a while I suppose. They had some delay either. I ordered it last Tuesday evening.

Thanks again for the replies, I'll contact you again when the SSD arrived, if possible.

---

### Post by jpl888 on 2010-02-20
BTW we aren't choosing the sector "size" we are just making sure that the partition starts and ends on a sector that will work well with the SSDs erase block size. 

Since erase block sizes vary from SSD to SSD it makes sense to use a 1MB boundary (2048 sectors of 512 bytes = 1MB). 1MB will be divisible by all erase block sizes up to and including 1MB.

Make sense? No? It didn't to me for a long time but it does now :)

---

### Post by Jarige on 2010-02-20
Whow, you do reply fast :P

The only thing I don't understand is an erase block. Whats it for?

---

### Post by jpl888 on 2010-02-20
I think the first few sectors are taken up by the partition table.

Normally in, Linux anyway, partitions start at sector 63 for legacy reasons, something to do with CHS and LBA.

Starting a SSD partition at 31.5k isn't a good idea because blocks of the file system will sit astride 2 erase blocks instead of 1 hence the "stuttering" as it's referred to when writing to the drive.

I could draw pictures but hopefully you have the idea.

---

### Post by Jarige on 2010-02-20
Your information, in combination to some Wikipedia (that site is awesome for technical stuff!) made it quite clear enough I guess. I hope your commands will work, but I guess they would. It makes sense. I'm just a little disappointed that I already bought the new SSD. There's nothing you could do about it, btw. I'm not blaming you :P
It did gave me a reason to buy more storage though :)

I hope to hear from you again :)

---

### Post by jpl888 on 2010-02-20
The erase block (size) is simply the size of data that the drive overwrites (in a multiple of) when a file is written to the disk.

If we take the example of a 16K file. If the erase block size is 4k when the file is written to the disk 4 (erase) blocks will be overwritten.

If the file system isn't aligned properly the same 16k file will occupy 5 blocks instead of 4 hence giving the poor SSD 25% more work to do. 

I can't think of a better way to explain it than that.

So to again explain the 1 MB boundary if the erase block size is 4k a 1MB boundary is ok because 1024KB (1MB) is divisable by 4K 256 times.

Hence 16k block size goes into 1024k (1MB) 64 times.

Hence 64k block size goes into 1024k (1MB) 16 times.

And so on and so forth.

It's the reason Windoze Vista and 7 use the 1MB boundary by default when partitioning.

Jaysus I could nearly write a thesis on it at this stage (not!)

---

### Post by Jarige on 2010-02-20
I do understand what you're saying :) You made it even more clear. I thought erase blocks where for erasing only. After your 'thesis' (:P) I thought this was the definition of a sector. What exactly is the difference between those a sector and an erase block? And, I heard that the bigger the erase block is, the more space a file takes on the drive. That's a pity, but it's probably worth it in speed anyway...
Thanks for your patience :D

I'm getting tired now (its 0:30 now :O ) so I might not respond fast after this message. I read you're from Ireland? Must be 11:30 or 10:30 there... So good night to you :)

---

### Post by jpl888 on 2010-02-20
Obviously if you have a lot of files which are 4KB or less (like on a Gentoo system cos of all the source code files) then your SSD problems will be piled on a thousand times with a bad alignment, in the scenario I just described.

---

### Post by Jarige on 2010-02-20
Last reply before sleep:
And what is the difference between a sector and an erase block?

---

### Post by ericface on 2010-02-20
[http://www.youtube.com/watch?v=-EfzckyZMTk](http://www.youtube.com/watch?v=-EfzckyZMTk)

great guide for upgrading ram in the acer aspire ones.

---

### Post by jpl888 on 2010-02-20
> **Jarige said:**
> I do understand what you're saying :) You made it even more clear. I thought erase blocks where for erasing only. After your 'thesis' (:P) I thought this was the definition of a sector. What exactly is the difference between those a sector and an erase block? And, I heard that the bigger the erase block is, the more space a file takes on the drive. That's a pity, but it's probably worth it in speed anyway...
Thanks for your patience :D

I'm getting tired now (its 0:30 now :O ) so I might not respond fast after this message. I read you're from Ireland? Must be 11:30 or 10:30 there... So good night to you :)

When you are overwriting a file you are erasing it. When a file is deleted from a file system the data is still there just the reference to it is deleted. So when something gets written in the "free" space (which has actually got data in it albeit unreferenced) data is in fact being overwritten (unless that space hasn't been used before obviously.

I don't know what the difference is exactly, but I do know that what most drives report to the operating system in terms of geometry i.e. cylinders, heads, etc. is in fact bollox and cannot be relied on by the OS so perhaps the sector size i.e. 512B is the same and it doesn't really mean anything any more.

I am probably making logic errors all over the place at this stage but it makes sense to me anyway ;) meh...

nighty night.

---

### Post by jpl888 on 2010-02-20
Just looking at disk sectors on wikipedia and sectors and blocks look like they are synonymous. So I think what I am saying is the sector size is normally reported by the drive as 512B which could well be a fallacy and the erase block size (at least what we are referring to here) is the real unit size the device actually uses to store data.

---

### Post by ericface on 2010-02-20
great explanations jpl888! can i give you beans or props or something? im going to reinstall moblin with some manual ssd work. im excited.

---

### Post by jpl888 on 2010-02-20
I don't know if you can give me beans?

And if you do will it give me wind? ;)

I'm just happy to have my ego massaged. It takes my mind off being a dribbling idiot ;)

---

### Post by ericface on 2010-02-20
frik. im still getting dev sda errors. i guess you were right to buy a new hd. thats unfortunate since the machine only cost 200 bucks and now i gotta shell out 120 for a hd.:( ah well at least i can have my beloved ubuntu back when i replace the hd. now its even saying media test failure, check cable LOL no bootable device. awesome.

---

### Post by jpl888 on 2010-02-20
> **ericface said:**
> frik. im still getting dev sda errors. i guess you were right to buy a new hd. thats unfortunate since the machine only cost 200 bucks and now i gotta shell out 120 for a hd.:( ah well at least i can have my beloved ubuntu back when i replace the hd. now its even saying media test failure, check cable LOL no bootable device. awesome.

I hate giving up on these things. How did you low level format before i.e. which program did you use and how.

From reading around a bit using something like ```
sudo dd if=/dev/zero of=/dev/sda
``` should do a reasonable job of reinitialising the drive.

If you boot from the live usb you will be able to do that.

---

### Post by ericface on 2010-02-20
i hooked up an external optical drive and ran killdisk. but check this out.....

I opened the little ******* up and reseated the harddrive connector. I booted it back up and it said no parent device then went straight into moblin like it never skipped a beat. i hope this fix lasts for longer than 30 minutes lol.

*edit- its runnin like a beast now it seems.

---

### Post by jpl888 on 2010-02-20
Good stuff.

I have found that SATA connectors can be a little flakey. The odd time if I have removed my SSD for some reason, it will not come up and I have to re-seat it again.

---

### Post by ericface on 2010-02-20
nah it was a hirose connector. that stupid little ribbon was messing me up this entire time. it figures it was something easy.

i currently boot to moblin in under 5 seconds. currently running hd youtube movie trailers with no skips.. i repeat. no lag or skips at all. this is amazing, imma reinstall ubuntu netbook remix.

---

### Post by jpl888 on 2010-02-20
Just imagine if you get aligned as well. You won't know yourself.

I'm going to write a book on "Zen and the art of SSD alignment".

Zmmmmmmmmmm, did you hear that I've now attained the next level of consciousness.

Either that or I'm talking BS LOL.

---

### Post by jpl888 on 2010-02-20
I'm glad you're finally getting somewhere near what you should be from the li'le laptop.

It's like looking out the window at a sunrise when things like that happen.

---

### Post by ericface on 2010-02-20
HAHAHAHA!!!! oh man that seriously had me laughing. ya ill do the ssd work and read some steve hagen at the same time just so im completely in alignment.

---

### Post by Jarige on 2010-02-21
I'm glad for you ericface :) Can you somehow find out what alignment you use?
I'm still waiting for the SSD to come. And thanks again, jpl888, for the explanation :) You could be a teacher :D

I sure hope that the new SSD will connect correctly... I don't want trouble with it. And I didn't see the youtube link yet, but I will tomorrow. It's sunday, I don't expect my package to be here today as the mail doesn't come on sundays. But I think its on board some ship anyway...

---

### Post by Jarige on 2010-02-21
I executed some commands, for more information about the alignment of my old SSD:

```
name@computername:~$ sudo fdisk -l

Disk /dev/sda: 8069 MB, 8069677056 bytes
255 heads, 63 sectors/track, 981 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf1a23463

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         932     7486258+  83  Linux
/dev/sda2             933         981      393592+   5  Extended
/dev/sda5             933         981      393561   82  Linux swap / Solaris
name@computername:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             7.1G  5.9G  821M  88% /
udev                  243M  252K  243M   1% /dev
none                  243M  436K  243M   1% /dev/shm
none                  243M  196K  243M   1% /var/run
none                  243M     0  243M   0% /var/lock
none                  243M     0  243M   0% /lib/init/rw 
```

You might be able to see whether the alignment is wrong or not, jpl888. I looked up where my new SSD is, and it was in San Francisco at Februari the 19th.

---

### Post by jpl888 on 2010-02-21
```
sudo parted /dev/sda
```

```
unit s
```

```
print
```

Will give us the start and end sector values of each partition.

---

### Post by Jarige on 2010-02-21
This is the output:

```

GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Model: ATA P-SSD1800 (scsi)
Disk /dev/sda: 15761088s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start      End        Size       Type      File system     Flags
 1      63s        14972579s  14972517s  primary   ext4            boot
 2      14972580s  15759764s  787185s    extended
 5      14972643s  15759764s  787122s    logical   linux-swap(v1)

```

Thanks again for the time you took to help me :) Start 63, not dividable by 2. I don't know what that means though... I guess you'll know what to do with it :)

---

### Post by jpl888 on 2010-02-21
So to get your SSD 1MB aligned (and get rid of naughty swap at the same time) we would want 1 partition that starts at sector 2048 and ends at 15759360.

Obviously unless you copy off your data/partition first you are going to lose everything.

Don't try this at home kids!

---

### Post by jpl888 on 2010-02-21
I suppose by extension that if you wanted to use absolutely every inch of space on the SSD you would start the first partition at 64 and end it at 15761088, since 15761088 is divisible by 64 which should mean the SSD has an erase block size of 32K.

Similarly my own SSD number of sectors is divisible by 1024 which should/could mean it has an erase block size of 512k, but I suppose that could just be a coincidence and it could be lower than that either (I read a vicious rumour somewhere that it is in fact 64k on my drive)

---

### Post by jpl888 on 2010-02-21
Coincidentally I happen to be looking at GPT partitions at the moment (don't ask me why I just like having the latest thing sometimes) and found this quote about standard hard disks:-

> The 4 KiB alignment issue is unimportant for most disks made through 2009, but beginning in December of 2009, disk manufacturers have begun introducing models that employ 4 KiB sectors rather than the traditional 512-byte sectors. These disks use firmware remapping to make the sector size appear to be the usual 512 bytes; the computer (including GPT fdisk) sees each physical sector as being eight logical sectors. The drawback to this arrangement is that performance can suffer if critical filesystem features, such as disk allocation blocks, straddle physical sectors. I've run some benchmarks on a 1 TiB Western Digital drive. Details vary from one filesystem to another, but as a general rule, I found that read performance wasn't greatly affected, performance when writing large files was somewhat affected, and performance when writing many small files was dramatically impacted. Untarring a kernel could take roughly 1.5 to 20 times as long on unaligned vs. aligned partitions, depending on the filesystem.

So it seems this isn't a problem specific to SSDs anymore.

---

### Post by Jarige on 2010-02-21
I do think this is an SSD problem only, since erase blocks only exists on SSD's. Therefor it is different from sectors, although I do not know the difference. Erase blocks has something to do with erasing files, and sectors are some file allocation stuff. I suppose the sectorsize and erase block size should have the same size (or the sector should be a factor 2^n the size of the erase block, and the partition should start at the right sector (dividable by the erase block size).
I think that pretty much coveres the problem I have, my partition doesn't start well to the erase block size. And now I'm having the problem you described before.

Thank you for your reply. The commands you just gave very usefull.

I heard that there's a way of having two SSD's in one AAO btw. That could be usefull, I could have an extra data partition on my 8GB drive. Or just install Ubuntu on the 8GB, and place the /home partition on the other one. Nah, I'd like Ubuntu to boot from the 32GB. That one is way faster...
Ericface, do you know anything about this?

---

### Post by jpl888 on 2010-02-22
Well I still think the difference between sectors and erase blocks is conceptual at best. Anywho I decided to downgrade from ext3 to ext2 by removing the journal and changing fstab and it seems to have made a bit of difference.

Running postmark from Phoronix test suite I am getting 2000 transactions per sec instead of 1500 before. I didn't run the rest of the disk test suite cos I would be here all night and I have laptop work to do. Maybe it's just the placebo effect but the laptop seems to be responding a bit quicker too.

---

### Post by Jarige on 2010-02-22
Hmm, I'm just going to go with Ext4. It is said to be the fastest, and you can turn of journalling there either. You'll have the best of both sides...

My SSD arrived in the Netherlands, it hasn't arrived at my home yet. I hope to receive it tomorrow :)

---

### Post by jpl888 on 2010-02-22
Yes well that seems to help things again. Transaction performance is about the same but it's at least 10MB better on 2GB IOzone write performance.

---

### Post by Jarige on 2010-02-22
Whow, thats great :)
I'd like to know how you turned off journaling. I just know it is possible, but don't know how to do so...
Together with the commands you previously gave me, and the extra gb of ram should bring the blazing speed I expected from an SSD :D

---

### Post by jpl888 on 2010-02-22
Boot off a Live CD then ```
sudo tune2fs -O ^has_journal /dev/sda1
```

Better run a manual e2fsck after just in case```
sudo e2fsck -f -C 0 /dev/sda1
```

The "-C 0" gives you a nice progress indicator.

---

### Post by jpl888 on 2010-02-22
Apparently BTRFS is the dogs dooda's in terms of performance, but I haven't enough time to sort it out if it borks my setup. I'll just wait until it's stable (I think in Lucid?).

---

### Post by Jarige on 2010-02-22
Thanks for the commands again :) Can't wait messing with the stuff.
Since this is my main usage computer, I'm not going to experiment with unstable filesystems :P But since its holidays in the Netherlands anyway, I've got some time to go under the hood of this thing.

---

### Post by jpl888 on 2010-02-22
Yes I think it is a man thing, the urge to fiddle if you'll excuse the pun.

I came from Gentoo, it's fiddlers paradise but it could consume your life if you let it.

---

### Post by Jarige on 2010-02-22
I'm a real man :) (I'm turning 18 in about a month)
Resisting temptation is something every man needs to learn :) (and every woman too btw :P )
And patience is important too. Waiting for my SSD...

I use a lot of smiley's, I noticed... I wonder why, cause you don't use them, and seem to get along pretty good. Did you notice that?

---

### Post by jpl888 on 2010-02-22
Yes I've been trying to teach my 14 year old daughter who lives in England restraint, it's working so far anyway.:?

Urm, well I suppose I've never really gone in for internet speak and trends that much and I've seen a few dodgy smiley programs for Windows that were spyware so smileys are tarnished for me always. I only like the tongue in cheek wink ;)

And I think you could count the amount of times I've used LOL on one hand including this post.

I'm a strange conundrum of a man. Forward thinking in some ways and resistant to new things (well things that I think are bollox) and change in others.

---

### Post by Jarige on 2010-02-22
You do seem conundrum, seeing all those English words I keep looking for in the dictionary :) Its like a puzzle sometimes. But I like that, it keeps my English on level in the holidays. English is one of the most important subjects I have, currently. The most important is ADP (at least to me it is). ADP is a translation from the Dutch 'informatica', from the dictionary. Apperantly 'informatics' is something different then what I mean. I mean ADP as in 'automatic data processing:  the branch of science and technology that is concerned with methods and techniques relating to data processing performed by automatic means'

I think I'm not quite so different from you. I am cutting-edge on computer techniques, always keen to hear new technologies, and always ready to install the new Ubuntu. But I'm quite resistant to changes in lifestyle, habits and other things ('bollox', is that 'useless' in this context? [http://en.wikipedia.org/wiki/Bollox](http://en.wikipedia.org/wiki/Bollox)). I hate getting a new job, for instance, it changes my habits, and might influence my lifestyle.

Whow, long message :)

---

### Post by jpl888 on 2010-02-22
Yes well "useless" would certainly come under the bollox umbrella, but to me it is more than that.

Like an Apple ipad. Something that some people seem very excited about and like to create hyperbole in relation to, but is ultimately useless and will be forgotten in the fullness of time.

---

### Post by Jarige on 2010-02-23
Ah, a new fresh day today (although its already about 10:50 here).
I find the iPad bollox either...

I've got nothing more to say, gotta get out of bed first :P
This will be a long day of waiting :S

---

### Post by Jarige on 2010-02-25
Well I got my netbook today, and the extra RAM is in it, and the SSD is in da box :D
This is the output of the following commands:
```

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) unit s                                                           
(parted) print                                                            
Model: ATA FEM32GF13M (scsi)
Disk /dev/sda: 60292512s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

```
I'm not quite so sure what to do next... I can see the sector size is 512B, but I don't know what that says about the erase size...
Can you help me, jpl888?

---

### Post by jpl888 on 2010-02-25
```
mkpart
```
```
primary
```
```
2048
```
```
60291072
```

Will give you a 1MB start and end to the partition. Then exit and type:-

```
mke2fs -t ext4 /dev/sda1
```

Which will create your spanking new ext4 filesystem.

```
tune2fs -O ^has_journal /dev/sda1
```

Which will disable naughty journalling and finally

```
e2fsck -f -C 0 /dev/sda1
```

Just to make sure everything is alright after all that.

You will then be able to go into the Ubuntu Installer and choose manual partitioning. Don't choose the option to format and do make sure sda1 is selected as root "/".

I think that's it though I could be wrong.

---

### Post by Jarige on 2010-02-25
Hmm, it goes wrong at the first command already:

```

ubuntu@ubuntu:~$ sudo parted /dev/sda
GNU Parted 1.8.8.1.159-1e0e
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) mkpart                                                           
Partition type?  primary/extended? p                                      
File system type?  [ext2]? ext4                                           
Start? 2048                                                               
End? 60291072                                                             
Error: The location 60291072 is outside of the device /dev/sda. 

```

And I already selected the filesystem here, since I was already asked to do so...
Thanks for your fast reply :D

---

### Post by jpl888 on 2010-02-25
You have to type ```
unit s
``` as soon as you go into parted or it will use KB or MB or something like that instead of sectors which isn't what we want.

AFAIK parted will only create ext2 filesystems so that is why I am telling you to create the file system using mke2fs.

---

### Post by Jarige on 2010-02-25
Its currently checking the SSD :)
I did need to change the command slightly, the 0 was not needed.

I'll keep you updated...

---

### Post by Jarige on 2010-02-25
Well, it worked :D
I'm kinda late with this reply, since I was distracted by TV, and customizing my netbook. Awesome, this text just appears exactly when I push the buttons :D
And I can play music on Youtube, make homework, and chat with my friends, all at the same time!

jpl888, I would like to thank you very much. Without you, I would probably have a mess of an SSD... And ericface, good luck to you too :)

This will probably be the last post. I'm so darn happy :D
I might make a VM with XP tomorrow, just for fun xD

This post makes no sense, but thats because I'm happy I guess. Dude, its like getting a new pc all of a sudden :D

Boottime are not really that fast, but it's reasonable. I'm curious what 10.04 has in store for us.

Thank you again :) I will mark this topic solved.
The solution was formatting the drive, respecting the 2048 sector boundaries. The starting and ending sector should be dividable by 2048. I hope I explained that well... I ordered a new drive anyway, for the extra speedboost and storage.
My next page will be a short tutorial on how to do this, using the commands I got from jpl888.

---

### Post by jpl888 on 2010-02-25
I'm not sure exactly what the time frame is but at some point fdisk will start using the 1MB boundaries by default, when the latest version makes it's way into Ubuntu.

There is no word on libparted based packages yet so your how to will certainly be useful for 6 months to a year I would imagine.

I'm glad you had a good experience. I have to thank you for recommending ext4. I tried using it just over a year ago with Gentoo, had a bad experience and was wary of it. Your recommendation gave me the onus to give it another go and I am very happy with it so far. I'll await your how to with baited breath.

---

### Post by Jarige on 2010-02-25
Well here is the tutorial. How to speed up your SSD.
First of all, credits go mostly to jpl888 for the commands and explanation. All I did was creating this tutorial, he did the actual thinking I guess :)

Note:
You will need to format your SSD, so be sure to backup your data before even starting this! And remember that this installation will NOT create a swap partition. If you have enough RAM then that will cause no problems. I do recommend at least 1GB if you don't have a swap partition.

1. The first step is to make a bootable USB stick with Ubuntu, or Ubuntu Netbook Remix. Or of course, use a LiveCD. You can make a LiveUSB by downloading unetbootin. In Windows, you can just search on the internet. In Ubuntu, its even more easy. In 9.10 you can just go to the Ubuntu Software Store and search for unetbootin, and install it.

2. Partitioning 
The hardest part.
Now you just need to boot into the LiveUSB or CD. Open a terminal (Applications -> Accessories -> Terminal). Execute the following commands in this order (these commands asume that you're installing Ubuntu at the first harddrive! If there's only one harddrive, then these are the commands you want). Each new line is considered a return.
```

sudo parted /dev/sda

```
Parted will start now, and it  will present you with (parted) texts. You can just keep on typing after that:
```

unit s
print

```
This is where it gets a little complicated. You'll see a table with all your partitions on /dev/sda. You'll need to find the highest 'end' value. For me, this was something like 60291455. Now, take that number and divide it by 2048. 60291455/2048 = 29439.187011719. Now round this number down. Take away the part after the ' . ' or the ' , '. For me, this was 29439. Now multiply that number by 2048 again. I got 29439 * 2048 = 60291072 after that.
Remember this number, you'll need it later.

Now execute these commands, in the same terminal as the previous ones:
```

mkpart

```
You'll be asked a few questions. The first question can be answered with 'primary' or 'p'. The second must be 'ext4' or 'ext2' or whichever filesystem you chose. I did 'ext4' but I turned off journaling for an extra speed boost, so I could get best of ext2 and ext4. ext3 is out of question here :P
Then you'll be asked for start and end. For the start value, type 2048 and press enter. For the end value, you'll need to use the value you calculated before. 60291072 for me.

Now quit parted by typing this:
```

quit

```
That was obviously :P
But now actually create the partition by executing this:
```

mke2fs -t ext4 /dev/sda1

```
This may take a while.

3. Stop journaling (optional!)
Turning off journaling will improve harddrive speeds, and increase they're lifespan, but will increase the change of dataloss in a power failure.
You can turn off journaling using this command (in LiveCD or USB):
```
tune2fs -O ^has_journal /dev/sda1
```

4. Check for errors (optional!)
This may take quite some time, but if you want to make sure whether the filesystem you just created is alright and usable you may want to execute this command:
```
e2fsck -f -C 0 /dev/sda
```

5. Actually installing Ubuntu
There's an icon on he desktop for the normal Ubuntu users, and for the Ubuntu Netbook Remix users I actually forgot where it is. Tell me if you know pls :) It is somewhere in the menu's in the top left side of the screen. It should be a pretty obvious name.
Just follow the first steps. But as you come into the partitioner, make sure you select manual partitioning! Then select the partition you created, WITHOUT formatting it. As for the mountpoint, it should be '/' (root). Then move on the next steps.

6. Wait for it to install

7. Boot into your freshly installed Ubuntu, and go customise it to your needs :)

I heard that the problems I had, and you may have, will be fixed somewhere in the future. But as long as these problems exists, this is probably the place to go.

I hope to hear your responses, and improvements :D 

Again, the credits belong to jpl888... :D

Jarige

---

