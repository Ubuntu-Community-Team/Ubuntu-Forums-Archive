---
title: "Problems with partitions"
date: 2011-04-25
forum: General Help
---

### Post by Quade97 on 2011-04-25
This isn't exactly an Ubuntu problem, but the people here are extremely computer literate and I hope they can help. 

I have 4 partitions on my hard drive. HFS+ , Ubuntu, Ubuntu Swap Area, and free space. I am trying to use the free space to install Windows Vista, But when the installer creates a partition from the free space it says "Windows cannot find a system volume that fits the criteria for installation".  I have tried using Ubuntu's helpful Disk Utility to create an NTFS partition for Windows but it still will not accept it. 

If this is an in appropriate question for these forums, please redirect me to a site that may be able to help.

Help would be extremely appreciated because Mac and Ubuntu don't exactly meet all the needs I have for my computer :)

---

### Post by coffeecat on 2011-04-25
I can think of two reasons why Vista is not happy with the NTFS partition you have created for it.

Either...

You have a GUID partition table (GPT) with a BIOS machine. Vista can only boot from a GPT disc on an EFI machine.

Or...

You have a conventional mbr partition table, but the free space is inside an already created extended partition. Which would mean that any partition you create will be a logical partition. Windows cannot boot from a logical partition. The only way you can have Windows C: in a logical partition is if you create a primary partition for its boot files. If you are presenting the Windows installer with a logical NTFS partition and nowhere for it to create a primary partition, it will refuse to co-operate.

By the way, I know you are not asking for help with your Mac partition in this thread, but the forum CoC disallows anyone from helping with a Hackintosh question. For your information.

---

### Post by Quade97 on 2011-04-25
Oops, Trying not to get in trouble, let me just remove that part and list it as HFS+ :P. I was a little nervous about putting that part but I thought it might be important in some way, such as the GUID Partition table thing you said, Even though Mac doesn't even have GUID as a default.

Okay well it is Master Boot Record partition table. I somewhat understand what you mean about the logical partition thing. But Ubuntu Disk Utility and Windows and Mac saw it as free space, Wouldn't it list it as extended or some sort of a partition?

Also I was thinking about using an XP Installer and jumping up to Vista using upgrade because XP Installer usually isn't as strange, but doesn't it usually try to format the whole HDD? 

Thanks :)

---

### Post by coffeecat on 2011-04-25
OK. Boot into Ubuntu and post the output of:

```
sudo fdisk -lu
```Then we can see what your partition layout is like.

A word or two of warning if you use the XP or Vista installer in the presence of logical partitions. XP = [Be afraid!]("http://ubuntuforums.org/showpost.php?p=10468958&postcount=42"). Vista = [Be very afraid!]("http://ubuntuforums.org/showpost.php?p=10470071&postcount=44") :-s

**EDIT**:

> **Quade97 said:**
> Also I was thinking about using an XP Installer  and jumping up to Vista using upgrade because XP Installer usually isn't  as strange, but doesn't it usually try to format the whole HDD?  

Not necessarily. The XP installer can use a pre-prepared partition or use less than the whole drive - when it's not busy corrupting the partition table, that is. :wink:

---

### Post by Quade97 on 2011-04-25
This is everything it said minus my External HDD, I took that part out (/dev/sdb right?) And I didn't realize I had 6 Partitions. Partition 3 should be the one I'm attempting to install Windows on. Not sure why it's currently FAT16. 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3fb2c97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488648790   244324364   af  HFS / HFS+
/dev/sda2       488650750   521850879    16600065    5  Extended
/dev/sda3       521850880   976771071   227460096    6  FAT16
/dev/sda5       488650752   517945343    14647296   83  Linux
/dev/sda6       517947392   521850879     1951744   82  Linux swap / Solaris

I'm unsure of where the extended volume came from, it shows up in Disk Utility as 17gb. But now the free space I had in Disk Utility appears as "Unknown 233gb"

Wait.... Couldn't Vista be freaking out because I have 5 partitions?

And a random question....What's up with /dev/sda4, its not there... Not saying I ever made one but why the skip? Possible that it might not be reading a part of my HDD? Location for GRUB Boot Loader? I did install the HFS+ Volume first, then Ubuntu which should have created two partitions.

---

### Post by coffeecat on 2011-04-25
It's best if you use code tags for terminal output. You get to preserve the formatting that way, making it readable. Here's your output for sda:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa3fb2c97

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488648790   244324364   af  HFS / HFS+
/dev/sda2       488650750   521850879    16600065    5  Extended
/dev/sda3       521850880   976771071   227460096    6  FAT16
/dev/sda5       488650752   517945343    14647296   83  Linux
/dev/sda6       517947392   521850879     1951744   82  Linux swap / Solaris
```The logical partitions sda5 and sda6 are inside the extended partition sda2, and the primary partition sda3 comes after sda2/5/6. Sizes are:

sda1 - 250GB
sda2 - 17GB, containing:
   -   sda5 - 15GB
   -   sda6 - 2GB
sda3 - 232GB

If the free space was where sda3 is now, you would have been able to make a primary partition, so perhaps the Windows installer didn't like a primary partition coming physically after an extended partition with logicals. Partition sda3 is formatted FAT16 at the moment which wouldn't do at all for Vista. Are you sure it was formatted NTFS when Vista rejected it?

Your sdb has a GUID partition table (I knew there would be one somewhere :wink:) which fdisk doesn't support. But I don't think that's relevant to your Windows installing problem.

I must log off now, but I'll check up on this thread in the morning.

---

### Post by Quade97 on 2011-04-25
Thank you, And I'm pretty sure I had it formatted to NTFS, I also attempted leaving it as empty space. But I suppose I'll try it again. And yeah tags... I'll remember that next time (hopefully :) )

---

### Post by coffeecat on 2011-04-25
You did a bit of editing while I was posting.

> **Quade97 said:**
> I'm unsure of where the extended volume came from, it shows up in Disk Utility as 17gb. But now the free space I had in Disk Utility appears as "Unknown 233gb"

The FAT16 label in fdisk and "unknown" in Disk Utility could be because the partition table has an ID for FAT16, but the partition itself may not have a valid filesystem.

> **Quade97 said:**
>  Wait.... Couldn't Vista be freaking out because I have 5 partitions?

No - two are logicals inside an extended - that's quite in order.

> **Quade97 said:**
>  And a random question....What's up with /dev/sda4, its not there... Not saying I ever made one but why the skip? Possible that it might not be reading a part of my HDD? 

That's not a problem. Primary partitions (and extended, which are simply special primaries used as containers for logicals) are numbered 1-4. Logicals are numbered 5 and upward. You have a spare partition #4 "slot". That's quite OK.

A link for you:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

That tells you most of what you need to know about partitions. Also - it tells you how to use Gparted. I suggest you install Gparted which is much more flexible than Disk Utility. DU is fine for simple jobs - confusing when things get more complicated.

---

### Post by Quade97 on 2011-04-25
Hm, Okay, Thank you. Maybe I should try that program, Disk Utility gave me an error while attempting to format the "unknown" /dev/sda3

Gparted worked much better, Thank you. Now I will attempt to install Vista yet again...

Didn't work. Same message as before. Uhg... Wouldn't the world be a better place if Windows was recognized as the worst of the three main operating systems that exist? I mean really....Linux is way better and its free, How did Windows get to be the most accepted Operating System? Wasn't Unix first?...

---

### Post by srs5694 on 2011-04-25
What version of Windows are you trying to install? That detail could be critically important.

I've just tried to reproduce your problem, using the fdisk output you posted as a model. (I used a much smaller virtual disk in VirtualBox, so if there's some quirk of the specific partition sizes or start locations that's an issue, my test would have missed that.) Neither Windows XP 32-bit nor Windows 7 64-bit seemed to have a problem, although I didn't proceed far beyond the partition-selection stage with either of them. My best guess is that the Windows installer is looking at /dev/sda3, seeing something there it doesn't like, and flaking out. You could try blanking the first 1 MiB of the partition with:

```

sudo dd if=/dev/zero of=/dev/sda3 bs=1024 count=1024

```

The choice to blank the first 1 MiB is somewhat arbitrary, since I don't know where critical NTFS data structures reside. If that doesn't work, try increasing the count value, or omit it entirely to blank the whole partition.

---

### Post by Quade97 on 2011-04-25
Thank you for your effort. I had included that I was installing Windows Vista, The version of Vista should not even matter though, because it won't even get to the file transfer. I had erased the partition multiple times using Ubuntu Disk Manager and Gpart, formatting it to NTFS, FAT, and leaving it as blank space. As far as I can see there is absolutely no reason vista should be rejecting the partition. The only strange thing I did see is that it shows up as Partition 4 instead of 3 but that isn't really strange because it reads everything before it, the HFS+ volume, the Ubuntu partition and the swap area.

---

### Post by Quackers on 2011-04-25
Could you post a screenshot of the gparted screen from the live cd desktop please?

---

### Post by Quade97 on 2011-04-25
Eh... I suppose that would help I have given almost all information on it though.

---

### Post by Quackers on 2011-04-25
It's just for confirmation of where the "free space" is.
Sometimes "free space" is a term used when the space is within an extended partition. Unallocated space is when the space is not in a partition.

---

### Post by Quade97 on 2011-04-25
This is the GParted screen... If the picture would work... 

Uhg...It keeps saying broken image or something... Heres the link :\ 

[http://img163.imageshack.us/i/screenshotcbm.png/](http://img163.imageshack.us/i/screenshotcbm.png/)

Right now the "Free Space" is the NTFS Partition. I do understand the difference between free space on the HDD itself and within a partition.
[IMG]http://img7.imageshack.us/i/screenshotcyb.png/[/IMG]

---

### Post by Quackers on 2011-04-25
I can't make out the details. It won't enlarge.

---

### Post by Quade97 on 2011-04-25
Uhg.... What exactly do you need to know I can just tell you...

---

### Post by Quackers on 2011-04-25
What designation does this NTFS partition have? /dev/sda?

---

### Post by Quade97 on 2011-04-25
I know that it is /dev/sda3

---

### Post by Quackers on 2011-04-25
Ok thanks. So this is the partition that used to be formatted FAT16.

How old is this pc please and in particular its bios? When looking in your bios in the past have you seen anything regarding Large Disk settings?

---

### Post by Quade97 on 2011-04-25
This is a fairly new laptop. It doesn't have anything like that listed in the BIOS. It is a Dell Latitude D630. I have had Windows Vista installed before, It has a SATA Hard Drive, DDR2 RAM, GMA x3100 graphics card. Just to give you an idea of how new it is. Its probably a 2007 laptop, Can't be entirely sure though, let me look that up...

---

### Post by Quackers on 2011-04-25
Thanks. It is unlikely that the bios has a 137GB hard drive limit. Some older ones do. This means that boot files installed further into the disc than 137GB cannot be read.

---

### Post by Quade97 on 2011-04-25
Interesting fact, I'll remember that one for other things. Now onto why windows doesn't like my partition :(

---

### Post by Quackers on 2011-04-25
Sadly I can't explain it :-( (assuming that there is no bios limit on the HDD size).
When you had Vista running earlier, was it on the first partition of the drive?

---

### Post by Quade97 on 2011-04-25
Yes, I believe it was.

---

### Post by Quackers on 2011-04-25
Just a suggestion. Try moving the boot flag to sda3 with gparted (right-click the partition, select "manage flags" then tick the "boot" box) and see if the Windows installer then recognises the partition.

---

### Post by Quade97 on 2011-04-25
It recognizes the partition, I click on it and select next like normal, then it gives me the "Windows cannot find a system volume that meets the criteria for installation." And I actually already tried making it bootable, it didn't work.

---

### Post by Quackers on 2011-04-25
I meant recognises the partition, as in "meeting the criteria for installation". Obviously if you've tried that it's a moot point. As it happens Windows won't boot without the boot flag on its partition (not that it matters if you can't install it).

---

### Post by Quade97 on 2011-04-25
Well I suppose my only other option is to format everything and see if it will work then. I'll do that tomorrow (I live in the US not the UK, just saying), Thank you for trying. I always love the Ubuntu forums because the people are nice and always reply with the best answers you can get quickly. :)

---

### Post by Quackers on 2011-04-25
Sorry I can't help further. I suspect it will work again if it's in the first partition - maybe :-)
What do you mean? It's 4am here :-)

---

### Post by Quade97 on 2011-04-25
And, that's what I meant, it was 11 when you replied to that lol. I just checked back one more time because I need to do something on Ubuntu real quick :D

I hope to become a more active member in the future because Ubuntu is one of the most useful operating systems there are, and I want to learn more about it. Ironically I was just getting deeper into Windows, like running it completely from a command prompt... Then I wanted to use Ubuntu and Mac OS X more now I'm trying to get a Mac Book 1st Generation but even those cost around $400 usually. 

I know you're not supposed to HELP with Hackintoshes but I'm just saying. I want a Mac Book because its easier to run Windows on Mac than it is to run Mac on a PC. XD

---

### Post by Quackers on 2011-04-25
Sleep well :-)

---

### Post by Quade97 on 2011-04-25
Hopefully you'll be sleeping soon too. And if not then... Have a nice day :P

---

### Post by srs5694 on 2011-04-26
Sorry about missing that you were on Vista. It was mentioned several times; I must go for an eye exam! ;)

I'm mystified. The only thing I can think of that might be causing this problem is if the computer was based on EFI rather than BIOS. In that case, Windows would insist on installing to a GUID Partition Table (GPT) disk rather than the Master Boot Record (MBR) disk you've got. Although EFI-based systems are starting to become available, your laptop is old enough that it's not likely to be EFI-based. You wouldn't happen to be using a boot loader like UEFI DUET or XPC, would you? If you were using such a boot loader, Windows would think it was on an EFI-based system. You might also want to check your BIOS options; if you've got any options about EFI or UEFI boot mode, it could be you've got an EFI-capable BIOS set to EFI mode. In that case, post back with the details.

Assuming you've got a conventional BIOS-based computer, instead of completely wiping everything, I have a suggestion that might enable you to save your existing Ubuntu installation and whatever's on the HFS partition:


[list=1]
[*]Back up all your important data from this disk.
[*]In Ubuntu or an emergency disk, type "sudo sfdisk -d /dev/sda > parts.txt". This saves your partition table to parts.txt.
[*]Copy parts.txt to a floppy disk, USB flash drive, CD-R, or some other convenient removable medium.
[*]Type "sudo fdisk /dev/sda" to edit the partition table. Note: Use fdisk for this, *not* GParted or parted!
[*]In fdisk, use the "d" option to delete your partitions 6, 5, 2, and 1, in that order.
[*]In fdisk, type "n" to create a new partition. Use the default start and end points.
[*]In fdisk, type "p" to view the partition table. It should now have two partitions: A Linux partition at the start of the disk and an NTFS or FAT partition at the end. There should be very little space between them. The idea is that the "Linux partition" is now serving as a protective partition to keep all your data safe from damage by the Windows installer. If you see something else, type "q" and start over again with fdisk. With any luck the installer won't be as flustered by this new and simpler setup than it is by your old one.
[*]In fdisk, type "w" to write your changes to disk.
[*]Reboot into the Windows installer. With luck, it will now install to the Windows partition. If not, this procedure has failed. You can continue in order to recover the rest of your partitions or you can quit, wipe the disk, install Windows, and restore your original data in new partitions.
[*]After installing Windows, reboot into an emergency disk, such as the Ubuntu installer in "live CD" mode.
[*]Insert whatever medium has the parts.txt file you created earlier and copy it to your current directory.
[*]Type "sudo sfdisk -f /dev/sda < parts.txt". This will restore your original partition table to the disk, restoring your original partitions.
[*]Type "sudo fdisk /dev/sda".
[*]In fdisk, type "p" to view the partitions. If /dev/sda3 has type "7" (in the "Id" column), you can quit now by typing "q" and skip the next two steps.
[*]In fdisk, type "t" to change a partition type. In response to the prompts, tell it to alter partition #3 and to change the type code to "7".
[*]In fdisk, type "w" to save your changes.
[*]Re-install GRUB. There are several ways to do this. Personally, I'd boot with [Super GRUB 2 Disk](http://www.supergrubdisk.org/) and type "sudo grub-install /dev/sda". It can be done from the Ubuntu install disc, but I don't recall the precise instructions.
[/list]


With any luck, this will enable everything to boot; however, I can't guarantee that. It's probably worth trying this just to avoid the hassle of re-installing Ubuntu, but you might have to rely on those backups in the end.

---

### Post by srs5694 on 2011-04-26
Another thought has occurred to me: Do you have another disk in the computer? If so, it's conceivable that the Windows installer is seeing that other disk but not the one you intend to install to. If so, you'll be able to repartition /dev/sda until the cows come home and it won't make any difference. Such problems can occur if the motherboard has two hard disk controllers and the Windows install disc has drivers for just one of those controllers. Moving the cables around can correct the problem, as can telling the Windows installer about drivers for the second motherboard disk controller (there's a prompt for that at some point during the installation).

---

