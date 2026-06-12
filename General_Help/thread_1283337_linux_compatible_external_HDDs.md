---
title: "linux compatible external HDDs"
date: 2009-10-05
forum: General Help
---

### Post by yanvolking on 2009-10-05
Hello Community,

When I look on the packaging of external hard disk drives, most claim to work with Windows and Mac OS.  Comparatively few claim to work with Linux.  Does that mean that a hard disk drive whose manufacturer does not mention that it can work with Linux on the packaging will NOT work under Linux or create problems in that environment?

---

### Post by MrWES on 2009-10-05
I personally never came across an external drive that didn't work with Ubuntu; USB, SATA, or eSATA for that matter. I've put many drives inside enclosures and never had an issue. I currently use a 1TB eSATA and a 30GB 2.5" drive daily without issues. The 1TB is formatted ext3, and the 30GB fat.

Bill

---

### Post by Roasted on 2009-10-05
I second that. Every flash drive* and every external hard drive has worked with Linux.

*The only thing that hasn't worked in Linux is, sometimes you get a flash drive and it comes with some garbage software on it for whatever freak reason. Each and every time I see this is drives me nuts and I format it to remove this program. However, my point is, that stupid little program is normally a Windows program, which obviously wouldn't work in Linux.

BUT - for storage purposes - every single drive I've tried has worked in Linux.

---

### Post by muteXe on 2009-10-05
Same with me.   I have 3 external drives of different makes. They all work okay on both my ubuntu and slackware partitions.

---

### Post by j7%&lt;RmUg on 2009-10-05
Certainly not, but alot of manufacturers simply leave linux off the "supported" list.

I have a Western Digital My Book 640GB (that i bought for $100 AU brand new im happy to say, which is really REALLY cheap for that size in oz) which worked perfectly out of the box.

Although most external hard drives work fine, my brothers HP 120GB external HDD doesnt work at all (but thats the first iv come across that doesnt).

---

### Post by yanvolking on 2009-10-05
Hi Guys,

Thanks for the fast reply.  Good news indeed.  When I get one of these external Hard Disk Drives,  Should I format it in NTFS, or Ext3?  I believe that NTFS formated drives can work under UBUNTU.  But is the reverse equally applicable? This is important as I have a dual boot windows/ubuntu computer and I need to work the HDD under both systems depending on the circumstances.  Finally, if Ext3 is advisable, how do I format the Drive?  Can it be done from within a UBUNTU application much like the right click then format function under "properties" title in Windows?

Thanks

Yan

---

### Post by anonymous_user on 2009-10-05
Since you want to use it with Windows, I would format is as NTFS.

To format a drive, you can use GParted. Go to System > Administration > Partition Editor

---

### Post by trikster_x on 2009-10-05
Actually, a new external HDD should work out of the box with both windows and linux.  I use one to store most of my media backups and it has always worked with the default msdos filesystem.  I have heard that the newest seagate freeagent externals do have some issues with linux OS:

[http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/](http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/)

[http://www.linuxquestions.org/questions/linux-hardware-18/fun-with-a-seagate-freeagent-pro-565473/](http://www.linuxquestions.org/questions/linux-hardware-18/fun-with-a-seagate-freeagent-pro-565473/)

Typing linux seagate freeagent in google will reveal a great many more of these.  For my money, I would go with a MyBook brand exernal.

---

### Post by Roasted on 2009-10-05
Just to tack in some additional info here, this is what kind of storage media I have used in Linux that has worked flawlessly.

Sandisk 8gb Flash Drive
Memorex 4gb Flash Drive
Lexar 2gb Flash Drive
Kingston 1gb Flash Drive

Western Digital MyBook 1TB External Hard Drive
Maxtor 160gb External Hard Drive

Western Digital 80gb IDE Hard Drive in External Enclosure
Seagate 80gb IDE Hard Drive in External Enclosure
Hitachi 40gb IDE Hard Drive in External Enclosure
Maxtor 20gb IDE Hard Drive in External Enclosure

So right there is a wide range of hard drive types and manufacturer's I've used (flawlessly) with Ubuntu Linux.

---

### Post by twright on 2009-10-05
I likewise have used many external harddrives in Ubuntu and none have failed to work.

One thing is though whatever drive you get will probably come formatted as FAT or NTFS, neither of these filesystems is very good at preventing corruption or fragmentation which could cause big programs if the driver is more than several hundred GiB - when you get it I recommend you format it to a better filesystem to keep your data safe (I use ext4 on mine).

---

### Post by Roasted on 2009-10-05
> **twright said:**
> I likewise have used many external harddrives in Ubuntu and none have failed to work.

One thing is though whatever drive you get will probably come formatted as FAT or NTFS, neither of these filesystems is very good at preventing corruption or fragmentation which could cause big programs if the driver is more than several hundred GiB - when you get it I recommend you format it to a better filesystem to keep your data safe (I use ext4 on mine).

Good call, but this is also very dependent upon what the user intends to use the external drive for.

Example - My 1TB WD external drive is EXT3. Why? Because I need it for Linux only. However, my 160gb Maxtor drive is FAT32. Why? Because I need it for Windows and Linux use.

It always seem that, Linux tolerates Windows, but Windows hates Linux. That being said, Linux will read/write NTFS + FAT32, but if you're using EXT2/3/4, you're stuck with Linux only.

Every scenario is very situation dependent, which is why I format my drives accordingly to what I need to do.

---

### Post by twright on 2009-10-05
> **Roasted said:**
> Good call, but this is also very dependent upon what the user intends to use the external drive for.
Very true, I used to use NTFS but then I started caring about my data more and stopped using windows on anything.

---

### Post by scouser73 on 2009-10-05
I've never seen any external drives that are made to work on Linux, but all my externals that I have do.

---

### Post by Roasted on 2009-10-05
> **scouser73 said:**
> I've never seen any external drives that are made to work on Linux, but all my externals that I have do.

In fact, my Sandisk USB Flash Drive is the only "Linux Certified" device I've used, as far as storage media goes. But yet, everything still works even if it's not "supported." 

Damn, I love Linux. :guitar:

---

### Post by twright on 2009-10-05
> **scouser73 said:**
> I've never seen any external drives that are made to work on Linux, but all my externals that I have do.
Well of course they don't 'support' linux, they can only expect call center attendants to do so much; Linux supports itself and that's the way it should be.

---

### Post by blur xc on 2009-10-05
> **trikster_x said:**
> Actually, a new external HDD should work out of the box with both windows and linux.  I use one to store most of my media backups and it has always worked with the default msdos filesystem.  I have heard that the newest seagate freeagent externals do have some issues with linux OS:

[http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/](http://www.engadget.com/2007/12/07/seagate-freeagent-drives-not-down-with-linux/)

[http://www.linuxquestions.org/questions/linux-hardware-18/fun-with-a-seagate-freeagent-pro-565473/](http://www.linuxquestions.org/questions/linux-hardware-18/fun-with-a-seagate-freeagent-pro-565473/)

Typing linux seagate freeagent in google will reveal a great many more of these.  For my money, I would go with a MyBook brand exernal.

I  have a 1tb freeagent that I bought a couple of years ago, and have not had any of those problems.  It seems to me that they only happen when you are plugged into via usb ports, correct?  I've been running mine on an esata cable, and it's been great.

BM

---

### Post by scouser73 on 2009-10-05
> **Roasted said:**
> In fact, my Sandisk USB Flash Drive is the only "Linux Certified" device I've used, as far as storage media goes. But yet, everything still works even if it's not "supported." 

Damn, I love Linux. :guitar:

I love Linux too and I didn't mean to sound as if I didn't love Linux because since I've been using Ubuntu I've really liked getting to know something other than Windows.  I love the fact I don't need an anti-virus software, I love the fact that I don't need to defrag the PC.

---

### Post by t0p on 2009-10-05
Very few consumer hardware manufacturers mention Linux-compatibility, even though the equipment very often *is* Linux-compatible.  And why don't they mention Linux?  Because they don't *care* about Linux.  Because our market share is seen as irrelevant. (I know that isn't the case in the server market.  But how many commercial server operators use consumer hardware?)

Unfortunately, this state of affairs means we don't know if a specific piece of hardware will work with our systems.  It's usually safe to guess that the hardware *will* work.  But we don't know for sure, and it can be an expensive guess if we guess wrong.

What we need is more online resources that tell us about hardwae compatibility.  There are some, such as the [Open Printing Database]("http://www.linuxfoundation.org/collaborate/workgroups/openprinting").  But there aren't many; and the ones that *do* exist are often crap (have a look at this site's Desktop Hardware (In)Compatibility Lists.  User-unfriendliness incarnate).

Hopefully, someone somewhere will create an easily-searchable resource to advise us on hardware compatibility.  But until then, it's going to be a mixture of guesswork and blind faith.  Bah!  Curse Linux's so-called "market share"!

---

### Post by Greg Xix on 2009-10-05
You will be fine with virtually any exteral HDD.

One of the things I LOVE about Linux/Ubuntu is its compatibility & flexibility with hardware. This is an area where I believe Linux is far superior to Window$.

For example. The HDD's on my Main desktop and my Laptop each are SATA, so I can't install XP on those, only Vi$ta. I can install Ubuntu those, and my 2nd Desktop which is IDE.

On my Main PC and Laptop, Vista requires a "Driver Install" for the NIC Card, Wireless Card, Wireless Mouse, & Flash Disks. All of those with the exception of the Flash Disks require a reboot. So I either have to download or have copies of 3rd Party Drivers for the NIC and Wireless.

When I install any Linux Distro(Ubuntu, Mint, Knoppix) on my Primary or Laptop. Its ready to go on the **FIRST** login, no drivers necessary except for the Graphics.

---

### Post by yanvolking on 2009-10-07
Hi Guys,

Thanks for the replies.  Looks like formating my HDDs in Ext3 or Ext4 is a must.  But can a HDD formated this way work in a Windows environment? (I have my computers Windows/Ubuntu dual boot).

Thanks

---

### Post by scouser73 on 2009-10-07
If you want your external drive to be seen by Windows machines then I think it has to be formatted to either Fat32 or NTFS.

---

### Post by fela on 2009-10-07
It really winds me up when manufacturers don't mention Linux alongside Windows and OSX.

---

### Post by t0p on 2009-10-07
> **yanvolking said:**
> Hi Guys,

Thanks for the replies.  Looks like formating my HDDs in Ext3 or Ext4 is a must.  But can a HDD formated this way work in a Windows environment? (I have my computers Windows/Ubuntu dual boot).

Thanks

There is software that will enable Windows to read/write to ext3. Unfortunately I can't remember what the software is called. The good news is:  Google  Is  Your Friend! ;)

---

### Post by twright on 2009-10-07
> **t0p said:**
> There is software that will enable Windows to read/write to ext3. Unfortunately I can't remember what the software is called. The good news is:  Google  Is  Your Friend! ;)
I really don't recommend doing that as it risks corruption (the drivers are now unmaintained and not very stable).

I would just split it into an ext4 partition and a fat32 one - that way you will be able to access some stuff in windows whilst still having safe data storage for Ubuntu related stuff.

---

### Post by Roasted on 2009-10-07
> **t0p said:**
> There is software that will enable Windows to read/write to ext3. Unfortunately I can't remember what the software is called. The good news is:  Google  Is  Your Friend! ;)

Although now I forget the software name, I tried it about a week ago with no success. It required me to format the drive before using it. Since XP was telling me to format the drive to use it (which was an EXT3 external) I can't help but to wonder Microsoft would require me to format it as FAT32 or NTFS.

If it's for Windows/Linux usage, choose FAT32 or NTFS.

FAT32 cannot store individual files larger than 4gb in size. That being said, FAT32 is nicer for flash drives and smaller storage media, whereas hard drive, which almost always have a higher capacity, might be nicer to use NTFS with.

Give it a shot and see what happens.

---

