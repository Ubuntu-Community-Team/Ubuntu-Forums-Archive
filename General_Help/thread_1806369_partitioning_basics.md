---
title: "partitioning basics"
date: 2011-07-17
forum: General Help
---

### Post by pdlethbridge on 2011-07-17
I think I'm closer to being able to run several ubuntus.It wants another partition before the swap file I think Should this be for the boot loader. I have  10.04 on the first partition.My next is the extended. I  guess that would be the boot loader on its own partition. of about 1-2 gig. right after the first partition. and then make the rest a extended with a swap and home. as the first logical partitions This is almost getting to be fun. Like fly fishing and catching a trout on a fly you tied.

---

### Post by oldfred on 2011-07-17
I do not like separate /boot partitions as you have to have one for every install also. Only if a server, RAID or LVM partitioning should you consider a separate /boot. 

With multiple installs I like to share my data, but you should not share /home as it has all your hidden user settings which may not be compatible across installs. So I create /data for sharing my Ubuntu installs and /shared (NTFS) for sharing with my XP.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition]("http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition")

I also prefer gpt is the drive will never have windows installed or will be used with UEFI in the future.

---

### Post by pdlethbridge on 2011-07-17
Well I do't use any windoz software and really don't intend on going beyond ubuntu or kubuntu. I have the kubuntu desktop loaded on my 10.04 install so its like having 2 Oses on the first partition'
My intent is to be able to test new ubuntu sofr ware and I would like to keep it separated fro the rest of the programs

---

### Post by ajgreeny on 2011-07-17
WOW!!  That's an unnecessarily complicated partitioning setup, in my opinion, and you do not appear to have a separate /boot partition, though perhaps I misunderstood what you meant in your original post.

There is absolutely no problem running as many different ubuntu versions as you want, ubuntu, kubuntu, xubuntu, lubuntu, etc etc with different distro numbers as well, if you want, ie 10.04, 10.10, 11.04 and even 11.10 if you're adventurous, but I agree with oldfred, keep the /home for each distro separate from the others as you may find problems if you don't, even in the same numbered distros.

I would advise you to either make a separate /data partition and mount it at boot in all distros, or do what I do; keep one main distro for your working use, and have a separate /home partition for that, with all your data files and the config for only that distro in it.

For all the other distros you want to try, leave /home within the root partition, then mount the /home partition of your main distro with /etc/fstab, and link all your data files from there to the /home folder of your second, third and so on, distros.

---

### Post by oldfred on 2011-07-17
I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

The actual user settings are small. My /home is 1GB with about 3/4 of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

Opposing viewpoint on separate data partitions - post14 srs5694:
[http://ubuntuforums.org/showthread.php?t=1738065](http://ubuntuforums.org/showthread.php?t=1738065)
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Another way to share:
kansasnoob's sharing and Morbius1 use of bindfs
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)
HowTo: Create shared directory for local users (with bindfs).
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472)

---

### Post by pdlethbridge on 2011-07-17
after doing much reading it appears that partitioning is like buy a new car. Lots of bells and whistles. and thats what the sails-man wants you to buy. It looks like what I'll do next is move the swap file to the second partition space and make the third partition a extended  with lots of logicals and free space. Unless there is more to be said I'll give that a try tomorrow. Hey all I can do is screw it up again. I won't be touching 10.04 on the first partition.
As 10.04 has its own home, etc, sys, bin, and usr folder. I also have all my stuff backed up on cds if I need them but I just use ubuntu one

---

### Post by Blasphemist on 2011-07-17
In my opinion, you should have the space in sda3 and sda4 in the extended partition and not as primary's. I also don't create a separate boot partition. I also recommend labeling your partitions. I also wouldn't be so sure that you'll never want to have other disto's. I have a bunch now after having just windows 7 and ubuntu. Now look at all I have. And if you do as recommended and use a partition or two for shared data, you'll find the distro partitions only need to be around 10GB. Lastly, I find I keep changing my distro mix. I try a beta or alpha or unusual distro, then decide to change that to something different frequently.

---

### Post by srs5694 on 2011-07-17
> **pdlethbridge said:**
> I think I'm closer to being able to run several ubuntus.It wants another partition before the swap file I think

Linux doesn't care about the relative positions of partitions -- you can put swap before, after, or between your other partitions. There are, however, performance implications for partition placement, and there are also rules in the Master Boot Record (MBR) partitioning system you're using (see below) that can affect where you can place partitions.

> Should this be for the boot loader.

On MBR disks, the boot loader seldom gets its own partition, although there are exceptions to this rule.

On GUID Partition Table (GPT) disks used on BIOS-based computers with GRUB, it's best to have a separate GRUB partition, known as the BIOS Boot Partition. You don't have this type of configuration, though, since your disk is clearly an MBR disk, not a GPT disk.

> I have  10.04 on the first partition.My next is the extended. I  guess that would be the boot loader on its own partition. of about 1-2 gig.

It would be helpful if you punctuated and capitalized your sentences conventionally. It was hard for me to follow your message because of the odd punctuation, and I'm not entirely sure I parsed it correctly.

The extended partition is a container for logical partitions. Look at your screen shot closely. The extended partition's container status is indicated in GParted in several ways:


[list]
[*]In the graphical list at the top, the extended partition is a pale blue outline that surrounds several other partitions.
[*]In the detail list, the extended partition has a little expand/contract triangle to its left; you can click that to hide its contents (namely, your logical partitions).
[*]In the detail list, the logical partitions are indented relative to the extended partition that immediately precedes them in the list.
[/list]


The MBR system is limited to four primary partitions, one of which can be an extended partition that can contain an effectively arbitrary number of logical partitions. Given your current partition layout, you can't easily add more partitions because you've already got four primary partitions and because your extended partition is sandwiched between primary partitions and therefore cannot be expanded into the free space. Thus, to fully utilize your available disk space, you have a few options:


[list]
[*]You can expand /dev/sda4 into the available free space. Whether this makes any sense or not I cannot say because I don't know what that partition is being used for.
[*]You can delete /dev/sda4 and expand /dev/sda3. Again, whether this makes sense depends on how you're using those partitions.
[*]You can delete /dev/sda3 and /dev/sda4, expand /dev/sda2 (your extended partition), and either add more logical partitions or expand the ones you've got.
[*]You can move /dev/sda3 and /dev/sda4 to the end of the disk, expand /dev/sda2, and add more logical partitions or expand the ones you've got.
[*]You can try to convert the primary/logical status of your partitions using [FixParts](http://www.rodsbooks.com/fixparts/) or perhaps a Windows utility; however, I can't guarantee you'll be able to do this, at least not without resizing some partitions.
[*]You can delete everything and start over from scratch.
[*]You can do minor variants or combinations of the above things.
[*]You can use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert the disk from MBR to GPT form. Since GPT doesn't make the primary/extended/logical distinction, these problems go away with GPT. Doing this, however, will require re-installing GRUB, and creating a BIOS Boot Partition is advisable. This may also limit your future options should you want to dual-boot with Windows, since Windows can boot from GPT only on UEFI-based computers.
[*]You can delete everything, create a new GPT layout, and start fresh with GPT.
[/list]


[quote=oldfred]With multiple installs I like to share my data, but you should not share  /home as it has all your hidden user settings which may not be  compatible across installs. So I create /data for sharing my Ubuntu  installs and /shared (NTFS) for sharing with my XP.[/quote]

Sharing /home across Linux distributions is perfectly OK *if* you use different user home directories in each. That is, you might use /home/paulu for Ubuntu, /home/paulf for Fedora, and so on. It's *these* directories, not /home per se, that hold users' data and configuration files. There are numerous ways to use different home directories for each distribution. The simplest is to use different usernames in each distribution, but there are ways to do it that use the same username in each distribution but different home directories. IMHO, using a single /home with separate user home directories in it is better than using a separate data partition since the standard way to do things in Linux is to put user data in subdirectories of /home. Using a separate data partition does work, but it's re-inventing the wheel and it's a Windows-style solution rather than a Linux-style solution.

---

### Post by ssreddy555 on 2011-07-18
I quad boot with win 7 on the primary partition & mint 10, ubuntu 11.04 & mint 11 on different logical partitions within an extended partition.

Is it necessary that I should have swap partitions at the end of each logical partition or is it enough to have one common swap partition?

---

### Post by Blasphemist on 2011-07-18
You only need one swap partition for all of your distros to use. I told each distro at install to use my one swap and even let the install format it each time. It seems like one complained when it couldn't format it. I don't really know for sure that it was required that I tell the install to use that swap but it seemed the safest to do. I do that again each time I install a distro. I had 2 like you do from installs where I didn't do the partitioning. I deleted one and made the one I use be at the end of the disk just for later partition sizing considerations.

---

### Post by srs5694 on 2011-07-18
> **Blasphemist said:**
> You only need one swap partition for all of your distros to use.

This is correct, but there is one caveat: If you use a distribution's suspend-to-disk feature, it saves its current memory in swap and then restores it from swap when you wake the computer up. Thus, if you share swap space and also use suspend-to-disk, you could run into problems with your suspended state being lost if you suspend and then switch to a different distribution.

---

### Post by FormatSeize on 2011-07-18
> **oldfred said:**
> LVM partitioning. 
Is there a very, very basic guide on what the heck is going on with a LVM partition and how to work with them? They're such a pain because they refuse to acknowledge or be acknowledged by normal partitions. When you boot from the hard disk that they live on, it pretends like nothing else is there. Then, if you can boot into another OS on that disk from a USB, you can't mount it because it goes and makes itself unrecognizable somehow. 
 
Is there some good reason to causing people that want to dual boot such grief?

---

### Post by Blasphemist on 2011-07-18
I'm not sure I understand. Normally people don't use LVM at a pc level where dual boot is in use. It is an option though.

> LVM allows you to create logical volumes out of the physical storage resources on your machine. However, unlike physical volumes, the logical volumes can be expanded and shrunk while the system is still running, providing Linux system administrators with the storage flexibility that they've until now only dreamed of.

Maybe it will help to read this. [http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)

---

### Post by pdlethbridge on 2011-07-18
I partitioned again last night how does this look

---

### Post by dabl on 2011-07-18
With 4 primary partitions defined, and the remaining unallocated space falling after the last primary partition, you're a little stuck with this layout -- the only way you will ever be able to use that final unallocated space is to expand /dev/sda4 to consume it.  Maybe that's OK.

However, if you _moved_ the /dev/sda4 partition all the way to the right, and then moved the /dev/sda3 partition to the right until it is up against /dev/sda4, then you could use your unallocated space in the future for additional logical partitions under /dev/sda2.  That's probably the desirable way to arrange it.

---

### Post by pdlethbridge on 2011-07-18
this is my new set up. partitions 1,2 an3 are used as follow
1 is 10.04 Lts with kubuntu desk top installed, #2 is the swap are and 3 is extended the rest are logical or unused. I hope this will work I don't ever plane to go back to windoze

---

### Post by Blasphemist on 2011-07-18
That's all good except your swap is way to big. I'd create a swap in the unused in the extended partition of a bit bigger than the amount of memory you have. Then change the existing swap to a different type or delete it and expand the extended partition to include that space. You'll need to boot to installation media to do this so the swap isn't mounted.

Sound good?

---

### Post by pdlethbridge on 2011-07-18
My bad its supposed to be only 3 gig.  I found that during the partitioning process 10.04 would cause problems like not allowing a delete or change Even though my default is 10.04 I used my 9.o4 cd for formating off the live CD. It worked better than expected and now. I'm up and running 10.04. Using cloud it was easy to restore every thing. If I add more memory then the 4 gigs will be fine Im not goimg through the hassle of changing what I have

---

### Post by ssreddy555 on 2011-07-18
> **Blasphemist said:**
> You only need one swap partition for all of your distros to use. I told each distro at install to use my one swap and even let the install format it each time. It seems like one complained when it couldn't format it. I don't really know for sure that it was required that I tell the install to use that swap but it seemed the safest to do. I do that again each time I install a distro. I had 2 like you do from installs where I didn't do the partitioning. I deleted one and made the one I use be at the end of the disk just for later partition sizing considerations.

How to "tell" each distro to use a common swap?

While installing, I simply made one Ext 4 partition & a Swap partition & installed the OS in Ext 4.

As I can see from the attached GParted screenshot, Mint 64 is using both the Swaps.

---

### Post by Blasphemist on 2011-07-18
> **ssreddy555 said:**
> How to "tell" each distro to use a common swap?

While installing, I simply made one Ext 4 partition & a Swap partition & installed the OS in Ext 4.

As I can see from the attached GParted screenshot, Mint 64 is using both the Swaps.

I don't see a screenshot with this. If you right click on each swap, does one not have swap on as an option and the other swap off?

---

### Post by pdlethbridge on 2011-07-18
I tried to install 9.04 but when I got to the partitioning of the setup it didn't see or show that the first partition was / so I exited the set up

---

### Post by Blasphemist on 2011-07-18
I'm not sure I understand. When you are choosing the partition during the installation, you choose to edit the partition and set it's mount point as /. You also set it's file system (normally EXT4 for linux) and whether or not to format the partition. I haven't installed 9.04 in ages so I don't remember just how it looks but that is how the last few versions have gone.

---

### Post by srs5694 on 2011-07-18
> **pdlethbridge said:**
> I tried to install 9.04 but when I got to the partitioning of the setup it didn't see or show that the first partition was / so I exited the set up

[quote=Blasphemist]I'm not sure I understand. When you are choosing the partition during  the installation, you choose to edit the partition and set it's mount  point as /. You also set it's file system (normally EXT4 for linux) and  whether or not to format the partition. I haven't installed 9.04 in ages  so I don't remember just how it looks but that is how the last few  versions have gone. 	[/quote]

To elaborate a bit, the assignment of partitions to mount points (e.g., /dev/sda2 is /, /dev/sda5 is /home, etc.) is something that's *not* part of the partition table; it's done by Linux, as set in its /etc/fstab file. Thus, when you install Linux, the partition setup tools may not know how an existing installation set things up; you may have to specify the mapping manually. (Sometimes the installer can figure this out, but usually they only attempt it if you select an option to upgrade an existing installation.)

---

### Post by Blasphemist on 2011-07-18
On the current ubuntu versions during install there is an allocate disk space step. At that step instead of choosing to install alongside existing os's, use whole disk or upgrade existing installation in some cases, you can choose an option called "something else". Selecting "something else" shows the partition table as it exists at that time. I created and sized my partitions ahead of time. I select the partition that I want to use and choose edit. I can then select the mount point, file system and whether or not to format the partition.

---

### Post by pdlethbridge on 2011-07-18
It sounds to me like they are trying to make partitioning easier. My final install of 9.04 screwed up 10.04 so Ill give it a rest for a few days. I've been labeled the nursing home geek, but this partitioning has me still baffled

---

### Post by FormatSeize on 2011-07-19
> **Blasphemist said:**
> I'm not sure I understand. Normally people don't use LVM at a pc level where dual boot is in use. It is an option though.

Fedora forces me to use LVM at te PC level. I can't find an option anywhere to use anything else. Then it sits there an rules the hard drive, not letting anything else boot if I am booting from the hard disk.

---

### Post by Blasphemist on 2011-07-19
> **FormatSeize said:**
> Fedora forces me to use LVM at te PC level. I can't find an option anywhere to use anything else. Then it sits there an rules the hard drive, not letting anything else boot if I am booting from the hard disk.

Hmm... I have 5 flavors of ubuntu, fedora 15 and openSUSE installed on this laptop right now. I can boot all of them and I don't use LVM. I really don't remember just what was different in the Fedora 15 install from the others. I did have all my partitions already made and so as I install each I make sure that I choose the desired partition, its partition type and the mount point /. They all share a swap partition.

---

### Post by pdlethbridge on 2011-07-19
Well now that the partitioning is done it's time to install something in one of those free spaces. without toasting 10.04 in the first partition. Getting all the kids ( OSES)  to play nice together is what I want
 When I added 9.04 to SDA5 it screwed up 10.04 in SDA1

---

### Post by ajgreeny on 2011-07-19
> **FormatSeize said:**
> Fedora forces me to use LVM at te PC level. I can't find an option anywhere to use anything else. Then it sits there an rules the hard drive, not letting anything else boot if I am booting from the hard disk.
No it doesn't!

It is a long while since I installed a Fedora distro, but you can choose to manually partition the disk, setting root, home and swap, if needed, to the size you want and overcome this LVM problem very easily.

Don't simply accept the defaults, or LVM is what you will get, and as you see, that makes life difficult for other non LVM distros on the same machine.

---

### Post by Blasphemist on 2011-07-19
> **pdlethbridge said:**
> Well now that the partitioning is done it's time to install something in one of those free spaces. without toasting 10.04 in the first partition. Getting all the kids ( OSES)  to play nice together is what I want
 When I added 9.04 to SDA5 it screwed up 10.04 in SDA1

It sure looks like you installed to sda1 again as that seems to be the only partition used right now. Is it possible this isn't the screenshot you intended as it still has the big swap?

---

### Post by FormatSeize on 2011-07-19
> **ajgreeny said:**
> No it doesn't!
 
It is a long while since I installed a Fedora distro, but you can choose to manually partition the disk, setting root, home and swap, if needed, to the size you want and overcome this LVM problem very easily.
 
Don't simply accept the defaults, or LVM is what you will get, and as you see, that makes life difficult for other non LVM distros on the same machine.
:(
 
... still learning.
 
Frustrated from having to boot into other distros from a USB, I grabbed anything worthwhile from the Fedora partition, then deleted the partition. Later, I was planning on filling the space left by the partition with the other two distros on the disk, and put Fedora on another disk. I thought there was no way to get around the LVM madness.
 
Thanks!

---

### Post by pdlethbridge on 2011-07-20
its what I have but sda1 is only for 10.4 but 9.04 still gets in there to play and screw things up. Possible I'm mounting sd5 wrong because only some of the settings were changed in sda1 but 9.04 was there and it should not have been I wanted it on sda5 if I mount sda5 as /var or/user is this what I'm doing wrong I know I can put them side by side  on the same partition but thats not what I want

---

### Post by Blasphemist on 2011-07-20
> **pdlethbridge said:**
> its what I have but sda1 is only for 10.4 but 9.04 still gets in there to play and screw things up. Possible I'm mounting sd5 wrong because only some of the settings were changed in sda1 but 9.04 was there and it should not have been I wanted it on sda5 if I mount sda5 as /var or/user is this what I'm doing wrong I know I can put them side by side  on the same partition but thats not what I want

You are only showing sda1 as in use and it's mount point is / (root). The others don't have anything on them. When you install, at the allocate disk space screen choose "something else". That is what is on the current release but it may be termed "manual" on the older versions. I don't remember. This will let you choose the partition to install to. Just keep it simple and set the mount point for that install on the desired partition as /. Give the partition a label if you have the option so it's clear what you installed where.

---

### Post by pdlethbridge on 2011-07-20
the partitions haven't changed 10.04 is stil onsda1 but when I tryed to put 9.04 od sda5 it went crazy as it wanted a mounting point and I gave it /us or /dev thats when things went bang!

---

### Post by pdlethbridge on 2011-07-20
the partitions haven't changed 10.04 is still on sda1 but when I tried to put 9.04 on sda5 it went crazy as it wanted a mounting point and I gave it /use or /dev thats when things went bang! I down loaded another partition manager and thats what the second attachment is showing The back ground picture is an Alaskan volcano

---

### Post by pdlethbridge on 2011-07-20
It seems easier to put Ubuntu and windoz together than 2 ubuntus. That should not be the case

---

### Post by srs5694 on 2011-07-20
> **pdlethbridge said:**
> the partitions haven't changed 10.04 is still on sda1 but when I tried to put 9.04 on sda5 it went crazy as it wanted a mounting point and I gave it /use or /dev thats when things went bang!

I think you fundamentally misunderstand what a mount point is. Every Linux installation has a partition (or other filesystem container, such as a logical volume in an LVM) that's given a mount point of "/" (pronounced "root"). Additional filesystem partitions are given other mount points, such as /home or /usr. Swap space isn't mounted.

If you have two Linux installations, then *each one* has *its own* root (/) partition. Thus, /dev/sda1 might be root (/) for Ubuntu 9.04 and /dev/sda5 might be root (/) for Ubuntu 11.04. If you wanted to access the 9.04 root (/) from the 11.04 installation, you'd give it a *different* mount point in the other installation -- say, /mnt/ubuntu904 or /u9 or /fred (it's arbitrary, really).

If, as it sounds like you did, you tried to assign a partition a mount point of /usr or /dev without also assigning a root (/) partition for that installation, you wouldn't be able to install. Without a root (/) partition defined, it's just not possible. It'd be like trying to build the second floor of a house without first building the first floor.

Remember, mount points are *not* inherent to the partition table or to the filesystems the partitions contain. They're assigned in the /etc/fstab file, by manual use of the mount command, or by other programs. There's nothing wrong with having two different root (/) partitions on one hard disk -- so long as they're root (/) partitions for *different installations*. If you want to share a partition for user data between installations, you can give it the same or a different mount point in the two installations, as you see fit.

---

### Post by pdlethbridge on 2011-07-20
so if I have / on
sda1 for 10.04 I can use / on sda5 for 9.04 I thought it wouldn't allow 2/ on the same drive. If Thats all that whats wrong then I receive the DAH AWARD THIS MONTH
 Final question Should I assign Root as I install now is it  just / or (/) I just tryed / and it would work.

---

### Post by srs5694 on 2011-07-20
You *must* assign root (/) as you install, otherwise the installer won't know where to put anything at all!

---

### Post by pdlethbridge on 2011-07-20
which  /  or (/)

---

### Post by pdlethbridge on 2011-07-20
my installer won't allow me to use two /  This is how my partitions are set up

---

### Post by Blasphemist on 2011-07-20
Remind me again please what distro you want to install. All ubuntu flavors, openSUSE, Fedora, etc., all that I have installed, have allowed me to choose the partition to install to if I make the right selections during the install. You should be able to install to sda5, sda6 and sda7 with a mount point of / for the distro you are installing at the time. Please try again and note your steps and then after a boot, run the bootinfoscript and post the results in code tags please. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by oldfred on 2011-07-20
Did you read post #37 by srs5694? 

I have many roots on my sdc drive, but you can only have one root per system and each needs to be in its own partition. When you start to have more than one system per drive you do have to keep track of which system is in control of the MBR and is the boot system and which partition every system is installed into.

---

### Post by pdlethbridge on 2011-07-21
I would like to keep it all ubuntu or kubuntu.I had the same problem last nigh, my 9.04 install trashed 10.04
Should I add a letter or number after /root
To keep it as simple as possible when I try an install I let the cd get to the desktop and I start it from there after answering the first 3 questions, language, key board timezone. the partition editor starts' I use the bottom button that is the advanced user to designate where I want to put the install. I don't use the automatic or side by side installs.
the next screen shows the partition and ask where the new Os should go  I choose the first or second logical after my swap fill marked it root/ with a letter n  after it and I had to remark sda1 as /. Then I went to the install screen. and then another bad install.Im going to keep after this until  it kills me

---

### Post by oldfred on 2011-07-21
When you say you marked it as root? Was this the label or the combo box that chooses the / partition.

I label each install like this so I can tell them apart.

```
/dev/sda1: LABEL="WinXP" UUID="04B05B70B05B6768" TYPE="ntfs" 
/dev/sda2: LABEL="backup" UUID="13a684e4-2849-4566-9528-21cd07028a9a" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: LABEL="SHARE" UUID="46CD-C9B2" TYPE="vfat" 
/dev/sdb2: LABEL="Maverick" UUID="0eea4e95-ea0a-4745-80d4-57bf2bbc9d69" TYPE="ext4" 
/dev/sdb3: TYPE="swap" 
/dev/sdb4: LABEL="MavData" UUID="431ba9e5-c72c-41c2-ba82-d8ee052336ff" TYPE="ext4" 
/dev/sdc1: LABEL="grub" UUID="9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc2: LABEL="Shared" UUID="44332FD360AA9657" TYPE="ntfs" 
/dev/sdc5: LABEL="Karmic" UUID="117412d5-2dbe-4011-8aec-ae310d1ee6c7" TYPE="ext4" 
/dev/sdc6: LABEL="Data" UUID="a55e6335-616f-4b10-9923-e963559f2b05" TYPE="ext3" 
/dev/sdc7: LABEL="LUCID" UUID="5e25282c-9c54-45df-9e79-514011e98648" TYPE="ext4" 
/dev/sdc8: LABEL="Test" UUID="af29c61a-34e9-48eb-9c94-afcb4bb61582" TYPE="ext4" 
/dev/sdc9: LABEL="OLDG" UUID="F6A6-705D" TYPE="vfat" 
/dev/sdc10: LABEL="newhome" UUID="b8a7e331-a716-4ac1-bf58-6ac515606c6d" TYPE="ext4" 
/dev/sdc11: UUID="09367687-86d1-4fd0-9b81-2787d3196159" TYPE="swap" 
/dev/sdc12: LABEL="Puppy" UUID="07e2a08d-37ca-4cf1-877b-f02b0eabcbca" TYPE="ext4" 
/dev/sdc13: LABEL="natty" UUID="318fd41e-4210-4960-a0d9-ee9b48388d69" TYPE="ext4" 
/dev/sdc14: UUID="5c703dd6-c2aa-4b09-a690-7d1cb88283a9" TYPE="ext4" 
/dev/sdc15: UUID="2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9" TYPE="swap" 
/dev/sdc16: UUID="63d146fd-1c63-4b31-95c5-ab52e2892283" TYPE="ext4" 
/dev/sdd1: LABEL="MC4GB" UUID="E489-24AF" TYPE="vfat" 

```

Now oldfred goes back to label sdac14 & c16. I forget which is oneiric.

---

### Post by pdlethbridge on 2011-07-21
I have never used the label box, my be thats the problem

---

### Post by Blasphemist on 2011-07-22
For each installation effort, you only need to touch the one partition that you are installing to. Do just as you've described to get to the partitioning but once there, the only partition you need to mess with is the partition you are installing to. Mark it as mount point of / and label it. You don't need to do anything else. You can also mark the partition to be formatted but that is more just good practice. Leave your already used partitions alone! Don't do anything with them. 

If prompted for where to write the boot image to, choose sda which should be the default. The parts of grub that go to the mbr will overwrite what is already there from previous installs but that is ok. Grub files will also get written to the /boot directory in the partition you are installing to. If you later want to change the installation that controls grub, you can reinstall grub from that partition. Don't worry about that now. Always wait until after all updates have been done to a new installation before you change grub. This ensures any kernel upgrades are done before that change but that is a whole other concern. 

You are very close, hang in there.

---

### Post by pdlethbridge on 2011-07-22
Well I'll give it another go But what should I do about the fact that when I give the new os root/ The rote has already disappeared from SDA1 my default OS Is that normal.

---

### Post by Blasphemist on 2011-07-22
When you are looking at the partitions in GParted it will only show one partition marked as root, the one you are using at that moment. Only one partition is root for the instance of linux you are running at that moment. Does that make sense?

---

### Post by pdlethbridge on 2011-07-22
Well Jim I finally have 2 OS's on the Machine and the both seem to be  working. You guys are great I think I'm on the right heading
Now a couple of associated questions . It booted to the default 10.04 which is a good thing but the mouse gave me some problems so I rebooted and the boot menu showed several versions of 10.04 including generic and I used the next option another generic and  recovery and several versions of 9.04. Is this usual or something I did. And should I always unmarked boot loader in the advanced button on the last page. On All OSes except the one on sda1

---

### Post by Blasphemist on 2011-07-22
> **pdlethbridge said:**
> Well Jim I finally have 2 OS's on the Machine and the both seem to be  working. You guys are great I think I'm on the right heading
Now a couple of associated questions . It booted to the default 10.04 which is a good thing but the mouse gave me some problems so I rebooted and the boot menu showed several versions of 10.04 including generic and I used the next option another generic and  recovery and several versions of 9.04. Is this usual or something I did. And should I always unmarked boot loader in the advanced button on the last page. On All OSes except the one on sda1

Sounds great! So just to be sure, are you good now or having mouse issues?

I'm still learning, from oldfred mostly as it turns out, about controlling what shows up in the grub menu. The answer to your question is that yes, without customization you will see multiple kernel version entries in the grub2 boot menu. When you run an update from update manager that includes a kernel update, a new kernel entry will show up with a corresponding recovery mode entry. Ideally you'll see an entry for previous versions that prevents them from all being listed. I can't remember right now what causes that sub-menu for the previous versions. 

Today, with oldfred's help I worked on implementing a method of specifying only the clearly worded distro name and the partition number in the grub2 menu. I like it a lot but I need to test my non debian distros and creating some documentation before I pass it on. 

For now it sounds like you are good but do let us know if that isn't right.

---

### Post by Blasphemist on 2011-07-22
Oh, I almost forgot your other question. Let's call whichever distro that was installed last the one that controls the grub configuration or grub controlling distro. I do believe that there may be distros that are best to not let install their boot loader but I don't know that for sure. I've seen that about Fedora but I don't know enough to say that for sure. I didn't have Fedora install it's boot loader but I really didn't know what I was doing at the time. I was just trying to keep things simple. 

For all of the debian distros at least, for now I go ahead and install the boot loader and update that distro to where it's current before I boot to another distro. This gets any kernel changes needed at the time done and ensures that partition can be standalone. Don't worry, that partitions grub2 will find the other distros and let you boot them. Then I boot my controlling distro, re-install grub2 and run update-grub to get my customizing back.

As I keep learning about that I intend to create and later post documentation.

---

### Post by pdlethbridge on 2011-07-22
This has been a big learning curve for me. It seems that you can disable the boot loader in 9,04 so that kept 10,04 as default also a fresh install of 10.04  cleared up the mouse problems an also change the double listigs of 10.04. I ll be getting some writable cds tomorrow so I'll try to add kubunt to the mix, I'll keep you guy informed of the latest good and bad news on this I'll also have screen shots I'm not sure if I  can do a boot screen shoot and if there is a screen shot you need let me know of the progress and answer any question

---

### Post by Blasphemist on 2011-07-22
> **pdlethbridge said:**
> This has been a big learning curve for me. It seems that you can disable the boot loader in 9,04 so that kept 10,04 as default also a fresh install of 10.04  cleared up the mouse problems an also change the double listigs of 10.04. I ll be getting some writable cds tomorrow so I'll try to add kubunt to the mix, I'll keep you guy informed of the latest good and bad news on this I'll also have screen shots I'm not sure if I  can do a boot screen shoot and if there is a screen shot you need let me know of the progress and answer any question

You can run the boot info script if there are issues and post the results. This link provides the script and how to use it. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It doesn't sound like you completely have your head around this yet but don't worry, very few do. I don't. I'm working on figuring out more tonight. Do post any questions or issues.

---

### Post by pdlethbridge on 2011-07-22
I think that we should see if this thread is good enough to join the stick club. The wisdom you guys have dealt out should be made available to the masse4s, Who really nows how to partition or get OSes installeded and working.I wanted to do this for a while but I couldn't get the answers I needed. I did lots of rerading but most of it related to it can be done not how it can be done. This thread is a how to, Any thought or ideas on this

---

### Post by ClientAlive on 2011-07-22
I only skimmed this thread so forgive if what mention has already been brought up.

pdlethbridge, when I read your original post one thing popped into my mind. I don't think it addresses your question exactly but it still may be worth mentioning. What occurred to me was that maybe the swap file is something that can be shared across all distros. After all you would only be running one at a time right? So no reason to have more than one swap.

Again, forgive me if I missed something and am just being redundant. Just wanted to share what came to mind.
---------------------

blasphemist, Hi. Good seeing you around.  :D

---

### Post by pdlethbridge on 2011-07-22
these were just taken and there really hasn't been any changes and yes the swap fill has been made smaller and it is going to be used by all ubuntu  distros. I have also made all partitions smaller, 30 gig rather than 60. They work just fine.
 on the final screen of the install right after the partition, there is an advanced button on the lower right clicking it will give you the choice of where to put the boot loader. In my case I was installing 9.04 but it gave me a list of places like sda1 which I choose which is my default Os 10,04

---

### Post by Blasphemist on 2011-07-22
You are getting very close to understanding it now. Look into what the mbr (google master boot record) is on a disk. When you are asked about where to right the boot loader, what is being asked is what disk's mbr should it go in. There are times when it could be written to a partition but that is a more advanced process that I still don't see a need for. There may be a good reason but for now you should just ignore writing it to anything other than the mbr.

So when you install it is fine to write the boot loader of more than one distro to the mbr of that drive. The grub of the last distro is what I call the controlling grub. Both OS's are fully independent but one grub is in control. I believe you have now achieved this. You have one in sda1 and one in sda5. You still have sda6 and sda7 available. 

You seem to have a good level of curiosity and willingness to learn but don't go to fast. When your OS's get kernel updates you will have questions. This is because of having one grub in control and happens more when you have more bleeding edge distro versions than you have now of course. If you haven't already, or even if you have started, I recommend you read the Grub 2 documentation and sites that discuss it. Here are a few to start with.

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)
[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html)
[http://ubuntuforums.org/showthread.php?p=10720322](http://ubuntuforums.org/showthread.php?p=10720322)
[http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html](http://ubuntu-install.blogspot.com/2009/11/grub2-title-tweaks.html)
[http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/](http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/)

---

### Post by ClientAlive on 2011-07-23
If it's of any use, here's a link to a page that talks very in depth about all this stuff. I came across it a couple days ago. It talks about the mbr and chain booting, grub, lilo, it even talks about bios and describes the entire process the computer goes through from hitting the power button to booted up.

[http://lennartb.home.xs4all.nl/bootloaders/node3.html](http://lennartb.home.xs4all.nl/bootloaders/node3.html)

HTH

---

### Post by pdlethbridge on 2011-07-23
I realize now why there are a couple of 10.04s in the boot loader, you mentioned kernal so if I added kubuntu desktop there would be another one. And I will take it slow. I have all ways been curious and it has got me into problems with computers

---

### Post by pdlethbridge on 2011-07-23
I plane on sticking to ubuntu for the short term, You mentioned cutting edge distros so I'm basically thinking in terms of the latest ubuntu. because the sda1 10.04 showed up in the advanced button just after I installed 9.04 as 10.04 would be the more cutting edge. then when I install 11.04 it will be the latest and greatest and inherit the boot loader?????:D:D
 And again I ask should this be made a stick. After I install 11.04

---

### Post by Blasphemist on 2011-07-23
Glad to hear your ready to add another ubuntu. 11.04 would be a good choice. When you install it choose something else on the allocate disc space screen. Choose one of your yet to used partitions and set mount point /. I'd label it natty or something. The existing swap will get used automatically. Do go ahead and intall the boot loader to sda and now that natty distro will have the controlling grub. It will be the latest Grub 2.

Then you can go about customizing your grub2. I hope to post more on doing that this weekend. I've kind of had to gather different pieces from different places related to customizing for multi-boot.

---

### Post by pdlethbridge on 2011-07-23
I just had a kernel update in 10.04 and it is obviously different, but the kde desktop didn't add a kernel. When I go to 11.04 I'll see how that effects the boot loader

---

### Post by pdlethbridge on 2011-07-23
there is a program in ubuntu called Start up manager and I got this pic from it 
it will let me chang the boot order if needed

---

### Post by Blasphemist on 2011-07-23
I don't think that startup manager handles sub-menus for older kernels on a given partition that Grub2 allows.

---

### Post by pdlethbridge on 2011-07-24
Jim look again at the screen shot and  you'll see several different kernels for 10.04

---

### Post by Blasphemist on 2011-07-24
> **pdlethbridge said:**
> Jim look again at the screen shot and  you'll see several different kernels for 10.04

Is startup manager creating a boot screen that shows all kernel versions or is it creating one that has all older than current kernels under a sub-menu for previous versions? I believe that even if you configure grub2 for that menu, startup manager will not show it.

---

### Post by oldfred on 2011-07-24
If you are not booting with grub 1.99 and 11.04, then startup manager will work. The new sub menus are only in grub 1.99 and that is where the issue has occurred. 

So if booting 10.04 startup manager should still work just fine.

---

### Post by pdlethbridge on 2011-07-24
does any one like the idea of re writing this thread and making it a stick thread

---

### Post by pdlethbridge on 2011-07-24
I want to add a very important thought. make sure the CDs you use to go live are super clean. I had some serious issues partitioning with the 10.04 CD because it was very dirt

---

### Post by pdlethbridge on 2011-07-25
In this link
[http://ubuntuguide.org/wiki/Ubuntu:Natty#Installing_multiple_OS_on_a_single_computer](http://ubuntuguide.org/wiki/Ubuntu:Natty#Installing_multiple_OS_on_a_single_computer)
 scan down to 2.5 about start up manager

---

### Post by pdlethbridge on 2011-07-29
I have been working hard to get every thing running smoothly. Here is the latest gparted photo

---

### Post by pdlethbridge on 2011-07-29
If you look closely you'll see how I have cut the partitions in half, they were 60 gigs each and swap was 40 gig. This is where this all  started  [http://ubuntuforums.org/showthread.php?t=1798653l](http://ubuntuforums.org/showthread.php?t=1798653l)

---

### Post by oldfred on 2011-07-29
Your partitions are starting to look like mine. I have many 20-25GB / installs and two larger data partitions with a little unallocated left inside my extended for a few more.

I am booting Maverick from my gpt sdb drive, so no root is mounted.

---

### Post by pdlethbridge on 2011-07-29
My default is to boot to lucid which is sda1 lucid. Trust me when.I say make sure you label your OSS or things can get very confusing at boot time. If I ever want to go back and try windoes ther is plenty of room at the end of the drive and as I have only used 3 of the 4 partitions I could down size the extended partition an add another partition at the end of the drive

---

### Post by GBB1 on 2012-01-17
> **Blasphemist said:**
> 
For all of the debian distros at least, for now I go ahead and install the boot loader and update that distro to where it's current before I boot to another distro. This gets any kernel changes needed at the time done and ensures that partition can be standalone. Don't worry, that partitions grub2 will find the other distros and let you boot them. Then I boot my controlling distro, re-install grub2 and run update-grub to get my customizing back.

As I keep learning about that I intend to create and later post documentation.

So using a separate /boot partitions doesn't solve the problem. Because I wanted to have just one Grub2 to control all distro's. As you lose all your settings when you overwrite the MBR with the new Grub2 (do not show recovery kernels, boot countdown, resolution, ...) from the new distro you are planning to install. 

But indeed, re-installing Grub2 on the controlling distro afterwards is not a bad idea. What command do you use for this?

---

### Post by pdlethbridge on 2012-08-27
I spent a week debuging the compute After I installed the grub replacement for start up manager. It was made more difficult by having the hard drive quit and go to Florida for a vacation

---

