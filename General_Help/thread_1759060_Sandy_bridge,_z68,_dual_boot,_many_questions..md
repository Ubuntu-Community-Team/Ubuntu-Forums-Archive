---
title: "Sandy bridge, z68, dual boot, many questions."
date: 2011-05-15
forum: General Help
---

### Post by profozone on 2011-05-15
Greetings.  Let me preface this by apologizing for posting.  I have been searching, but the Z68 chipsets are so new it's difficult to find all of the information I need and I'm suffering from search fatigue.  That said, here is my reason for posting.  I am building a new computer and I would like to migrate to Linux as my primary OS, but I want to be able to boot into Windows on the same machine.  This creates multiple questions.  My plan for the hardware:  Intel 2600K Sandy bridge CPU (already purchased) 1155 Z68 motherboard 8 GB RAM 256 GB Crucial M4 SSD drive (already purchased) EVGA nVidia GTX 570 superclocked video card (already purchased) Other hard drives.  The Z68 chipsets will allow SSD caching called SRT.  To speed things up, I'd like to use this feature, but I don't know if it applies to both operating systems or not.  How do you partition the drive to handle them both?  Using this feature isn't as fast as just using an SSD the normal way, but due to it's size I will run out of room quickly if I use the SSD with two operating systems, I think.  So what to do?  I am nearly a complete Newb when it comes to Ubuntu.  I have installed Ultimate Edition on an old computer of mine and I liked it quite a bit, but I always defaulted to my Windows machine because it had the better hardware and a nice monitor.  I'd like to install UE on this machine.  As you can see I am in the middle of purchasing hardware so any suggestions on what is compatible with Linux would also be appreciated.  From searching I think I have made the right choice going with nVidia vs Radeon and I think when I go to install, I should first load windows (Windows 7) because Ubuntu will see it, but again do I partition with the 64GB used for the SSD caching or just split the drive in half?  Do I need two 64GB partitions?  Does the caching even work with more than one drive?  Lots of questions!  Danger Will Robinson!  Danger Overload!  Thanks for listening.  Any other recommendations are also welcome, of course.

---

### Post by profozone on 2011-05-15
Whoa!  That's really hard to read.  All my formatting seems to have disappeared.  Sorry.

---

### Post by profozone on 2011-05-15
Answering some of my own questions. Right now I don't think the caching even works in Linux, so that may be a non-issue.  Anything over 68GB becomes a user accessible partition.  Does that mean I could install Windows, set up the caching and then load Linux on the remaining portion?  Anybody?  Anybody?  Bueller?

---

### Post by lakerssuperman on 2011-05-15
Greetings,

I have a very similar setup that I just put together.  I am running a 2600k, P58 mobo, Geforce 560 Ti, Intel SSD plus 3 other mechanical drives for data and Windows.

To address your questions, in no particular order:

1) You can absolutely boot into Windows.  You install Windows first and then Ubuntu.  It will detect Windows and configure the Grub boot loader to give you the option of which you would like to load when you boot.

2) Depending on what you plan to do with Windows, you could just stick it on a conventional 7200 rpm drive.  I do this for my Windows install as I only use it for games and load times with this type of drive are more than fine for me.  I have my Ubuntu install on the Intel SSD to give the speed to my primary OS.  Finally I have 2 2TB data drives for my files.

3) I would have a dedicated drive for Windows as it doesn't like having itself split between two drives and you would want to only put the OS on an SSD, leaving you limited room for data.

4) I am not aware if SSD caching has any type of implementation on Linux.

5) I would think about using Ubuntu 10.10 with your NVIDIA hardware.  Their drivers are usually top notch, but in 11.04 there seems to be a severe bug that causes degraded performance when watching video.  10.10 and 10.04 LTS don't seem to suffer from this problem.  In years past NVIDIA drivers have been far superior to whatever ATI/AMD was offering.  Recently though, they have caught up and are in good shape now from what I've seen of them running on the Radeon 4870 I have in a spare machine.

This should be sorted out soon hopefully with a new driver release from NVIDIA.  Bottom line, either type of card will work and you should get whatever brand you feel more comfortable with.

My recommendation is to offload your data onto a large mechanical drive.  If Ubuntu is going to be your primary OS, then I would put that on the SSD and have a fast mechanical drive for Windows.  Load times of programs will still be acceptable, if not blazing fast like with the SSD.  Obviously if you plan to use Windows more heavily than this you will want a slightly different setup.

---

### Post by profozone on 2011-05-16
Thank you that was very helpful.  Let me make sure I understood what you said.

I have a 150GB raptor and a 300 GB velociraptor at my disposal as well as a 1TB Caviar Green.  So if I understand, you would recommend putting the Linux OS on the SSD alone and just use that for everything.  Put Windows on say the 300GB velociraptor and use either of the two remaining drives any way I want to.  That way each system gets it's own drive and the primary OS will get the fast one.  Right?

That would be fine for me.  The only question I had was if maybe I partitioned the SSD with 64 GB on one partition, used that partition when I'm in Windows to accelerate things there and use the other partition for everything Linux.  I thought that way I could maybe get a speed advantage no matter which operating system I was in.  Of course, I could always get another 256GB SSD, but that would mean coughing up another $470!.  Not going to happen.

Thanks for replying.  This is the most active forum I have ever been on.  my post was like 15 pages deep and my last post was only last night!  Holy Cow!

---

### Post by linutx on 2011-05-17
I am too planning on build a new Z68 based computer, running just Linux
Questions for the OP:

[LIST=1]
[*]Your motherboard's manufacturer?
[*]Z68 has integrated. GPU, is there any reasons as to why you opted for a discreet video card?
[/LIST]
Thanks for sharing and best of lucks

---

### Post by profozone on 2011-05-17
I wanted the z68 board because I don't really trust companies, so when they say they have solved the P67 and H67 problem, that is probably true, but I think there is a good chance they will sell off old stock of the bad ones and just not tell anyone.  Plus I kind of like the idea of the SSD caching.

There are two reasons I chose a discrete video card.  First, while I am not strictly a gamer, I do like to play them on occasion and a discrete card still destroys the on-board graphics of the one in the chip.  Plus at the moment, there are no z68 based motherboards with on-board graphics, at least not on newegg, where I get most of my parts.  Despite all of the articles in magazines and on websites telling you the sandy bridge has built in video, there is not a single board offered today that has it.  I'm sure it won't take long for that to happen, but because I don't care about that, I'm not willing to delay my purchase.

I haven't purchased the motherboard yet, but the one I am considering is:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813128493&cm_re=z68-_-13-128-493-_-Product](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128493&cm_re=z68-_-13-128-493-_-Product)

I have chosen this one for several reasons.  1. It has a lot of SATA ports.  2. It has a lot of USB ports.  3.  It supports faster RAM without it needing to be overclocked (at least that's the way it appears).  4.  Price is right, since I don't really need anything more than that.

The only problem I've had with that choice is finding RAM for it.  I always go to the board manufacturers website and find the compatible RAM and only order from that list.  Well like 80% of the RAM on their website is unavailable for some reason, at least the fast RAM I can effectively make 8Gb from.

Hope this helps.

---

### Post by oldfred on 2011-05-17
Do not know about that motherboard, but most of the new one's offer UEFI and BIOS. UEFI is the new better way but is having some issues working correctly. Then you get into gpt partitioning which is also the new better way. But windows only works with gpt if you use UEFI. 

Windows 7 64bit UEFI 2.x boot:
[http://www.insanelymac.com/forum/index.php?showtopic=186440](http://www.insanelymac.com/forum/index.php?showtopic=186440)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
[http://ubuntuforums.org/showthread.php?t=1746194](http://ubuntuforums.org/showthread.php?t=1746194)
Many links & discussion:
[http://ubuntuforums.org/showthread.php?t=1734677](http://ubuntuforums.org/showthread.php?t=1734677)
[SOLVED] Win 7, Natty dual boot on UEFI sort of working :
[http://ubuntuforums.org/showthread.php?t=1753717](http://ubuntuforums.org/showthread.php?t=1753717)

---

### Post by srs5694 on 2011-05-17
> **oldfred said:**
> Do not know about that motherboard, but most of the new one's offer UEFI and BIOS. UEFI is the new better way but is having some issues working correctly. Then you get into gpt partitioning which is also the new better way. But windows only works with gpt if you use UEFI.

There's no mention on Newegg's site about that board being a UEFI model, and Newegg *does* mention that detail for other models, so I suspect it's not a UEFI board. Checking with Gigabyte is worth doing, though.

This is an extremely important detail because, as you say, Windows can't boot from GPT on BIOS-based computers. (Windows Vista and 7 *can*, however, use a GPT disk as a non-boot data disk on BIOS-based computers.) The older MBR partitioning system tops out at 2 TiB (assuming 512-byte sectors), so use of BIOS limits future disk upgrade options under Windows. It's conceivable that Microsoft will correct this limitation in the future, but AFAIK they have no plans to do so. (I've spoken with engineers -- not customer support reps -- at two disk drive companies, and both report that Microsoft seems uninterested in correcting this limitation.) Windows' BIOS/GPT limitations might be important if you expect to upgrade to, say, a 4 TB disk in another couple of years.

Linux, incidentally, boots fine from GPT disks even on BIOS-based computers. (There may be limits on where particular files or partitions reside, though; drives over 2 TiB are still rare enough that I don't have information on that.) As oldfred says, Linux distributions, including Ubuntu, are still working the wrinkles out of installing to and booting from UEFI-based computers. It can be done, but may require some extra knowledge and persistence. Things are likely to improve with future releases for at least another year or so.

Thus, for a Linux-only system, BIOS has a slight edge today, but in the future the two should work equally well. For a Windows-only system, I'd have to give UEFI a solid recommendation over BIOS. For dual-boot it gets trickier because you've got to figure out how to weight the two competing recommendations, factoring in other issues such as your skill level, your current disk requirements, and your anticipated future disk requirements. Overall, I'd say that if you're not comfortable with technical issues BIOS is probably still better because of the quirks of installing Ubuntu on a UEFI system; but if you've got intermediate to advanced skills UEFI is better because of BIOS's limitations with Windows.

---

### Post by profozone on 2011-05-17
This is what Gigabyte says about BIOS/UEFI:

                      DualBIOS™ 3TB+ HDD Support (Hybrid EFI Technology)         
             Hybrid EFI Technology combines the benefits of GIGABYTE's mature BIOS  platform including stability and compatibility with 3rd party products  with 3TB+ HDD support from EFI technology, allowing GIGABYTE to offer  the best of both worlds through a quick and easy BIOS update using  GIGABYTE's @BIOS utility that is freely available from the GIGABYTE  website. 
 GIGABYTE DualBIOS™ is a patented technology that automatically recovers  BIOS data when the main BIOS has crashed or failed. Featuring 2 physical  BIOS ROMs integrated onboard, GIGABYTE DualBIOS™ allows quick and  seamless recovery from BIOS damage or failure due to viruses or improper  BIOS updating. In addition, GIGABYTE DualBIOS™ now supports 3TB+  (terabyte) hard drive booting without the need for partitioning, and  enables more data storage on a single hard drive.

I don't even know what GPT is.  Gotta search.  I also haven't looked at the above site yet.  I'll take a look when I have a moment.

Thanks for the replies.

---

### Post by srs5694 on 2011-05-17
The Gigabyte quote lays on the marketing-speak pretty thickly and is remarkably thin on actual information. It sounds like it may be an optional UEFI you can flash in place of the standard BIOS; or maybe it's a UEFI that supports a BIOS boot mode. (The latter is fairly common in UEFI-based systems.)

GPT = [GUID Partition Table.](http://en.wikipedia.org/wiki/GUID_Partition_Table) This is a new partition system that replaces the older [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) system that's been used on most PCs since the 1980s. MBR is limited because it uses 32-bit sector pointers, and in conjunction with a 512-byte sector size, this limits MBR to 2 TiB or smaller disks. GPT, by contrast, uses 64-bit sector pointers, so it should be adequate for a few more years. GPT also has several other advantages over MBR. Most of these are minor, like the addition of a partition name field and CRCs and backup data to help in case a non-partitioning tool overwrites or damages the main partition table. One GPT advantage that's more broadly relevant is the fact that there's no need for the hack that is extended and logical partitions; GPT supports up to 128 partitions by default, and that value can be increased if necessary.

---

### Post by profozone on 2011-05-17
Ok, so how do I know what I have?  It seems to me that if the GPT is new, that is what an SSD would have.  I went to Crucial's website and couldn't find it mentioned.  Re-reading what was written earlier, do I understand it correctly that if I get a GPT drive that Windows 7 will not boot on it assuming, of course, that the board has BIOS?  I would have to boot on a different drive and use the SSD for something else?  That seems incredible to me that a new operating system won't work on what is becoming a more and more common drive solution. Do you think that Gigabyte's "hybrid" BIOS accommodates that some how?  Thanks for the info!

---

### Post by oldfred on 2011-05-18
I only have BIOS but have converted one of my older drives to gpt and it works fine. With 10.04 I had to add a grub parameter to get the gpt drive to dual boot my XP on an MBR drive, but that has been fixed since 10.10.

I suggest keeping each operating system on separate drives. I have done that and have several Ubuntu versions on two of my drives and XP on a third drive. Then if any one drive fails I can still boot something on the others. While most of my data is on one drive, my backups go to another. 

Arch site has a page on SSDs and suggests gpt.
SSD’s, Journaling, and noatime/relatime 
[http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/](http://thunk.org/tytso/blog/2009/03/01/ssds-journaling-and-noatimerelatime/)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by psusi on 2011-05-18
What is this about SSD caching?  That doesn't have anything to do with the chipset; it is all about software.   I have heard that Windows 7 can do this, but Linux can not yet.

---

### Post by srs5694 on 2011-05-18
> **profozone said:**
> Ok, so how do I know what I have?  It seems to me that if the GPT is new, that is what an SSD would have.

GPT and MBR are both data structures that are written to drives when you partition them; they aren't immutable features of drives. In fact, every internal drive I've ever bought new has come with *no* partition table on it at all (MBR or GPT), although external drives often come pre-partitioned, usually with MBR.

You can change a drive from MBR to GPT or from GPT to MBR using software. As I wrote  earlier, which is best to use depends on factors such as the disk's size, the type of firmware your computer has, and the OS you're running.

---

### Post by gordintoronto on 2011-05-18
> **profozone said:**
> There are two reasons I chose a discrete video card.  First, while I am not strictly a gamer, I do like to play them on occasion and a discrete card still destroys the on-board graphics of the one in the chip.  

Plus at the moment, there are no z68 based motherboards with on-board graphics, at least not on newegg, where I get most of my parts.  Despite all of the articles in magazines and on websites telling you the sandy bridge has built in video, there is not a single board offered today that has it...


Actually, Newegg has a problem describing Sandy Bridge motherboards. There are several boards which use the CPU-based Intel video, but there isn't a video chipset on the motherboard, so that is how Newegg classifies them. When you look at the pictures, there are VGA and DVI ports. Eg:
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813131730&cm_re=z68_motherboard-_-13-131-730-_-Product](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813131730&cm_re=z68_motherboard-_-13-131-730-_-Product)

Your first reason is still valid, though!

---

### Post by profozone on 2011-05-18
> **gordintoronto said:**
> Actually, Newegg has a problem describing Sandy Bridge motherboards. There are several boards which use the CPU-based Intel video, but there isn't a video chipset on the motherboard, so that is how Newegg classifies them. When you look at the pictures, there are VGA and DVI ports. Eg:
[http://www.newegg.ca/Product/Product.aspx?Item=N82E16813131730&cm_re=z68_motherboard-_-13-131-730-_-Product](http://www.newegg.ca/Product/Product.aspx?Item=N82E16813131730&cm_re=z68_motherboard-_-13-131-730-_-Product)

Your first reason is still valid, though!

That is messed up.  Some of the boards say VGA card required, so I assumed that all of the ones that said "Video Chipset = none" (which was all of them until the Asus board showed up) needed a video card.  I never looked at the pictures.  Anyway, some of them don't and some of them do have outputs.  Either way I plan to get a discrete card.

Earlier someone said that the caching was software related, not chipset.  That may be true, but I'm not writing that software and from what I've read the SSD caching called SRT is only available on the Z68 boards.

So no one's still mentioned (or I haven't fully understood) whether I can partition the SSD to 64GB and use that partition with SRT so that Windows runs faster and use the rest of the 256GB for Linux.  It sounds like I could because I read that anything over 64GB is "user accessible" like a normal drive.  That way Linux would be fast using the large portion of the SSD and Windows would be fast using the 64 GB partition to do it's caching thing.  It could be installed on the velociraptor.  That would leave me with the raptor for data storage or even the 750GB drive I bought.

What do you think?  Possible?

Also, if I partition the drive, does that mean there is an option to use GPT or MBR?  I've partitioned disks in the past, but don't remember this.  If so, Do I just try GPT and see if it works or what?  Sorry, still a little confused on the details.

As usual, thank you for the input.

---

### Post by srs5694 on 2011-05-18
> **profozone said:**
> Also, if I partition the drive, does that mean there is an option to use GPT or MBR?  I've partitioned disks in the past, but don't remember this.  If so, Do I just try GPT and see if it works or what?  Sorry, still a little confused on the details.

If Windows will be booting from the disk, then:


[list]
[*]If your motherboard uses UEFI (or boots in UEFI mode), then use GPT.
[*]If your motherboard uses BIOS (or boots in BIOS mode)), then use MBR.
[/list]


If you start with an unpartitioned disk, then the Windows installer should set it up correctly, if you install Windows first.

If you start by installing Ubuntu on an unpartitioned disk, then the installer seems to use MBR for disks up to somewhere between 1 TiB and 2 TiB, but uses GPT on larger disks -- at least on BIOS-based systems. On UEFI systems, I'm pretty sure it defaults to GPT for all disks. This is made as clear as mud, BTW. If you want to force use of a particular partition table type, you must partition ahead of time, and know enough about your partitioning tools to select the right partition table type. Tools based on libparted (GNU Parted, GParted, etc.) support both MBR and GPT, but you can only switch when you opt to create a new partition table. The Linux fdisk tool supports only MBR (and some other relatively exotic partition table types). My gdisk tool supports GPT, although it can convert to and from MBR.

If you've got a board with UEFI that supports both UEFI and BIOS boot modes, you'll be able to choose either mode (although it may start up in a default mode and not make it obvious which it's using). In that case, from a Windows perspective, UEFI and GPT makes more sense because it's more future-proofed -- you'll be able to upgrade and replace disks with models that exceeed 2 TiB with less hassle. OTOH, as I wrote earlier, Ubuntu's UEFI support is still new enough that it's got a number of pitfalls, so it may cause you some problems in the short term.

---

### Post by profozone on 2011-05-18
Hmmmm.  Kind of complicated.  Thank you for the information.  I'll definitely refer to this thread when I get all my hardware.  So one more question.  Assuming the board is BIOS, for SRT, Windows expects to see a separate hard drive anyway.  Do you think I could partition the mechanical hard drive with MBR and put Windows on it.  Then partition the SSD with the 64 GB windows wants to see for SRT, using GPT, then install Linux on the remaining part?  Thanks again.

---

### Post by srs5694 on 2011-05-19
It's certainly possible to mix MBR and GPT disks on one computer; I've got two computers set up that way right now.

I agree it's too complicated with the MBR/GPT and BIOS/UEFI thing; but we're just at a transition point for these critical low-level technologies, and different OSs have different requirements. I expect it'll be much simpler for new hardware in a year or so; by that time, UEFI will be more common and better supported.

---

### Post by psusi on 2011-05-19
It looks like this SSD caching feature is something they have shoehorned into their fakeraid driver.  As such, it isn't going to work under Linux.

---

### Post by profozone on 2011-05-19
Yeah, I figured as much.  But it wouldn't have to for me, since the whole linux OS will be on the SSD.  It shouldn't need any bump in speed.

This will be my first SSD.  I hope it's as fast as people say.  Reviews seem to indicate that programs open as if they were merely minimized.  If I knew that, I would have splurged earlier.

Keeping my fingers crossed.

---

### Post by tobestool on 2011-10-19
Hi,

I've just seen your thread after starting my own. Did you end up using your SSD for both your Linux install and the SRT cache area under Windows? I'm having a lot of trouble getting any flavour of Linux to recognize the remaining space on the SSD once I've enabled SRT. Would be interested in your experiences if you've made it work.

Thanks.

---

