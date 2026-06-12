---
title: "Installing multiple Linux distros"
date: 2012-05-23
forum: General Help
---

### Post by tech291083 on 2012-05-23
Dear Friends,
 
I am interested in installing multiple Linux distros on the same hard drive. Please tell me how I can do so. I have the following distros with me. Also let me know which one I should install from the list below. To be honest, I want to install all of them if possible. Which one I should install first, second etc. Thanks.
 
Ubuntu 10.04 LTS
Fedora 16
Debian 6
Gentoo 11
OpenSuse 12.1
Knoppix 6.4.4
Damn Small Linux 4.4.10
Mint Linux 12
Arch 2011.8.19
Puppy Linux 5.3.1
Sabayon 8
 
 
Dear Admin,
 
Please forgive me if this is not the right forum for my thread, thanks.

I have been searching the internet for a proper set of guidelines to installing multiple Linux distros to the same hard drive (I have one with 500 GB), but I have not been able to find one that can used by someone like me who is self-taught and not that technically sound. But i am sure that this is possible to accomplish and some people on other forums have done it successfully. Some have arrogantly discouraged me to do so. Please help me so that we can help others on this forum with the whole concept. 
 
Experienced Linux users on this forum can really help me and others by giving us some tips/guidelines. It will be really nice if someone tries this successfullly and makes us aware of the steps involved in reasonable detail. Thanks.

---

### Post by zombifier25 on 2012-05-23
Most Linux distros when installing should give you the option to repartition your hard drive. Install each OS on each separate partition, just don't choose override the bootloader (grub) if it's already installed. The actual process varies from distro to distro however.

Also, why do you want to do this?

---

### Post by holycow131415 on 2012-05-23
ive never done it, but i think this is correct...

On the ubuntu liveCD installer, you can "choose to do something else" to partition from there. basically youll need 1 swap partition that is double your ram size, probably 1 home partition, and 11 root partitions of about 20 gb depending on your home partition size and swap size.

Also through most of them use grub2, so each will install grub and update the grub for you. arch linux uses grub 1 by default, so be careful with that.

---

### Post by MadmanRB on 2012-05-23
Eh I dont think you will be able to do that many.
You see by default a hard disk can only take up to 4 logical partitions even on the the largest hard disk drives.
At max I say do two or three linuxes unless you have more then one hard drive this will not really work

---

### Post by wilee-nilee on 2012-05-23
> **tech291083 said:**
> Dear Friends,
 
I am interested in installing multiple Linux distros on the same hard drive. Please tell me how I can do so. I have the following distros with me. Also let me know which one I should install from the list below. To be honest, I want to install all of them if possible. Which one I should install first, second etc. Thanks.
 
Ubuntu 10.04 LTS
Fedora 16
Debian 6
Gentoo 11
OpenSuse 12.1
Knoppix 6.4.4
Damn Small Linux 4.4.10
Mint Linux 12
Arch 2011.8.19
Puppy Linux 5.3.1
Sabayon 8
 
 
Dear Admin,
 
Please forgive me if this is not the right forum for my thread, thanks.

Most of these will boot using grub 2 as the main bootloader.

Have you every loaded the mbr and are you familiar with grub 2

---

### Post by tech291083 on 2012-05-23
> **zombifier25 said:**
>  Install each OS on each separate partition, just don't choose override the bootloader (grub) if it's already installed. The actual process varies from distro to distro however.?

 
 
I have GParted Live tool with me on a CD and I am quite familiar with it when it comes to partitioning a hard drive, but even if I create the required number of partitions for the various Linux distros listed above, I am not sure as to how I should install each of them to a separate partition. I also do not know how to configure the boot menu after installed the last distro so that it lists all the distros (from which i can choose one to boot into) when to pc boots.
> **zombifier25 said:**
> 
Also, why do you want to do this?

 
Want to learn a few things about Linux and teach my friends and family and not to forget the community center kids, most of them from very poor background. My objective is noble and need your help my friend, so please guide me.

---

### Post by MadmanRB on 2012-05-23
why dont you just use virtualbox or something?
Its a nice tool to test out other os's

---

### Post by carl4926 on 2012-05-23
It's not difficult

Use gparted to create a swap
Then put everything else in side an extended as logicals

I would use one /home 
It's better to have one for each or don't use separate /home's at all

You might want to add a label to each or make a written note

---

### Post by tech291083 on 2012-05-23
> **holycow131415 said:**
> 
Basically youll need 1 swap partition that is double your ram size, probably 1 home partition, and 11 root partitions of about 20 gb depending on your home partition size and swap size.
 
Also through most of them use grub2, so each will install grub and update the grub for you. arch linux uses grub 1 by default, so be careful with that.
 
Your suggestions seem interesting to me. so if I am correct then, all I need to do is create 1 swap partition, 1 home partition and 11 root partitions (one each for distro, 11 in all). I think i can use GParted Live tool/CD to do so, what do you say to this? Thanks.

> **MadmanRB said:**
> why dont you just use virtualbox or something?
Its a nice tool to test out other os's
 
Thanks but tools like Virtualbox never really give the real feel or experience. I want to use a pc that I often use to do something interesting.  I have enough hard drive 500 GB and 4 GB DDR3 RAM to go ahead if I am correct.

---

### Post by holycow131415 on 2012-05-23
> **tech291083 said:**
> Your suggestions seem interesting to me. so if I am correct then, all I need to do is create 1 swap partition, 1 home partition and 11 root partitions (one each for distro, 11 in all). I think i can use GParted Live tool/CD to do so, what do you say to this? Thanks.

Yep gparted would do the job!

---

### Post by tech291083 on 2012-05-23
> **MadmanRB said:**
> Eh I dont think you will be able to do that many.
You see by default a hard disk can only take up to 4 logical partitions even on the the largest hard disk drives.
At max I say do two or three linuxes unless you have more then one hard drive this will not really work
 
 
Yes, not more than 4 logical partitions are allowed, but people have done this with 10-12 distros and they have told me on other forums that it is possible, but despite my repeated requests to them no one has so far given me a set of guidelines that everybody can follow easily and that is why I have turned to this forum for help. I am not doubting your skills or intelligence but just telling you what I have read on other forums on the net. i will try to find out threads on other forums that deal with this issue. Thanks.

---

### Post by MadmanRB on 2012-05-23
> **tech291083 said:**
> Thanks but tools like Virtualbox never really give the real feel or experience. I want to use a pc that I often use to do something interesting.  I have enough hard drive 500 GB and 4 GB DDR3 RAM to go ahead if I am correct.

But as I said space is not the issue, its partition allocation that is at stake here.
the limit I am talking about is not a lie, the limit of primary partitions of a hard disk is at least 3 or 4.
Now you can have up to 64 logical extensions but most OS's will only use what are listed as primaries.
Trust me I have tried what you are doing on an old computer and new or old more then three main OS's is not really possible.

---

### Post by malspa on 2012-05-23
> **MadmanRB said:**
> Eh I dont think you will be able to do that many.
You see by default a hard disk can only take up to 4 logical partitions even on the the largest hard disk drives.
At max I say do two or three linuxes unless you have more then one hard drive this will not really work

Not so. You just have to use an extended partition containing logical partitions. Even on one of my computers here, with an old 80 GB hard drive, I have six Linux installations, and could easily have installed more. And I'm pretty sure the OP wasn't talking about using an 80 GB drive.

To the OP: I like for my first distro to be one I think is gonna be there for the longest. Something like Debian Stable, for example.

---

### Post by carl4926 on 2012-05-23
There seems to be some missinformation

You can only have a max of 4 Primary partitions
If you create an extended partition (which is itself a primary, but just a container) you can put all the logical partitions you want inside it

---

### Post by tech291083 on 2012-05-23
Here is a thread that discusses multiple Linux distros successfully installed on the same hard drive by a Fedora forum member named Glennzo.
 
[http://forums.fedoraforum.org/showthread.php?t=267037](http://forums.fedoraforum.org/showthread.php?t=267037)
 
Post no. 14 page of the thread.
 
Ii do not intend to convey that Fedora people are smarter or more hepful than Ubuntu people, this is just a query by me that needs a proper anwser from experienced Linux users. This is just question, anwser to which will help all Linux uses understand installation of multiple distros better I am sure that I will get some help here. This is an issue i have been trying to solve for some time now, but failed in my efforts so please help me guys. Thanks.

---

### Post by malspa on 2012-05-23
> **MadmanRB said:**
> Trust me I have tried what you are doing on an old computer and new or old more then three main OS's is not really possible.

Sorry, this is not true, if you are talking about Linux only.

First three primary partitions, one of them has to be a swap partition. The fourth one is the extended partition. After that, all of them are logical partitions. You can put tons of Linux systems on those logical partitions. I don't know what the limit is but I have not had any problems doing this with any distro I've tried. I am not sure if you can put Windows on a logical partition, but then I haven't used Windows in any of my multi-boot set-ups for years.

---

### Post by carl4926 on 2012-05-23
>  I am not sure if you can put Windows on a logical partition, You can but you need a available primary in windows format for windows boot code

---

### Post by tech291083 on 2012-05-23
> **carl4926 said:**
> There seems to be some missinformation
 
You can only have a max of 4 Primary partitions
If you create an extended partition (which is itself a primary, but just a container) you can put all the logical partitions you want inside it
 
Agreed,
 
The max no of primary partitions is 4 and then you can have as many logical partitions as you like, that is all I understand, correct me if I am wrong, thanks.

> **malspa said:**
>  You can put tons of Linux systems on those logical partitions. I don't know what the limit is.
 
 
Even I am not sure as to how many, thanks.

---

### Post by malspa on 2012-05-23
> **tech291083 said:**
> The max no of primary partitions is 4 and then you can have as many logical partitions as you like, that is all I understand, correct me if I am wrong, thanks.

I think there's actually a limit on the number of logical partitions, or maybe there was a few years back. (???)

---

### Post by tech291083 on 2012-05-23
Dear Friends,
 
Thanks a lot for responding so fast. I have got my new 500 GB SATA hard drive ready, bought just 3 days ago to learn things about Linux. 
 
i am really happy that my thread/query which has bugged me for so long and i must admit here my own lack of proper technical skills (pardon me if you can but I am self-taught and most of my skills are results of forum discussions like this one, thanks to forum users for the sharing of ideas.) for the time it has taken me to find a solution. But i am sure that with the kind of interest that you have shown in the last 1 hr it is definitely going to be solved. I am so happy, can't hide me joy. Thanks a lot guys. Please continue...

---

### Post by goaliedude3919 on 2012-05-23
You should just be able to install each distro with a Live CD/USB and during the install process, it should give you options to either install over other OS's, install alongside other OS's, or something custom.

---

### Post by malspa on 2012-05-23
> **tech291083 said:**
> so if I am correct then, all I need to do is create 1 swap partition, 1 home partition and 11 root partitions (one each for distro, 11 in all). I think i can use GParted Live tool/CD to do so, what do you say to this? Thanks.

I would stay away from a shared /home, but that's just me.

Yes, you can use GParted from a live session.

Here, I use a separate / and /home for most distros, but that isn't necessary. I use a couple of separate data partitions that each distro can access. You could have one partition for each distro and then a big data partition for your personal stuff, or there are other ways people like to do it, too.

One distro, you can install grub to the MBR, then for the other distros install grub to their root.

Again, different people have different approaches, there is no right way. For more information you might want to do a web search, **multi-boot linux**, something like that. There are lots of people like me out there who prefer multi-booting instead of a virtual set-up,for various reasons, and there's a lot of info out there.

Also, although space is not an issue in your case, you can easily go with as little as 10 GB for each distro. I've been using 7 GB for / and 5 GB for /home, but with separate data partitions the 7/5 combination really turns out to be more than I need. I did a couple of installations with only one 10 GB / partition and that worked fine, too.

There's a lot that I can't think of at the moment (it's late here) but certainly you want to take good notes during each installation; they'll come in handy. And once you've had a little practice setting up multiple distros, it's no big deal. Just learn how to set up the primary partitions and the extended and logical partitions, and how to get grub in the right place.

---

### Post by tech291083 on 2012-05-23
> **malspa said:**
> I would stay away from a shared /home, but that's just me.
 
 
 
I agree.
 
 
> 
Here, I use a separate / and /home for most distros, but that isn't necessary.

 
I also prefer the same.
 
 
> 
One distro, you can install grub to the MBR, then for the other distros install grub to their root.
 
Yes, this is right.
 
 
> Again, different people have different approaches, there is no right way. For more information you might want to do a web search, **multi-boot linux**, something like that. There are lots of people like me out there who prefer multi-booting instead of a virtual set-up,for various reasons, and there's a lot of info out there.
 
I have done the web search but as you have metioned people have different styles and that has confused me so far and taken a lot of time to reach a reliable solution. I think you approach seems to be very close to one that I have in mind for some time now, although I have read other forums and tried things but failed time and again.

Ok, here is what I think I should do.
 
1 swap partiton 10 GB (my RAM is 4 GB), which will serve all the distros.
 
11 partitions within which I will create a separate / and /home partitions during install for each of the 11 distros.
 
Should i install Grub for each distro to its / partition or create a separate boot partition?
 
 thanks.

---

### Post by malspa on 2012-05-23
> **tech291083 said:**
> I have done the web search but as you have metioned people have different styles and that has confused me so far and taken a lot of time to reach a reliable solution.

One thing that could be confusing is that a lot of info out there was before grub2 came into play. It does seem that perhaps grub2 is easier for multi-booting than grub-legacy was, although most of my experience has been with grub-legacy.

With earlier version so Ubuntu, I had to use the alternate CD so that I could install grub to Ubuntu's root because the main CD would only install it to the MBR. This was not the case with 12.04, though.

Also I have had other distros overwrite the MBR when I meant for it to install grub to the distro's root. Either a mistake on my part or a problem with the installer. It happens, though, so you'll want to learn how to reinstall grub to the MBR if you need to.

Some people just use a different bootloader altogether.

Post-install, I usually have to create mount points for the other partitions, and edit /etc/fstab, and then I can easily access each partition from any distro.

You'll want to pay attention during the installation to how the distro handles the system time. A lot of times it'll be something like "UTC - yes or no?" Or sometimes the distro won't even ask you. Sometimes you have to go back and fix it later so that one distro won't be using UTC when the others are set not to use it. That's a subject within itself, but you don't want to end up with one system having one time and others having a different time. Here, I have all mine set to UTC=no, and if I need to correct it I go to /etc/default/rcS and change the line UTC=yes to UTC=no. But on your computer you might do it opposite, I'm not sure.

> **tech291083 said:**
> Ok, here is what I think I should do.
 
1 swap partiton 10 GB (my RAM is 4 GB), which will serve all the distros.
 
11 partitions within which I will create a separate / and /home partitions during install for each of the 11 distros.
 
Should i install Grub for each distro to its / partition or create a separate boot partition?
 
 thanks.

4 GB RAM is a lot; you probably won't need a 10 GB swap. I have 2 GB RAM and my swap almost never gets used. Someone else might want to step in on this one but I think 2 GB swap might be more than enough. Check out what other people say who have 4 GB RAM or more.

Again,separate / and /home is great but also consider just one / partition. A lot of people will say it's much better to do that.

A separate /boot partition is normally unnecessary. I think Fedora's documentation recommends it but a friend of mine runs Fedora without it.

---

### Post by tech291083 on 2012-05-25
Dear Friends,
To tell you the truth, I have always believed that there are basically 5 types of Linux distros in the world and my info comes from the page below. 
 
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)
 
Debian-based
Gentoo-based
Pacman-based
RPM-based 
Slackware-based 
 
I have so far downloaded the below mentioned 11 Linux distros that spread across these 5 distro types. I have chosen atleast 1 distro from each of the above 5 distro types.
 
Arch 2011.8.19 (Pacman-based) 
Damn Small Linux 4.4.10 (Debian-based)
Debian 6 (Debian-based)
Fedora 16 (RPM-based)
Gentoo 11 (Gentoo-based)
Knoppix 6.4.4 (Debian-based)
Mint Linux 12 (Debian-based)
OpenSuse 12.1 (RPM-based)
Puppy Linux 5.3.1 (Slackware-based)
Sabayon 8 (Gentoo-based)
Ubuntu 10.04 LTS or Ubuntu 12.04 LTS (Debian-based)
 
 
I have so far installed only the following distros successfully and they belong to only 2 distro types namely Debian-based and RPM-based. Each of the below 4 distros was installed using the option use entire disk, thus it remained the only OS on the hard disk whenever I installed and explored it for a few days. There was no other distro or OS, not even Windows.
 
 
Fedora 16 (RPM-based)
Mint Linux 12 (Debian-based)
OpenSuse 12.1 (RPM-based)
Ubuntu 10.04 LTS or Ubuntu 12.04 LTS (Debian-based)
 
 
I want to install all of the above mentioned 11 distros (which includes all the 5 types) to the same hard drive (500 GB SATA) in order to know how each of these 5 types behave when installed alongside each other. This is going to teach me a lot about different distros. This might be a total waste of time, but it will surely teach me a thing or two about Linux. I will share my experiece with others on this forum and my personal blog if all goes well. So in this regard, your help is of utmost importance to me and I am sure that you will be there till the very end. Thanks for supporting me so far.
------------------------------------------------------------
Please do reply with your suggestions, thanks a lot.
 
Now before I start, I have the following questions that need answers.
 
1. Which distro should be the 1st distro? 
 
2. Is there a particular order that I need to follow based on your experience?
 
3. I have also tried to install Arch 2011.8.19, Damn Small Linux 4.4.10 and Puppy Linux 5.3.1 but not been able to do so. Is it possible to install these 3 distros along others as part of the original 11? Or do I need to replace them with something else?
 
4. Knoppix 6.4.4 is basically a live distro, usually not meant for installation to hard drive. Should I drop it from the original list of 11 or is it possible to install it to a hard drive? 
 
5. Gentoo and Sabayon are rolling distros. Is it possible to install these 2 distros along others (9) as part of the original 11? Or do I need to replace them with something else?
 
6. If you think a particular distro will not install with others, please suggest me a replacement for the same that belongs to the same type ie the 5 mentioned above namely Debian-based, Gentoo-based etc.
 
7. Technically speaking, is it possible to install 5 types of distros which are based on different code base to the same hard drive? Have you ever tried to so? 
 
Thanks.

---

### Post by sammiev on 2012-05-25
I have 4 OS on one hard drive with no problems. Would I try another? Maybe. :)

---

### Post by oldfred on 2012-05-26
I really only have installed Ubuntu's to my sdc drive. It was newer and I had upgraded from my 160GB 32 bit install and wanted 64 bit. So I installed in a 25GB / partition and kept data on a 100GB partition. But I did not allocate entire drive as I did not need it, and have since just kept adding 25GB / partitions. I have just about every version of Ubuntu from 10.10 on my drive. I also install Puppy to prove it would install, but have not booted it recently. I will go test it now. Edit - my old puppy Lucid Puppy 5.1 still boots. It is almost as fast booting as my Ubuntu on a SSD.

I have not installed knoppix.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Order of install is not critical, last install may be more important as then it will default to be your boot loader in the MBR. But you can easily reinstall grub legacy or grub2 to boot any system. You may want to edit grub2's 40_custom after using grub2 to find all the installs as the boot menu gets too long. I turn off os-prober and just put one entry in 40_custom for each install.

Fedora likes to use LVM. Some suggest partitioning in advance and not using LVM.

If you want to share data be aware of UID/GID. Ubuntu uses 1000 & I believe Fedora just changed from 500 to 1000 as the default. Not sure about others.
Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

Back in the days before grub2, we used to install grub legacy to the partition and chain load. Now old info but shows some of the planning required.
chainboot 145 systems - saikee
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)

---

### Post by houseworkshy on 2012-05-26
There is also this, which I haven't tried out myself so can neither recomend or caution against.
[http://omniboot.sourceforge.net/](http://omniboot.sourceforge.net/)

---

### Post by KBD47 on 2012-05-26
> **MadmanRB said:**
> But as I said space is not the issue, its partition allocation that is at stake here.
the limit I am talking about is not a lie, the limit of primary partitions of a hard disk is at least 3 or 4.
Now you can have up to 64 logical extensions but most OS's will only use what are listed as primaries.
Trust me I have tried what you are doing on an old computer and new or old more then three main OS's is not really possible.

I have 4 operating systems right now on my computer:
Kubuntu 12.04, SolusOS, Mint 13, and CentOS 6.2. My understanding is only 4 primary partitions, but quite a few logical partitions are possible. Some installers are easier than others, the biggest issue I've run into is the OS's that use Legacy Grub, those are picked up by Grub 2, but Legacy doesn't always pick up Grub 2 installs, so best to install the legacy grub versions first, but if that cannot be done I'd install legacy grub only to the partition you are putting it on and go back and update the top grub 2 install to pick up the legacy install, I hope that makes sense.

edit: one thing I would recommend before installing all those systems is to test each one first to make sure it works with your computer hardware, use live dvds/cds which are fairly cheap, no use installing something you can't run. Also keep in mind you could start with 3-4 systems, and add more by resizing your partitions using gparted. I would be nervous about installing a dozen operating systems without testing them on my hardware first, and I would gradually add them, say start with a dual boot, size down your first partition with gparted, keep resizing as you move along, but that's me :-)

---

### Post by ts3 on 2012-05-26
> **tech291083 said:**
> Now before I start, I have the following questions that need answers.
 
1. Which distro should be the 1st distro? 
 
2. Is there a particular order that I need to follow based on your experience?
 
3. I have also tried to install Arch 2011.8.19, Damn Small Linux 4.4.10 and Puppy Linux 5.3.1 but not been able to do so. Is it possible to install these 3 distros along others as part of the original 11? Or do I need to replace them with something else?
 
4. Knoppix 6.4.4 is basically a live distro, usually not meant for installation to hard drive. Should I drop it from the original list of 11 or is it possible to install it to a hard drive? 
 
5. Gentoo and Sabayon are rolling distros. Is it possible to install these 2 distros along others (9) as part of the original 11? Or do I need to replace them with something else?
 
6. If you think a particular distro will not install with others, please suggest me a replacement for the same that belongs to the same type ie the 5 mentioned above namely Debian-based, Gentoo-based etc.
 
7. Technically speaking, is it possible to install 5 types of distros which are based on different code base to the same hard drive? Have you ever tried to so? 
 
Thanks.

I multi-boot various linux distributions (no Windows) on a couple of laptops so here are a few answers based on my (admittedly limited) experience:

1) Doesn't matter which distro is first, but as already mentioned it's a good idea to remember which was last as its grub would be the one most likely in use, unless you really know what you're doing; also, as oldfred mentioned, grub can be re-installed/updated so ultimately it's not a huge deal.

2) No particular order; personally I like to put on sda1 the distro I'll use the most but it's just a preference, YMMV.

3) DSL and Puppy Linux are meant to be live distros, DSL is not actively maintained IIRC so not much point in installing for either; Arch is tricky - it's doable but you have to be comfortable on the command line, follow closely the Beginner's Guide from the Arch Wiki, make sure you have a wired connection for the install (setting up wireless from the command line is not fun and may not always be possible depending on drivers) and have another device (computer, smartphone) to connect to the internet and research during the install; also Arch uses grub legacy methinks so care is needed.

4) Same for Knoppix as for DSL & Puppy; there's probably a way to install but not much point - if you want to try them out just run from a USB for a while

5) Sabayon and Gentoo are rolling distros, Arch is a rolling distro as well; all can be installed on multi-boots but Gentoo is probably trickier than Arch because it's compiled from source.  Check distrowatch - Arch is for "competent users," whilst Gentoo is geared towards "developers and network professionals."  Not an insurmountable barrier but something to keep in mind. Sabayon is relatively easy to install.  Rolling distro basically means that you install at a certain point and keep updating from then onwards.

6) No reason why any distro should not install with others but different combinations may throw out some unexpected errors and you may need to troubleshoot. 

7) I've ran 3 versions of ubuntu and five other distros on two different laptops (but not more than 3 at the same time) with no problems apart from the occasional grub issue until I figured out how grub works.  As to "code base," the different distros all have a linux kernel, a package manager, a desktop environment (usually) and packages and each distro runs on its own self-contained partition so it should not affect the others once installed; the actual installation and grub are when things may go wrong.

As to partitioning I'd suggest running Gparted from a live USB, partitioning in advance and writing down the numbers and sizes of partitions and what's installed on which, with the following split on a 500 GB: sda1 20-25 GB, 8G swap on sda2, 15 GB on sda3, and then create an extended partition on sda4 and split it into sda5,6,7,8,9,10 etc, say of 10-15GB each.

All in all installing 11 distros may be a tad ambitious and also a bit pointless in the case of live distros such as DSL, Puppy & Knoppix.  

Be prepared to be patient, to read a lot of manuals and do a lot of research: not many people run that many distros at the same time so getting help may not always be easy/possible.

Cheers :)

---

### Post by Ralph L on 2012-05-26
Section 1 of this may be helpful.  [http://ubuntulinuxnoviceguide.webs.com/](http://ubuntulinuxnoviceguide.webs.com/) .
It is somewhat dated so some of the menus are a little different now.  However, I have installed many versions of ubuntu and some of Mint, Zorin lubuntu, kubuntu, etc.

---

### Post by tech291083 on 2012-05-27
> **ts3 said:**
> 
 
Arch is tricky - it's doable but you have to be comfortable on the command line, follow closely the Beginner's Guide from the Arch Wiki, 

 
 
I will surely refer to the Wiki.
 
> Sabayon is relatively easy to install. 

 
This is really a good suggestion, I will give preference to Sabayon if needed.
 
>  
No reason why any distro should not install with others but different combinations may throw out some unexpected errors and you may need to troubleshoot. 

 
I agree, I will try my best to do it the right way.
 
> As to partitioning I'd suggest running Gparted from a live USB

 
I always use GParted Live CD.
 
> All in all installing 11 distros may be a tad ambitious and also a bit pointless in the case of live distros such as DSL, Puppy & Knoppix.
 
 
Ok, agreed, but can you please suggest me alternatives for these 3 distros based on your own experience?
 
> Be prepared to be patient, to read a lot of manuals and do a lot of research: not many people run that many distros at the same time so getting help may not always be easy/possible.

 
Yes, a lot of patience is required. Thanks a lot for anwsering my queries, appreciated. Keep sending suggestions/tips/advice, I will take them on board.

7. Technically speaking, is it possible to install 5 types of distros which are based on different code base to the same hard drive? Have you ever tried to so? 

Thanks.

---

### Post by houseworkshy on 2012-05-27
This is a little off topic but not too much I hope.  
Just found this [http://www.hybryde.org/hybryde_evolution](http://www.hybryde.org/hybryde_evolution)
Both the website and the disto are in French though English language  packs are available for installation.  What it is is a distro with many  gui's, the big deal seems to be that one can switch gui's without a  reboot and without having to close ones apps.  Very clever but don't  know how much of the previous gui is flushed from ram after a change (  thinking performance ).     [http://distrowatch.com/table.php?distribution=hybryde](http://distrowatch.com/table.php?distribution=hybryde) don't have links  to reviews of it as I write but I've just grabbed an iso to play with  later.
The reason for this aside and my feeble attempt to sound on topic is  that if one of the OP's reasons for wanting so many operating systems is  to test out differant user interphases this may be a many in one  solution.  As some apps partially depend on the gui this could  also be a  fit most applications system, flip to suit whatever one is using.  I  used to duel boot Kubuntu and Ubuntu simply because some app's ran much  better in kde and installing them in Ubuntu caused too much lint and  occasional problems.  
It'd, probably be a very handy distro to have around if one wanted to  quickly show other's what sort of gui's are out there for linux too.
Ok asideish bit over.  The limit for partitions for per disk is usually  four.  Be cautious of that, if one exceeds it one can have severe  problems which take some fixing and, I've been told though don't  remember the source so could hopefully be wrong on this, sometimes the  problems are *not* mendable.  I'd give each system only one and make it's  required internal partitions all logical.  So the max would be four  times however many drives you have.

---

### Post by oldfred on 2012-05-27
No the max is 4 primary partitions under MBR, of which one can now be an extended partition and the extended can hold essentially an unlimited number of logical partitions. Windows has to boot from primary, but can have a second install in a logical & Linux works from Logicals. Not sure about some of the other systems that are Unix based.

The limit on partitions is 128 with gpt partitioning which works for most Linux installs but not sure about all the one's you are using. gpt is required for drives over about 2.2TB or 2TiB. Arch also suggests gpt for SSDs.

My c: drive has several installs but most are Ubuntu:

```
fred@fred-Precise:~$ sudo blkid -c /dev/nul -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   /mnt/backup    13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  (not mounted)  431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdc14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    quantal  (not mounted)  3b72e3d4-3d56-469b-ad50-f13ac4f5f0

```

---

### Post by malspa on 2012-05-27
> **ts3 said:**
> All in all installing 11 distros may be a tad ambitious and also a bit pointless in the case of live distros such as DSL, Puppy & Knoppix.

> **tech291083 said:**
> Ok, agreed, but can you please suggest me alternatives for these 3 distros based on your own experience?

Even without DSL and Knoppix you'd have three Debian distros (Debian, Mint, Ubuntu); install nine distros instead of 11? 9 is a much nicer number! :)

And how about Slackware instead of Puppy?

---

### Post by 23dornot23d on 2012-05-27
I have had 13 Distros or more on one USB hard drive ........ 

Some of the problems I have noted on my website have a look through its old but maybe you can get some ideas from it .....

[https://sites.google.com/site/000menu/](https://sites.google.com/site/000menu/)


The thing is try it and you will run into all sorts of problems but you will learn .....

I now mainly run Arch and Ubuntu together now ....


But here is a quick overview of what may be the best course of action to take to do it.

Things change by the way and I have not found the need to have that many all running off of one drive recently ...... as it does get confusing unless you keep each Desktop and OS for a particular task ....

ok 

Number one thing to do is to divide the hard drive up before you start installing them all

1 ....... Use one OS to start with ..... my choice would be KDE 12.04 at the moment
use the custom install and install boot to the MBR for this OS

2 ...... Divide the drive into 4 partitions ...... Primary .... Primary .... Primary .... Extended

3 ...... The Partition sizes are the main thing you do not want to have to go back and start re-sizing things afterwards .......

4 ..... So 500 Gig and 11 operating systems ..... 40 Gig for each would be ok 

5 .... Kahel OS is a Arch based system use this for ease and it needs to go in a Primary partition

6 .... There are always problems with some OS's wanting to use the OId Grub .....
only Mandriva 2010 install ever seemed to sort this out ...... not sure where it stands now as
that system seemed to loose its developers and changed name.

7 ..... If you start by getting 3 on to start with we will go from there ...... but as I say 
set the drive up first .....

Primary 40 Gig .... Primary 40 Gig ..... Primary 40 Gig ( Extended  40 40 40 40 40 40 40 40 swap )

11 x 40 = 440 +  a swap 4 Gig ......... 444 Gig ....... and the Unallocated if you want another system at some point ...... you can never have enough Linux installs ....

I now have 4 x external USB hard drives all full of Linux OS's ...... I never usually delete them ...... just go out and buy another USB hard drive and keep adding  :lolflag:


It seems a crazy thing to do but its fun - and you do get a good overall view of the Linux systems available ......

See if you can get these on the first three primary partitions to start with

1 .... Ubuntu KDE 12,04
2 .... Kahel OS
3 .... Mandriva  ( This uses the old grub  and it links to grub 2 in its boot menu )

4 .... The extended Partition - have all the partitions ready to use - but not sure what order to put then on in yet .... Fedora and Sabayon have odd installers .... you may even want to get used to installing these two separately before you begin for real ....
You can always reformat and restart ..... but ensure you know that you can install them first ....... 

You are not going to install them ( 11 ) all at once ...... the task will be a nightmare ..... and the way I did it was over time ..... with problems and reformats expected along the way.

And keep the Grub Boot on the partition with the OS ....... its easier that way ..... trust me on this ....... doing it any other way will be confusing at the very least ..... * NOTE ( you always need to go to your main OS and update grub when adding other OS's ...... but at least you know which OS is controlling the BOOT this way. )

One OS think I used Mandriva ....  this controls the Master Boot but install it 3rd  ....... that way when you go into it and do a update Grub it will find all the rest of the OS's you have ...... and it can use the old and new Grub .....

Hope this helps to get you started ......

> 
Ubuntu 10.04 LTS
Fedora 16
Debian 6
Gentoo 11
OpenSuse 12.1
Knoppix 6.4.4
Damn Small Linux 4.4.10
Mint Linux 12
Arch 2011.8.19
Puppy Linux 5.3.1
Sabayon 8
Open SUSE and Gentoo ...... not going to be a good experience mixing these in ...... there ..... but it can be done
as I did it once .....

The changes to all distros through time adds to problems you will encounter and you are bound to hit many hurdles along the way.

Each system can use the same swap space ..... so only one swap space is needed ...... * ( do not use /home
this will also be a nightmare as each system will try writing different config files there - the partitions are going to be busy enough without adding any more confusion to it )

---

### Post by Avaritia on 2012-05-27
Unless your going to go into programming level details about how linux works isnt installing that many distros a bit pointless? 

There are only so many desktop enviroments so the only thing people who see the distros will see is different package managers and the launchers in different places,

---

### Post by 23dornot23d on 2012-05-27
> 
Unless your going to go into programming level details about how linux works isnt installing that many distros a bit pointless? 
I would say that nothing is pointless .... how do you know anything - without first trying.
As in this thread - some people think that only 4 partitions and possibly 4 OS's already people are learning new things .... once you have succeeded then you can start to see which work best with each other and which are faster on the same machine and hard drive and which do not upgrade so easily .....

If the USER was to just take advice and not explore ..... then the start above is what I would use ...... they may find that these give all that is needed and not need to go any further but who knows . * things change in each Distro ......

Ubuntu 12.04
Arch ( Kahel OS )       
Mandriva 2010



I was impressed when I installed KNOPPIX and KANOTIX was my favourite distro
it almost brought the LiveCD into existence on its own ..... yet you do not see so much
mentioned nowadays .... but it still progresses in different directions too .....
> 
**Adriane Knoppix**

  [[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/c/c6/Knoppix.JPG/220px-Knoppix.JPG[/IMG]]("http://en.wikipedia.org/wiki/File:Knoppix.JPG")  [[IMG]http://bits.wikimedia.org/static-1.20wmf3/skins/common/images/magnify-clip.png[/IMG]]("http://en.wikipedia.org/wiki/File:Knoppix.JPG")
 Knoppix
 
 
 Adriane Knoppix is a variation that is intended for [blind]("http://en.wikipedia.org/wiki/Blindness") and [visually impaired]("http://en.wikipedia.org/wiki/Visual_impairment")  people, which can be used entirely without vision oriented output  devices. It was released in the third quarter of 2007 as a Live CD. *Adriane Knoppix*  is named after Adriane Knopper, the wife of Klaus Knopper, the  developer of Knoppix. Adriane has a visual impairment, and has been  assisting Klaus with the development of the software.[[12]]("http://en.wikipedia.org/wiki/Knoppix#cite_note-11") The name Adriane is also a [backronym]("http://en.wikipedia.org/wiki/Backronym") for "Audio Desktop Reference Implementation And Networking Environment".
 Adriane Knoppix is intended not only for the blind but also for beginners who don&#8217;t know much about computers. It uses the [SUSE]("http://en.wikipedia.org/wiki/SUSE_Linux_distributions") Blinux [screen reader]("http://en.wikipedia.org/wiki/Screen_reader") with a [phoneme]("http://en.wikipedia.org/wiki/Phoneme") generator and speech engine for normal output.




I could also see something good coming from this - if more people tried it - then maybe one day it would create some form of environment where we can bring back together all the splits ......... and make LINUX united ......

Think the overall community is massive - if it could only be brought back together again.

---

### Post by malspa on 2012-05-27
> **Avaritia said:**
> Unless your going to go into programming level details about how linux works isnt installing that many distros a bit pointless? 

There are only so many desktop enviroments so the only thing people who see the distros will see is different package managers and the launchers in different places,

I think it actually gives you a lot more than seeing different package managers and launchers in different places. Comparing and contrasting how different distros do different things is a very effective learning vehicle; seeing how things are set up in one distro can really help you out in another one. Also, just reaching a point where you know you can run *any* distro is a really good feeling. Besides that, it's a fun exercise, hardly pointless -- but that depends on how you look at things, I guess.

> **23dornot23d said:**
> I could also see something good coming from this - if more people tried it - then maybe one day it would create some form of environment where we can bring back together all the splits ......... and make LINUX united ......

I agree. Multi-booting totally eliminated any desire I might have once had to be a fanboy of any one distro -- taught me to be a "Linux user," not just a Mepis user or an Ubuntu user or whatever. I wish more people did it.

---

### Post by ts3 on 2012-05-27
> **tech291083 said:**
> To tell you the truth, I have always believed that there are basically 5 types of Linux distros in the world and my info comes from the page below. 
 
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)
 
Debian-based
Gentoo-based
Pacman-based
RPM-based 
Slackware-based 

To go back a bit, the above list is not necessarily how I'd describe the types of Linux distributions so I'd suggest not to try to base a decision on what to install too rigidly on this list.   For starters there are many more than five types :)  I'd say that the desktop environment and the package manager are the main features to look at.

23dornot23rd above has excellent advice.

> **tech291083 said:**
> Ok, agreed, but can you please suggest me alternatives for these 3 distros based on your own experience?

I've been thinking about possible replacements.  There's Chakra, which is an Arch fork and from what I understand it's easier to install than Arch.  Chakra sounds like Arch for beginners, the same way that Sabayon is like a Gentoo for beginners, put very roughly.  Sabayon offers two package managers, Entropy (easier) and Portage (same package manager as Gentoo, for more advanced users), users are advised to pick one and stay with it.  Personally I don't see the point of installing either fork (I tried Sabayon 8 a few months ago).  The main attraction of Arch or Gentoo is the ability to create highly customised, user-configured systems where the user is in control of the system; using pre-configured installs such as Sabayon or Chakra kind of defeats the purpose :) but YMMV.

Fedora is going to release a new version in a few weeks, it might be worth waiting for that.  Fedora is probably a good distro to use with GNOME (its default DE) the same way that openSUSE is a good way to try out KDE (openSUSE's default DE).

As a replacement for DSL, Knoppix or Puppy one might want to look at lighter desktop environments/window managers such as xfce, lxde and Enlightenment, which can run on top of different distributions (xubuntu and lubuntu are examples for the first two and you don't even have to install separately but can just run them on top of ubuntu).  

Also, Mageia just had a new release and it offers a lot of options: apart from GNOME & KDE it also has IceWM, lxde, xfce, Openbox and WMaker.

Installing multiple distros is an interesting project but I'd second 23dornot23rd and say start with a couple of installs, troubleshoot, then install another etc.

Cheers and keep us posted :)

---

### Post by xyzzyman on 2012-05-27
> **malspa said:**
> I agree. Multi-booting totally eliminated any desire I might have once had to be a fanboy of any one distro -- taught me to be a "Linux user," not just a Mepis user or an Ubuntu user or whatever. I wish more people did it.

People don't need to use multiple OS's. For the majority of people out there (Not tech "nerds") they just need the OS to get to the programs they use and stay out of the way. Over the course of two months last year I tried a half dozen distro's, from ubuntu to fedora to arch, with different WM's. I settled on Ubuntu with Unity and haven't even booted into Windows 7 in 2 months. Had a short run for a month or so of custom compiling my kernel with it stripped down to nothing except what my hardware needed, but eventually gave that up as it was taking up time from the real world.

As far as the OP, making a multi-boot USB of live environments of Linux might save a lot of time to try out different variants of Linux before you start partitioning and installing different ones. Realistically you're only going to wind up using 2-3 of them tops as who has the time to keep them updated, etc and actually get any real work done?

---

### Post by malspa on 2012-05-27
> **xyzzyman said:**
> People don't need to use multiple OS's. For the majority of people out there (Not tech "nerds") they just need the OS to get to the programs they use and stay out of the way. Over the course of two months last year I tried a half dozen distro's, from ubuntu to fedora to arch, with different WM's. I settled on Ubuntu with Unity and haven't even booted into Windows 7 in 2 months. Had a short run for a month or so of custom compiling my kernel with it stripped down to nothing except what my hardware needed, but eventually gave that up as it was taking up time from the real world.

As far as the OP, making a multi-boot USB of live environments of Linux might save a lot of time to try out different variants of Linux before you start partitioning and installing different ones. Realistically you're only going to wind up using 2-3 of them tops as who has the time to keep them updated, etc and actually get any real work done?

You're absolutely right, people don't *need* to multi-boot.

But some people want to, and enjoy doing so. People don't *need* to use Linux, people don't *need* to install and use more than one desktop environment, people don't *need* to have more than one desktop background, people don't *need* to use the command line, people don't *need* to play computer/video games, people don't *need* to read novels, people don't *need* to drink beer... Quit wasting your time, people! :)

---

### Post by chocklet on 2012-05-28
"I want to install all of the above mentioned 11 distros.... This might be a total waste of time..."

Agreed

1. Which distro should be the 1st distro?

Start with Ubuntu 12.04 and install grub to MBR.  Then install other grub2-based distros.  Then boot into Ubuntu 12.04 and sudo update-grub.
--
2. Is there a particular order that I need to follow based on your experience?

Start with all grub2 (1.99) distros and then stop and use your multiboot system for a while.  Copy your grub.cfg to a flash drive,  print it out and put it on the wall or refrigerator where your wife will see it.  Glory in your success.  Have a beer.  Tell your neighbors, and sleep on it.  

Then, when you have a few hours, grit your teeth and proceed with the other non-grub2 distros.  After each install, boot into your recent install, and copy menu.lst or grub.cfg to your flash drive and rename the copy to identify the distro.  Then reboot into Ubuntu and sudo update-grub.

If you can't get back into Ubuntu, then boot from the Ubuntu CD and rebuild grub2 grub.cfg from the CD.  Here are 3 explanations of how to accomplish the rebuild (there are others)...
[http://odzangba.wordpress.com/2011/05/14/455/](http://odzangba.wordpress.com/2011/05/14/455/)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD")
[http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

For any distro that grub2 can't automagically boot, be prepared to inquire in the appropriate forum.  You will become an expert at editing /etc/grub.d/40_custom.
--
3. I have also tried to install Arch 2011.8.19, Damn Small Linux 4.4.10 and Puppy Linux 5.3.1 but not been able to do so. Is it possible to install these 3 distros along others as part of the original 11? Or do I need to replace them with something else?

You probably need Arch if you want a complete exposure to popular options.  (I don't)  But if Arch is difficult, then save it until later, and then treat it as a separate project.  If you have a problem and go the the Arch forum, you'd best have some evidence that you have some experience, and that you have exerted some effort before asking for help.
--
4. Knoppix 6.4.4 is basically a live distro, usually not meant for installation to hard drive. Should I drop it from the original list of 11 or is it possible to install it to a hard drive?

It is possible, but don't do it.  To learn how Linux works, first use distros in the manner that they were designed to be used.

Use Knoppix 6.7.0, DVD version.  Forget the hard drive install.  Run from an 8GB flash drive... it "installs" from the DVD with one or two clicks.  First put a second partition on the flash drive.  There, now you have an example of a "poor man's install" on flash, and this should be part of the process of getting exposure to popular Linux options.

You can spend days experimenting with all the software included and figuring out how Knoppix functions.  Works on several of my PCs.  It's not clear why people take a distro that is designed to run from CD/flash and install it on a hard drive, and then take a distro that is designed to run from a hard drive and put it on flash.
--
5. Gentoo and Sabayon are rolling distros. Is it possible to install these 2 distros along others (9) as part of the original 11? Or do I need to replace them with something else?

It is possible.  I doubt that it is easy with all 9 others.

"Rolling" should *generally* not be a determining factor.  It makes no difference with PCLOS (a rolling release that uses grub legacy).  I currently multiboot PCLOS with Ubuntu grub2.  (grub2 makes me edit /etc/grub.d/40_custom and my grub menu is ugly with extra non-functional entries).  In the past, PCLOS has been easy with some other grub-legacy non-rolling release distros (Mepis and probably old Mint).  

Once upon a time, 2+ years ago(?), I multibooted Sabayon, almost certainly with a boot loader from a non-rolling release, but don't remember any specifics.

"Rolling" *might* be a factor if an update to the rolling distro installs a new version of grub or installs a new kernel.  There are so many variables here that any generalization might have exceptions.
--
6. If you think a particular distro will not install with others, please suggest me a replacement for the same that belongs to the same type ie the 5 mentioned above namely Debian-based, Gentoo-based etc.

It's a matter of expertise.  Somebody here, probably several, can make all this stuff boot from the same boot loader.  But even to the expert, I'll bet that it just isn't much fun.

If I truly want to get a thorough exposure to Linux, then I need to be familiar with the most common DEs.  Not just look at them, but actually use them for a few evenings at the very least.  That would include Unity and Cinnamon.

Must installs would be...
Ubuntu 12.04 Unity & Classic
Mint Cinnamon
Fedora Gnome 3
Mageia or PCLOS KDE & grub-legacy

Then, after I'm comfy with the above, probably...
OpenSuse to see why you don't need mono
Bodhi Enlightenment
Debian LXDE or Lubuntu
Sabayon
Arch (I've never tried)
Slack (I failed, long ago)
Maybe Cent or Scientific
Maybe Gentoo (A different experience from Sabayon?)
Maybe Linux from Scratch (LFS)? (I've never tried)

Manditory, but not on hard drive...
Knoppix DVD version from flash
Puppy CD or flash

7. Technically speaking, is it possible to install 5 types of distros which are based on different code base to the same hard drive? Have you ever tried to so? 

Technically speaking, anything is doable and has been done, and done multiple different ways.

But generally speaking the question is inappropriate.  It is like asking if it's possible to use a universal remote on 5 TVs that are different screen type.  As screen type will not determine compatibility with a remote, code base *generally* does not determine compatibility with a boot loader.  That said, my understanding is that Slack requires a particular kernel to be booted by grub2, so while it might be said that Slack can *easily* be booted by grub2, the "technically" correct semantics is (are?) debatable.  Actually, any generalization a person tries to make here might be inaccurate.

A better question would be... "Is it easy to multiboot distros that are released with different boot loaders?"  
The answer, for some here, is "No Problem".
The answer, for most here, is "Sometimes".  
The answer, for a perpetual noob like me is, "no".

I use removable drives (cartridge system) for experimenting.  I don't tinker with my main drive until I'm confident that I know that something will work, because of my low level of expertise and because I hate it when my wife laughs at me.  Obviously, I don't touch her PC until I am absolutely totally and completely certain that I won't mess up her current/old system.

Some time ago, I installed Sabayon with other distros.  I don't recall the mix of distros although the boot loader was probably Mepis'.  It's unlikely that I used Sabayon's boot loader.

Not long ago, on a friend's PC, I installed 3 different "code bases".  
Lubuntu (grub2) 
OpenSuse (grub-legacy)
Legacy (a Puppy derivative that uses grub-legacy)
I could not get Lubuntu's grub2 to boot Legacy (the Puppy derivative), even though I had specific directions.  Likely I was blind to some stupid mistake.  OpenSuse's grub-legacy booted everything, I think with no tinkering.

Here is some info on dual booting distros that were released with different boot loaders.
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259](http://www.dedoimedo.com/computers/grub-2.html#mozTocId982259)

<>

There's three ways to approach learning Linux.
1. Learn what's easiest to learn first.
2. Learn well how a major code base works (probably Debian or Fedora) and then enlarge your studies.
3. Learn about everything all at once.

#1 worked for me.  Find something that works on your hardware, that has a forum where you're comfy, ask for help and help others when you can. It's all good.

I think that #3 is the most difficult.

---

### Post by carl4926 on 2012-05-28
Install the legacy grub distros first, they may not boot if they are way down the table anyway, just let them install grub to / and continue with all the installs

Finish with Ubuntu if you want to use that. Or other grub2 distro

You can switch to any grub2 distro for booting but more than the quoted is reqiured

> @chocklet wrote: Then reboot into Ubuntu and sudo update-grub.Yes but you would also need
```
sudo grub-install /dev/sda
```

---

### Post by tech291083 on 2012-05-30
> **23dornot23d said:**
> 
 
2 ...... Divide the drive into 4 partitions ...... Primary .... Primary .... Primary .... Extended
 
3 ...... The Partition sizes are the main thing you do not want to have to go back and start re-sizing things afterwards .......
 
 
Primary 40 Gig .... Primary 40 Gig ..... Primary 40 Gig ( Extended  40 40 40 40 40 40 40 40 swap )
 
11 x 40 = 440 +  a swap 4 Gig ......... 444 Gig ....... and the Unallocated if you want another system at some point ...... you can never have enough Linux installs ....
 
 
Each system can use the same swap space ..... so only one swap space is needed ...... * ( do not use /home this will also be a nightmare as each system will try writing different config files there - the partitions are going to be busy enough without adding any more confusion to it )
 

 
Thanks a lot for the plan you have given to me. I will need some of it.

> **23dornot23d said:**
> I would say that nothing is pointless .... how do you know anything - without first trying.
 
 
I could also see something good coming from this - if more people tried it - then maybe one day it would create some form of environment where we can bring back together all the splits ......... and make LINUX united ......

 
Thanks for the kind words, I need them.

> **carl4926 said:**
> Install the legacy grub distros first, they may not boot if they are way down the table anyway, just let them install grub to / and continue with all the installs
 
Finish with Ubuntu if you want to use that. Or other grub2 distro

 
 
Yes, I agree with you 100%. My choice of the original 11 seems to be a faulty one now as you have rightly pointed out that some of them may be using legacy Grub and thus not install that easily as per my thinking. So I did some research on the net and tried to find out the Grub version of each of these 11 distros and here is what I got from Distrowatch site. Correct me if I am wrong here. Thanks.
 
Arch 2011.8.19 (Grub version 0.97) 
Damn Small Linux 4.4.10 (Grub version 0.91)
Debian 6 (Grub version 1.98)
Fedora 16 (Grub version 1.99)
Gentoo 11 (Grub version 0.97)
Knoppix 6.4.4 (Grub version 0.97)
Mint Linux 12 (Grub version 1.99)
OpenSuse 12.1 (Grub version 1.99)
Puppy Linux 5.3.1 (Grub version 0.97) 
Sabayon 8 (Grub version 1.99)
Ubuntu 12.04 LTS (Grub version 1.99)
 
 
So I need to change my plan a bit. Although I still want to install atleast 1 distro from the 5 types (RPM based, Debian based etc...) So it look like that I need to drop some of these 11 distros which use use the legacy Grub and replace them with the ones that use Grub 2 and belong to the same type. 
 
I am mentally ready to drop the following completely from the original list of 11 as they use legacy Grub.
 
Damn Small Linux 4.4.10 (Grub version 0.91)
Knoppix 6.4.4 (Grub version 0.97)
Gentoo 11 (Grub version 0.97)
 
Even if I drop the above 3 completely, I still have atleast 1 distro from their types for example Sabayon has Grub 2 so that I can drop Gentoo as they both belong to the same type. After dropiing the above 3, I still have atleast 1 distro left that belongs to 3 separate types namely Debian based, Gentoo based and RPM based. But if I have to drop Arch (Pacman based) and Puppy Linux (Slackware based) simply because they do not use Grub 2 then I must look for their replacements that use Grub 2.
 
Can anyone please suggest me replacements for these 2? I am thinking of either Salix OS or Zenwalk 7 as possible alternative to Puppy Linux, but I can't find for sure whether they use Grub 2 or not on Distrowatch site.
 
Chakra OS can be an alternative for Arch and it uses Grub 2 if I am correct, is that true?
 
So instead of 11, I will have 8 distros spread across 5 types (as I despearately want it that way to learn more about Linux) and I will still be happy in the end if all goes well, allowing me to achieve what I want ie to install 5 types of distros to the same hard drive. Send me your suggestions in terms of replacements for Arch and Puppy.
 
Thanks.

---

### Post by 23dornot23d on 2012-05-30
See if you can get these on the first three primary partitions to start with

1 .... Ubuntu KDE 12,04
2 .... Kahel OS * Arch (except it uses Gnome Shell basically) 
3 .... Mandriva 2010  ( This uses the old grub  and it links automatically to grub 2 in its boot menu )

Try these 3 first - there was a reason for this choice .....

1 .... Grub 2 and dead easy to install
2 .... Grub 1 and relatively easy to install and needs to be on a Primary partition
3 .... Grub 1 and chainloads automatically to Grub 2  from what I can remember

1 .... Debian based
2 .... Arch repos
3 .... RPM based

When the last on is loaded it lets you choose any of the 3 above ..... if you can get these working then you are a good way to achieving your goal ..... as we can always revive them installing without formating.

There are a few things that make it awkward ..... but we can stick all the grub 2 one in the extended after doing the above ...... give it a shot on a clean USB hard drive ...... always reformat and start again should things not go the way you want them to .....

Is easy if you had 2 drives .... from what I remember on my older computer 
Grub 1 based ended up on 1 drive ( on mine Kanotix Arch Slackware .... etc )
Grub 2 based ended up on the other ( Ubuntu Mint Sabayon Fedora .... etc )

---

### Post by Paqman on 2012-05-30
Regarding separate /home partitions, sharing one between any number of different installs is fine as long as you use a separate *user account* on each system. This keeps the config files nicely compartmentalised from each other.

I'm not sure I'd bother personally, but it would work fine.

---

### Post by 23dornot23d on 2012-05-30
Thats a interesting point and true ...... 

I tend to stick with the same Username with so many Distros.

But as you say /home can be done with multiple user names ..... 
I originally used to say have a seperate /home for data ....
as times changed and I got a Windows 7 install too ..... 

I added fat32 partitions for photography - music etc ......  this way meant all distros could get to the information .... without having file access errors due to file protection from one Linux Distro to the next.

Depends if you are keeping all the users from seeing the other users data in that case it can be better to use seperate users and /home

Personally I dropped using the /home a long time ago and could see no use for it on a one user system which
mine is.

---

### Post by tech291083 on 2012-05-30
Ok, if only 8 remain then, how should I plan the sequence of distros and partitions? I will have the following.
 
4 primary partitions as follows
 
1st primary partition - 1st distro (its Grub to be installed to MBR)
2nd primary partition - swap 4-10 GB
3rd primary partition - 2nd distro (its Grub to be installed to its / partition)
4th primary partition - extended one to have 6 logical partitions, 1 each for 6 distros.
 
I guess that as I start installing distros one by one as per the plan above, which is a temporary one, I will create the /, /home and /boot partitions depending upon the requirement or default behavious of a particular distro. Right now I am not sure as to which distros will require all of these 3 partitions or only 2 partitions namely / and /home. 
 
Thanks.

---

### Post by 23dornot23d on 2012-05-30
My swap is in the extended partition .... 4 Gig is usually enough for me ... this will depend on your onboard memory .... at least you should match it or have it 2 Gig bigger.

Partition 1 ..... Ubuntu ... (whichever Desktop Manager you prefer) - write grub to its partition sda1

Partition 2 ..... Kahel OS ... will go to its own partition if it will otherwise MBR ... and you will only have Kahel in Grub 1 till you install Mandriva 2010 .... which should then show Kahel and Ubuntu ..... from what I remember.

Partition 3 ..... Mandriva 2010 ... will go the MBR ..... and Take over. * when this goes in will you be able to see Ubuntu again to boot it ....

Then the rest is plain sailing * ( in extended )
 ....... the above should give a good start .....


Try on a clean drive I use USB HDs that boot by settiing it in the BIOS nowadays .....
Can always re-install Mandriva or Ubuntu back at a later point ...... 
and they will pick up the  other installs on the
drive as far as I know.  

Would hope this works out well ..... can only give you advice here from my own experiences
but I never let the system stop me from installing what I wanted .

Mine ..... root and swap all thats needed ......
/ and swap ..... (and only one swap space is needed in the extended partition) use gparted to set things up

Any Grub 1 installs are possible going to wipe the boot loader when they are installed .... so need following with
a Grub 2 install to see them again ..... ( and have a feeling they need to be in primary partitions to work properly )
may need a second drive ...... ( my main system was always using 2 drives - often a USB HD as the second )

> 
Is easy if you had 2 drives .... from what I remember on my older computer 
Grub 1 based ended up on 1 drive ( on mine Kanotix Arch Slackware .... etc )
Grub 2 based ended up on the other ( Ubuntu Mint Sabayon Fedora .... etc )


---

### Post by Paqman on 2012-05-30
> **tech291083 said:**
> Right now I am not sure as to which distros will require all of these 3 partitions or only 2 partitions namely / and /home. 


None require /home to be a separate partition. All you'll need is a single root partition for each distro and a single swap for the lot of them. A separate /home partition is optional, I certainly wouldn't create a separate one for each.

You don't need /boot partitions at all if you're just using the default filesystems without anything fancy.

You also don't have to have 4 primaries. There's no reason you couldn't just have one extended with everything inside it logical. It would be simpler IMO.

---

### Post by 23dornot23d on 2012-05-30
If Arch or Mandriva go into an extended partition and you try to run them from Grub 2 can you tell me what you do to get them to boot as it will be something I have not worked out yet.

Always seem to crash at some point when I have tried that ...... but not sure why it does that .

---

### Post by oldfred on 2012-05-30
Any installs with grub legacy should not be an issue. I actually did not like grub2 as it does not like to be installed to the PBR and I was using a grub only partition where I manually maintained menu.lst and chainloaded all my partitions. That made it easy to install grub legacy to the PBR and boot from one partition.

But grub2 has the os-prober and that works really well and you can still add manual entries in 40_custom. So for all the legacy grub systems install the grub boot loader to the PBR of the same partition and add an entry like this to 40_custom of the install with grub2's boot loader in the MBR.

Adjust drive & partition to yoru entry. Recognize grub legacy partitions start count at 0 and grub2 starts at 1 so partition numbering between grub legacy & grub2 is different.

```
menuentry "Chainload Other Systems Grub Menu on sdc1" {
set root=(hd2,1)
chainloader +1
}

```

Debian based systems put a link in root to the most current kernel that lets you direct boot the newest kernel.

More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)
```

menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by 23dornot23d on 2012-05-30
Is good - but I was trying to do it without having to do any editing at all .....

Will have a go now ...... this drive isnot big enough ....... on this old machine

But at the moment its got Dreamlinux - Ubuntu 9.04 - Kanotix and Arch on it ...... as you can tell it was a while ago so things change ......

I trust what you say Old-Fred ...... but I rarely have needed to alter the custom menu the way I now work.

But rarely go mad like I used to with installs. ....... 


Can add any of my USB drives to this do a update-grub - or change BIOS to boot from the USB drive and I have as many other systems as I need

> 
root@dream:/home/keith# update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.1.1-dream-3
Found initrd image: /boot/initrd.img-3.1.1-dream-3
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Arch on /dev/sda4
Found Debian GNU/Linux (4.0) on /dev/sda6

----------------------second drive can be added ... this was a USB I had handy but there are many more ..... dreamlinux seems to pick most up now which on this old machine controls the MBR and this needs updating when you update any other os to reflect the latest kernels on each partition.

Found Ubuntu 11.10 (11.10) on /dev/sdb10
Found Ubuntu 11.04 (11.04) on /dev/sdb11
Found Ubuntu 11.04 (11.04) on /dev/sdb12
Found Linux Mint Xfce Edition (1) on /dev/sdb13
Found Ubuntu 11.04 (11.04) on /dev/sdb14
Found Ubuntu 11.04 (11.04) on /dev/sdb15
Found Debian GNU/Linux (6.0.1) on /dev/sdb16
Found Ubuntu 11.04 (11.04) on /dev/sdb17
Found Arch Linux (rolling) on /dev/sdb3
Found Ubuntu 11.10 (11.10) on /dev/sdb5
Found Ubuntu precise (development branch) (12.04) on /dev/sdb6
Found Linux Mint 11 Katya (11) on /dev/sdb7
Found Ubuntu 11.04 (11.04) on /dev/sdb8
Found Ubuntu precise (development branch) (12.04) on /dev/sdb9
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
root@dream:/home/keith# 



Take that USB off then add another ....

> 
root@dream:/home/keith# update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.1.1-dream-3
Found initrd image: /boot/initrd.img-3.1.1-dream-3
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Arch on /dev/sda4
Found Debian GNU/Linux (4.0) on /dev/sda6
Found Ubuntu precise (development branch) (12.04) on /dev/sdb10
Found Ubuntu 11.04 (11.04) on /dev/sdb11
Found Ubuntu 11.10 (11.10) on /dev/sdb12
Found Ubuntu 11.10 (11.10) on /dev/sdb13
Found Ubuntu precise (development branch) (12.04) on /dev/sdb14
Found Fedora release 15 (Lovelock) on /dev/sdb15
Found Linux Mint Xfce Edition (1) on /dev/sdb16
Found Linux Mint 11 LXDE (11) on /dev/sdb17
Found Ubuntu 11.10 (11.10) on /dev/sdb2
Found Ubuntu 10.10 (10.10) on /dev/sdb7
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
root@dream:/home/keith# 


---

### Post by gordintoronto on 2012-05-30
Eventually, one of the distros will be in control of the Grub. That means, any time any distro gets a new kernel version, you will need to boot into the one which controls the Grub, and run sudo update-grub

My choice would be to install one distro, such as 64-bit Linux Mint 13 with Cinnamon (was that on the list?), and tell every other distro to not install Grub. They will whine and complain, then do what you want.

---

### Post by 23dornot23d on 2012-05-30
Yep in [COLOR=Blue][_**thread #43 **_]("http://ubuntuforums.org/showpost.php?p=11973009&postcount=43")[/COLOR]

I try to explain this situation ..... and as you say you need all the others to
stay dormant .... I achieve this by adding the boot to the partition for all of the others

> 
And keep the [COLOR=Blue]**Grub Boot on the partition with the OS**[/COLOR] ....... its easier  that way ..... trust me on this ....... doing it any other way will be  confusing at the very least ..... * NOTE ( you always need to go to your  [COLOR=Blue]**main OS and update grub when adding other OS's ...... but at least you  know which OS is controlling the BOOT this way**[/COLOR]. )

[COLOR=Red]**One OS > think I used Mandriva ....  this controls the Master Boot but  install it 3rd**[/COLOR]  ....... that way when you go into it and do a update  Grub it will find all the rest of the OS's you have ...... and it can  use the old and new Grub .....
Have set up a new drive today to check out what I said ..... and might be able to use something other than the old version of Mandriva to control them .... but that was the only Distro at the time I knew would chainload from Grub 1

I have DreamLinux on a computer though and it seems to handle things pretty well now .... will be tomorrow before I know for sure though ,,,,,

I do not like telling people what to do without being able to prove it to myself too . 

1 ..... Ubuntu 12.04 is on already
2 ..... Kahel OS .... loaded earlier .... but am upgrading now as it was out of date

Tomorrow may add Dreamlinux .... as its the only thing I have available at the moment. ( unless I can find some blank CDs so I can burn a new copy )

Good for something to do .... not sure I need all the other distros though
but will put a couple on here too ..... just to check things out .....

Could do a step by step ...... I covered the Kahel OS install and upgrade

(from [[COLOR=Blue]_**Thread #256**_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11804247&postcount=256") and upgrading it .....  [[COLOR=Blue]_**this is the full thread**_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1906762&page=26") scroll down to #256 )


[IMG]http://img441.imageshack.us/img441/3964/screenshotat20120531035.jpg[/IMG]


cannot find Mandriva 2010 and Dreamlinux is not picking up my wireless on the machine I
am currently using ...... so going to try [[COLOR=Blue]_**Magia 2 from here**_[/COLOR]]("http://www.mageia.org/en/downloads/get/?q=Mageia-2-i586-DVD.iso") ..... and see if it can find and use
the Kahel OS *(Arch) install

---

### Post by PeepNPope on 2012-05-31
...after all these years, this thread just pulled me from the woodwork.):P

Before  burning another distro proper, I'd *highly* suggest grabbing the  current parted magic, as it has the gdisk suite and a super grub disk  1/2, LILO, and a few more in its own Boot Menu. 

I'm actually in  the middle of trying to install >30 distros for a concept I've had  rolling around in my head that would require me to know GRUB2 like it  was the only shell that mattered. (I'm obviously biased, assume I  acknowledge LILO, Legacy, BSD loader, and even EFIShell will be  inevitably encountered. And that MS thing, if it goes anywhere) :wink:
I'm  sitting up in PMagic land after a failed 2nd attempt, but I've learned  an insane amount in the last 2 weeks, as I've been preparing to take  advantage of GPT. It's funny now how things change, it used to be  spreading a distro across 30 disks. If you are in a position to do so,  switch the disk to a GPT partition. Not only are there 128 partitions,  but they are all able to be primary. GPT also allows for a great deal of  disk format designations. Linux FS now has its own designation, among  several other changes and unique designations. On top of it all, you can  designate the partition number in no particular order which is great  when gparted looks like a barcode and you want some idea of where to  find the right 8G ext2 partition or to set up the first few ahead of  time so that you know where shared partitions of a type will always be.

I  honestly didn't realize how new this was, as I just kind of do my own  thing and... have never posted on a forum... but if I'm spending 13  hours a day for the last month planning and working on the backup of the  mess of partitions I've accumulated, then  find I'm in lightly tested  waters, I might be able to assist, rather on-the-fly. For reference, I'm  on an ASUS U56E for my first GPT experience. So if I'm oblivious to  seamless BIOS/UEFI quirks and compatibilities, take that into account if  your results differ. I'll have the desktop back up as soon as i can  find a working switch... or a proper case somewhere. (like mechanics who  drive deathtraps) :razz: 

Also,  I'm technically a total Linux n00b... perhaps casual interested Ubuntu  end-use auditor is a better description. I was, however, a DOS Junkie as  a kid, even building a full GUI out of barebones graphical launcher.  Then 95 came around and I've been mostly a WinZombie. 12.04 ended  that... in Beta. Bravo. The reason I rather inappropriately throw in my  intro is that I expect to be 50% insightful and 50% facepalm as GPT and  GRUB2/Burg are where I'm focusing, but as variable payloads, I'm  experiencing some of these OSes for the first time at the same time so  I'm liable to do some ridiculous things... and have already... I  think... Oh yeah... I cloned over Win7.  Nothing of value. Lit the fire,  really. But, you know, like that. So, first two runs:

Run #1 was  a fail before it got going... as far as planning goes. I did have a  LOVELY PC-BSD9 however, and I'd recommend a glance as it's quite a  lovely KDE native with an excellent package chooser on setup with most  favorites available and perhaps 6 stable and 4 unstable WMs to choose.  Its weakness in my case, however was the clarity of its partitioner.  Reading the handbook prior, I tried to set up the appropriate  partitioning scheme of boot-swap-root-tmp-user in pre-allocated  arbitrary but sequential Partitions of the appropriate types. (FreeBSD  boot, Swap, and UFS) PC-BSD, though the Desktop to FreeBSD9's Server,  was a little too "User-Friendly" and didn't seem to let me assign mounts  as I've become accustomed to of late. I'm quite glad I went for the odd  one out, first, as I wound up with the assumed "rest of disk as user"  that it wanted to give me. From the FreeBSD9 handbook, I'm to understand  that I would have been able to mount as I had expected. In the end...  First time around I jumped back into my P-magic and gdisked from  scratch.

Run #2 I focused more on setting up shared regions,  perhaps I bit more zealously than I should. Curious if the separation of  /tmp /boot, although originally done for legacy reasons would have the  benefit of keeping all the Linux boots in one place and keeping /tmp  extra /tmp. I'm sure it may have been fine that way for a couple of  distros with different kernels but remixes (deb/ubu/mint derivs) led to  eventual misconfiguration of a kernel for sandybridge between patched  and unpatched. It went surprisingly well beyond that, with a Slack, 3  Debs, and a Fedora (not in that order) before a grub 1.98 got completely  baffled.   

The scheme that time was laid out about like this on my 640GB
GPT8 ef02 - MBR,EFI-Boot (standard GPT start 8, because of FS type misunderstanding) 
GPT1 8300 - ext2 1G (will be for GRUB resources and a master script)
GPT2 8200 - Linux Swap 12G (2xRAM)
GPT3 8300 - ext2 4G /boot Shared
GPT4 8300 - ext4 8G / (1st)
GPT9 8300 - ext4 8G / (2nd)
GPT10 8300 - ext4 8G / (3rd)
etc... leaving a large amount of empty space. Some installers partition, a few don't.
GPT5 8300 - ext2 2G /tmp Shared
GPT6 0700 - Microsoft Compatible (A decent chunk to keep allocated if FAT was needed)
GPT7 a500 - disklabel (Mostly setting aside some space to see if that's like a BSD logical)
GPT127 8300 - ext2 16G "Frugals" (for puppies, etc)
GPT128 8300 - ext4 256G "Homes" (/home w/ diff user names + a shared common) 

While  I had the foresight to simplify home by putting it at the end, as well  as a place for my puppy addiction to flourish, you can see how quickly  128 primaries goes from boon to nightmare. I learned to designate GPT1  as an ef02, then I'll have GPT2  for my future Master Grub. 5 for swap  at the beginning, for ease of remembering, then 3 for frugals and 4 as  my leading distro, If I can decide on one. Then, time for some gaps. I'm  gonna start the "DOS/Win Zone" at 32 with a marker partition, a "BSD  zone" at 64, and at 96 a marker for any Solaris/Mac/Chrome/ etc, the  "rare" file systems. Finally, sticking with 128 for home. the "zones"  are for keeping things in order as best as possible as it quickly gets a  bit overwhelming depending on whether they're sorted by number or disk  location, especially in programs that don't read the label. I choose to  install each grub to the root partition and will super-grub my way  around for the moment, until I send an OS-Probed script to the  standalone grub once a bunch have been accumulated. Then I start what  this is prep for... :D 

For now this is experience with my  machine, but shortly I plan to start installing in VMWare and exporting  to partitions. This would probably save a LOT of the hassles, but I want  the hassles, so I'll save that for later. 

I hope something in  my tl;dr sparked some thoughts and saved some accidents. Happy  Boot-Surfing! Time to use P-Magic for Partitions, not for forums.   Actually, I may install it first. persistant toram from frugal. the 10  second boot recipe.

---

### Post by oldfred on 2012-05-31
@PeepNPope
If you are going to use gpt with BIOS, you need to add a 1MB bios_grub partition (ef02). I now add both efi & bios_grub as I now boot BIOS but any new drives may go into a new system and need that efi partition first. I just used gparted to create all my gpt drives but download gdisk to list and review partitions.

The main reason not to use gpt now is if you want Windows and do not have UEFI. Windows will only boot from gpt with UEFI.

If you want a grub only type partition you can use chainloading to grub legacy and the partition boot type entries on Debian based systems to reduce the maintenance on kernel updates.

---

### Post by 23dornot23d on 2012-05-31
I installed Mageia ..... and am running from it now ...... but the bootloader did not 
seem to pick up the other installs automatically ..... which is a shame .... but will try adding dreamlinux now and see if that does any better as I know this is ok for the boot on my older machine ..... ( but not having wireless set-up from the start makes my life a little more difficult on this machine )

Booted in and no partition table present .... 

Do not add Mageia ..... is my best advice ... I resized a partition to add it on ...... not only did it not detect the other systems it
managed to corrupt the MBR ......

Will rebuild it back now using Testdisk ..... but that is not a good way to start the day ....... 

[COLOR=Red][B]Always write a backup to a flash drive - first ......
( this can help for getting into the systems even when the MBR has gone on the main drive )
[/B][/COLOR] 
[IMG]http://img853.imageshack.us/img853/3462/aaagzd.jpg[/IMG]


[IMG]http://img593.imageshack.us/img593/4597/aaa1im.jpg[/IMG]

Note that once I did boot into Mageia I did get the wireless to work ..... and also managed to boot into Arch ..... but the thing
is the boot loader of Mageia froze Arch at the login screen  ....... 

So I am not impressed with that at the moment. ( I have a feeling it was the resize in Mageia that may be a problem .......
but be aware ...... as that is one install off my own list now ...... ( if it was that )

____________________________________________________________________________

Interesting ....  I am getting the same error on the Deep Search as a USER recently commented on ......

[http://ubuntuforums.org/showthread.php?p=11973624#post11973624](http://ubuntuforums.org/showthread.php?p=11973624#post11973624)

[IMG]http://img43.imageshack.us/img43/8381/aaa2mh.jpg[/IMG]

The deepsearch looks as if it is going ok now ...... will reset it up and try again tomorrow or tonight
re-installing with a different OS as the control OS .

As for GPT ....... it is not something that I have used it did not suit my purpose with removeable USB hard 
drives that can swap positions and sometimes are not even there at all ..... 

[http://en.wikipedia.org/wiki/GUID_Partition_Table#Operating_System_support_of_GPT](http://en.wikipedia.org/wiki/GUID_Partition_Table#Operating_System_support_of_GPT)

> 
In [computer hardware]("http://en.wikipedia.org/wiki/Computer_hardware"), **[GUID]("http://en.wikipedia.org/wiki/Globally_Unique_Identifier") Partition Table** (**GPT**) is a standard for the layout of the [partition table]("http://en.wikipedia.org/wiki/Partition_table") on a physical [hard disk]("http://en.wikipedia.org/wiki/Hard_disk"). It forms a part of the [Extensible Firmware Interface]("http://en.wikipedia.org/wiki/Extensible_Firmware_Interface") (EFI) standard, which is [Intel's]("http://en.wikipedia.org/wiki/Intel") proposed replacement for the [PC]("http://en.wikipedia.org/wiki/IBM_PC") [BIOS]("http://en.wikipedia.org/wiki/BIOS"). It is also used on some [BIOS]("http://en.wikipedia.org/wiki/BIOS") systems because of the limitations of [MBR]("http://en.wikipedia.org/wiki/Master_Boot_Record") partition tables. GPT allows for a maximum disk and [COLOR=Red]**partition size of 9.4 [zettabytes]("http://en.wikipedia.org/wiki/Zettabytes")**[/COLOR] (9.4 × 1021 bytes[[1]]("http://en.wikipedia.org/wiki/GUID_Partition_Table#cite_note-Redmondmag64bitQuestion-0")). As of 2010, most current [operating systems]("http://en.wikipedia.org/wiki/Operating_systems") support GPT, although some operating systems (including Mac OS X and Windows) require systems with EFI hardware to support *booting* from GPT partitions.
Often swap these between computers - but depends if the OP is going to have a Static setup with the 
same drives always present ...... 

( I know he wants to run them all off one drive here .... and will try my hardest to work towards a solution - will
listen to any comments and remarks made along the way as problem solving is always interesting
when there are a few people watching ..... and adding to it  )

With doing it on older systems and setups - I would have expected it to become easier with time ..... but who
knows ..... there are maybe more variables now with different partitioning options to use larger drives.

Who needs more than 1 Terra anyway !!! ( times change)

As of March 2012, no storage system has achieved one zettabyte of information.

Got it back again .....

> 
keith@keith-Aspire-7730ZG:~$ su
Password: 
root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-22-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-22-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-19-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-19-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Linux Mint Debian Edition (1) on /dev/sda12
Found Linux Mint 12 LXDE (12.04) on /dev/sda14
Found Linux Mint Xfce Edition (1) on /dev/sda16
Found Debian GNU/Linux (6.0.1) on /dev/sda17
Found Ubuntu precise (development branch) (12.04) on /dev/sda18
Found Debian GNU/Linux (6.0.1) on /dev/sda2
Found Ubuntu precise (development branch) (12.04) on /dev/sda20
Found Ubuntu 11.10 (11.10) on /dev/sda7
Found Arch Linux (rolling) on /dev/sdb2
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb3
Found Mageia 2 (2) on /dev/sdb5
done
root@keith-Aspire-7730ZG:/home/keith# 

Although it picked up the boot for each OS ..... none will boot now .....
Using Gparted now in one last attempt to sort the partition table out

> 
root@keith-Aspire-7730ZG:/home/keith# gparted
======================
libparted : 2.3
======================

** (gpartedbin:3620): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed

(gpartedbin:3620): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: The connection is closed
Can't have a partition outside the disk!
otherwise its start again ( so a days work may be lost )

The drive is brand new .... and as I said earlier always best to start on 
a fresh drive ( I always use USB HDs .. ) 

So we had Kahel OS and Ubuntu 12.04 ..... will get back to this position
once again and try with a different 3rd OS. already again ,,,, had to remove all the Mageia install

[IMG]http://img818.imageshack.us/img818/8411/aaa15.jpg[/IMG]

---

### Post by tech291083 on 2012-05-31
> **Paqman said:**
> None require /home to be a separate partition. All you'll need is a single root partition for each distro and a single swap for the lot of them. A separate /home partition is optional, I certainly wouldn't create a separate one for each.

You don't need /boot partitions at all if you're just using the default file systems without anything fancy.



Ok, I will not create separate /home partitions for any of the 8 distros and only create one /root partition for each of them. 

I will not create a separate /boot partition for any of them as I will stick to the default installation.

I was totally confused and that is why I needed some clarification on this, but you have given me a great and simple installation plan and I will try to stick to it.
 
4 primary partitions as follows
 
1st primary partition - 1st distro (its Grub to be installed to MBR)
2nd primary partition - swap 4-10 GB
3rd primary partition - 2nd distro (its Grub to be installed to its / partition)
4th primary partition - extended one to have 6 logical partitions, 1 each for 6 distros.
 

Here is what I have planned.

1st distro - Fedora 16
2nd distro - Mint 12
3rd distro - OpenSuse 12.1
4th distro - Debian 6.0.4
5th distro - Sabayon 8
6th distro - Ubuntu 12.04 LTS
7th distro - Not decided yet, but probably a Pacman based distro with Grub2 if any
8th distro - Not decided yet, but probably a Slackware based distro with Grub2 if any

I am sure that all the distros listed above have Grub2. So that they should recognize each other easily, I guess. Please let me know if I need to change the sequence of the distros. Thanks.

Now, as requested earlier, I want someone experienced here to suggest me a distro each for the Pacman type and Slackware type that is based on Grub2 if any out there. I am struggling with it, so please help me. 
 
Thanks.

Just a quick note, a few days back I installed Mint 12 32 bit as the only OS on the hard drive using the Use entire disk option during installation and did not create any partitions manually and stuck with the default. It remained the only OS on the hard drive for a few days, say 7-8 days. But when I typed a command in a terminal to see what version of Grub it had, I was shocked to see Grub 0.97. I thought Mint 12 uses Grub2 now, am I right here?

Thanks.

```

grub --version
Grub 0.97

```

---

### Post by ts3 on 2012-05-31
> **tech291083 said:**
> 7th distro - Not decided yet, but probably a Pacman based distro with Grub2 if any
8th distro - Not decided yet, but probably a Slackware based distro with Grub2 if any

Now, as requested earlier, I want someone experienced here to suggest me a distro each for the Pacman type and Slackware type that is based on Grub2 if any out there. I am struggling with it, so please help me. Thanks.

By the time you get to partition 7 you'll probably know enough to install Arch :)  It's doable with research and patience.

As an alternative you can look at Chakra, it just had a new release and uses pacman and grub2.  There's also Archbang, it also uses pacman but has grub legacy.  I have no experience with either Chakra or Archbang, my info is based on distrowatch which is a handy information source for stuff like this :)

One last thought: if you want the full pacman experience ignore any GUI front ends and just use it from the command line.  The arch wiki and the man pages for pacman have a lot of info.

---

### Post by tech291083 on 2012-05-31
> **gordintoronto said:**
> Eventually, one of the distros will be in control of the Grub. That means, any time any distro gets a new kernel version, you will need to boot into the one which controls the Grub, and run sudo update-grub


Yes, I agree with you 100% here, but then how do I decide as to which one should be my first distro and which one the last one, thanks.

---

### Post by ts3 on 2012-05-31
> **tech291083 said:**
> But when I typed a command in a terminal to see what version of Grub it had, I was shocked to see Grub 0.97. I thought Mint 12 uses Grub2 now, am I right here?

Interesting.  When you look in the /boot/menu/ directory what do you see?

Grub legacy has /boot/grub/menu.lst which in grub2 has been replaced by /boot/grub/grub.cfg

My old install of Mint 12 definitely had grub2.

---

### Post by tech291083 on 2012-05-31
> **oldfred said:**
> 
So for all the legacy grub systems install the grub boot loader to the PBR of the same partition and add an entry like this to 40_custom of the install with grub2's boot loader in the MBR.



I got the idea. Thanks.

> **oldfred said:**
> 
add an entry  like this to 40_custom of the install with grub2's boot loader in the  MBR.


Which install are you talking about here? Ubuntu 12.04 LTS or all the distros on my list that are Debian based ie Debian 6.0.4 and Mint 12?

As far as I know only Ubuntu has a file called 40_custom in /etc/grub.d directory, please correct me if I am wrong here.

Please suggest me the exact order of install based on your experience, it will really help me. Thanks.

---

### Post by critin on 2012-05-31
> but people have done this with 10-12 distros and they have told me on other forums that it is possible, At the moment, I'm running 6 distros, 5 are within an extended partition.  You can run as many as your disk will hold with the extended--at least I assume you can.  Only the size of my disk limits me. 

(Of course I use grub 2 only to avoid issues with booting)  

You just install one at a time until you're finished.  Don't let it get too complicated with extra partitions.  If you're only testing distros you shouldn't have to worry about /home, etc.  

Just save your personal stuff  in the main primary distro and you won't have to worry about it.

---

### Post by tech291083 on 2012-05-31
> **critin said:**
> If you're only testing distros you shouldn't have to worry about /home, etc.  


Yes, that is exactly what I intend to do here, thanks, you got my idea.

---

### Post by 23dornot23d on 2012-05-31
I started to lay it out again and gparted looks like this at the moment ......

[IMG]http://img217.imageshack.us/img217/7107/b6av.jpg[/IMG]

Found Arch Linux on /dev/sdb3
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5
Found Linux Mint Debian Edition (1) on /dev/sdb7
Found Dreamlinux-5 (1.0) on /dev/sdb8

These 4 are working ..... was about to load [[COLOR=Blue]_**Sabayon**_[/COLOR]]("http://mirror.freelydifferent.com/sabayon/iso/") next but my version is quite old
so will download the latest tonight.

---

### Post by oldfred on 2012-05-31
It helps to label partitions. Then you have a better idea of what is where. I also like to run bootinfo script before & after every install, so I know I installed to the partition I thought I was ( I have installed to the wrong one.).

```
fred@fred-Precise:~$ sudo blkid -c /dev/nul -o list
[sudo] password for fred: 
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs    WinXP    /mnt/cdrive    04B05B70B05B6768
/dev/sda2  ext3    backup   /media/backup  13a684e4-2849-4566-9528-21cd07028a9a
/dev/sda4  vfat    SHARE    (not mounted)  46CD-C9B2
/dev/sdb2  ext4    Maverick (not mounted)  0eea4e95-ea0a-4745-80d4-57bf2bbc9d69
/dev/sdb3  swap             (not mounted)  00c4e383-cf30-4b54-9a9f-d46953e3966e
/dev/sdb4  ext4    MavData  /media/MavData 431ba9e5-c72c-41c2-ba82-d8ee052336ff
/dev/sdc1  ext3    grub     (not mounted)  9e16ad9c-c5f8-4b5a-b2b3-20dfc71a422f
/dev/sdc2  ntfs    Shared   /mnt/shared    44332FD360AA9657
/dev/sdc4  ext2    bios_gpt (not mounted)  bbda6045-bb8a-4666-8bd4-04b3945ca581
/dev/sdc5  ext4    Karmic   (not mounted)  117412d5-2dbe-4011-8aec-ae310d1ee6c7
/dev/sdc6  ext3    Data     /mnt/data      a55e6335-616f-4b10-9923-e963559f2b05
/dev/sdc7  ext4    LUCID    (not mounted)  5e25282c-9c54-45df-9e79-514011e98648
/dev/sdc8  ext4    Test     (not mounted)  af29c61a-34e9-48eb-9c94-afcb4bb61582
/dev/sdc9  vfat    OLDG     (not mounted)  F6A6-705D
/dev/sdc10 ext4    newhome  (not mounted)  b8a7e331-a716-4ac1-bf58-6ac515606c6d
/dev/sdc11 swap             <swap>         09367687-86d1-4fd0-9b81-2787d3196159
/dev/sdc12 ext4    Puppy    (not mounted)  07e2a08d-37ca-4cf1-877b-f02b0eabcbca
/dev/sdc13 ext4    natty    (not mounted)  318fd41e-4210-4960-a0d9-ee9b48388d69
/dev/sdc14 ext4    kubuntu  (not mounted)  2b42c9ad-4304-4a8a-8991-08cfe35717ec
/dev/sdc15 swap             <swap>         2c05178d-1e0e-4ae8-80e6-a700dc0d6eb9
/dev/sdc16 ext4    oneiric  (not mounted)  63d146fd-1c63-4b31-95c5-ab52e2892283
/dev/sdc17 ext4    server   (not mounted)  63045773-e42a-46eb-9e96-b93428542527
/dev/sdc18 ext4             (not mounted)  117e0c31-7e16-4e8b-90b7-a3c688a34f26
/dev/sdd1  vfat    EFI      (not mounted)  7B30-5ACA
/dev/sdd3  ext4    Precise  /              adc013e9-a23d-4a36-849b-3faeac005667
/dev/sdd4  ext4    quantal  (not mounted)  3b72e3d4-3d56-469b-ad50-f13ac4f5f0d4
fred@fred-Precise:~$ 



```

---

### Post by 23dornot23d on 2012-06-01
Thats a good idea ..... 
I must admit it makes it a lot easier when looking at gparted to see what is what ..... 
remember to label them as you install them. ( not always good as a after thought )

Here is where I got to today ..... and have burnt the latest Fedora and Sabayon to RW+DVDs 

```
root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Arch Linux on /dev/sda3
Found Ubuntu 12.04 LTS (12.04) on /dev/sda5
Found Linux Mint Debian Edition (1) on /dev/sda7
Found Dreamlinux-5 (1.0) on /dev/sda8
done
root@keith-Aspire-7730ZG:/home/keith#
```


Fedora 15 is now on ..... ( it has its boot in its own partition )

This only picks up from the Dreamlinux install  when you do update-grub it adds Fedora ok

If you do it from the Ubuntu 12.04 install ...... Fedora does not show up in your boot menu .....

Ok added Sabayon .... this is a very similar install procedure to Fedora 
both Sabayon and Fedora ( the boot was put onto the partition with the OS )

[IMG]https://diasp.org/uploads/images/scaled_full_0f4574551be9497f4bc1.gif[/IMG]

Not tried the update-grub on Ubuntu yet but this is the result from the Dreamlinux install

will post the one I get in a few minutes from the Ubuntu 12.04 update-grub 

```

root@dream:/home/keith# update-grub
Generating grub.cfg ...
Found background image: /usr/share/images/desktop-base/desktop-grub.png
Found linux image: /boot/vmlinuz-3.1.1-dream-3
Found initrd image: /boot/initrd.img-3.1.1-dream-3
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Arch on /dev/sda4
Found Debian GNU/Linux (4.0) on /dev/sda6
_______________________________________________ USB Dirve

Found Ubuntu 12.04 LTS (12.04) on /dev/sdb11
Found Gentoo Base System release 2.0.3 on /dev/sdb12
Found Arch Linux (rolling) on /dev/sdb3
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5
Found Linux Mint Debian Edition (1) on /dev/sdb7
Found Dreamlinux-5 (1.0) on /dev/sdb8
Found Fedora release 17 (Beefy Miracle) on /dev/sdb9
grep: input file `/boot/grub/grub.cfg.new' is also the output
done
root@dream:/home/keith# 

```and here is the Ubuntu update-grub

For some reason it fails to see Fedora ( but it picked up Sabayon - Gentoo install ok  )

```

root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 9.04 (9.04) on /dev/sda1
Found Arch on /dev/sda4
Found Debian GNU/Linux (4.0) on /dev/sda6
Found Dreamlinux-5 (1.0) on /dev/sda7
Found Gentoo Base System release 2.0.3 on /dev/sdb12
Found Arch Linux (rolling) on /dev/sdb3
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5
Found Linux Mint Debian Edition (1) on /dev/sdb7
Found Dreamlinux-5 (1.0) on /dev/sdb8
done
root@keith-Aspire-7730ZG:/home/keith# 

```Drive now looks like this

[IMG]http://img811.imageshack.us/img811/8208/peargparted.jpg[/IMG]


Ubuntu 12.04
Sabayon 8
Arch ( Kahel OS ) fully updated with Gnome Shell and KDE installed
Rebecca Black * ( +Wayland - KDE edition V004 )
Linux Mint Debian 10
DreamLinux 5
Fedora 17
Pear (Comice OS) based on Oneiric

8 OSs working ..... took 2 days ..... with one hiccup on a Distro that now is not in
my listing ....

________________________________________________

```
root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-20-generic
Found initrd image: /boot/initrd.img-3.0.0-20-generic
Found linux image: /boot/vmlinuz-3.0.0-16-generic
Found initrd image: /boot/initrd.img-3.0.0-16-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 12.04 LTS (12.04) on /dev/sda10
Found Gentoo Base System release 2.0.3 on /dev/sda11
Found Ubuntu 12.04 LTS (12.04) on /dev/sda12
Found Debian GNU/Linux (wheezy/sid) on /dev/sda13
Found Arch Linux (rolling) on /dev/sda3
Found Ubuntu 12.04 LTS (12.04) on /dev/sda5
Found Linux Mint Debian Edition (1) on /dev/sda7
Found Dreamlinux-5 (1.0) on /dev/sda8
Found Ubuntu 11.04 (11.04) on /dev/sdb1
done
```

A few notes ..... (  I prefer a USB hard drive for lots of installs - easy to do and portable between computers with similar graphics cards - mine are all nvidia - but I tend to stick to the nouveau driver for most of the installs .... Pear has Nvidia-current as I quite like this install )

Slackware - unless this has changed a lot - do not use it ..... can  seriously mess the update-grub up ...... in fact it will stop it and
come back with an error ...... that stops the grub getting updated. 
( This may have changed in later ones like puppy - but I did not go there - if someone else knows for sure that this is fixed now
let us know ...... )

1 ..... Do not be worried if they all the OS's do not show up after installs like Kahel OS - only one will show in the boot menu
until you load in Ubuntu 12.04 or Rebecca Black ...... as either of these will become the main install .... all others put grub to their
own partitions when they will let you.

2 .... Make a copy of the MBR once a few have been loaded .... do this using a flash USB key and use the grub-install /dev/sdb
in my case but you need to check by doing df to see what the USB key was loaded as.

3 .... Do not resize partitions that exist using anything other than gparted ( doing it in some of the installs gives bad results )

4 .... Once you have loaded a few ..... just go into your main distro that controls the MBR and do a update-grub

Hope you have got a few loaded now ..... and as I said before - 

Start with  3 - Kahel needs to be in one of the first Primary Partitions.

Rebecca Black was my first install
Kahel OS was second
Dreamlinux
Mint 10 in my case as it was handy ( but there are later 12 and 13 now )
[COLOR=Blue]**Ubuntu 12.04 then ( to the MBR .... ) this will then show all the installs and control from here on will be with it.**[/COLOR]
Fedora and Sabayon use a similar install I did these one after the other ( grub goes on their own partitions ) 
Pear was the last install ..... and I have room for another ..... but may keep the last part free .....

Best quick guide I can give - as getting used to all the different installs may take a little of getting your head around them.
Fedora - picks up using a older version of Dreamlinux ..... but Ubuntu does not want to show it as being there for some reason.

Leave a message if anything odd happens .... every machine is different - I have a hybrid machine and would not even attempt
to use it for doing this lot on it ..... but once done can take this USB to it and see what will work ok ..... its the graphics more than
anything that can be a problem with that ..... as it uses both intel and nvidia to conserve energy. 
( My Acer Aspire z7730 seems good for most installs though and I have had this a while so know what
to expect if something does play up at all. )

If anybody wants to see the Bootinfoscript results they are here
for download and perusal .....

```
[https://sites.google.com/site/23dsources/home/source-lists/RESULTS2.txt?attredirects=0&d=1](https://sites.google.com/site/23dsources/home/source-lists/RESULTS2.txt?attredirects=0&d=1)

 

These were from Dreamlinux (Dream3) .... may give a clue as to why Fedora picks up here 

sdb9: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub2 (v1.99)
    Boot sector info:  Grub2 (v1.99) is installed in the boot sector of sdb9 
                       and looks at sector 454197592 of the same hard drive 
                       for core.img. core.img is at this location and looks 
                       in [COLOR=Blue]**partition 99**[/COLOR] for .
    Operating System:  Fedora release 17 (Beefy 
                       Miracle) Kernel on an ()
    Boot files:        /boot/grub2/grub.cfg /etc/fstab

menuentry "Fedora release 17 (Beefy Miracle) (on /dev/sdb9)" --class gnu-linux --class gnu --class os {
    insmod part_msdos
    insmod ext2
    set root='(/dev/sdb,msdos9)'
    search --no-floppy --fs-uuid --set=root e626bf8f-b575-4252-b270-3db2f55f2eae
    linux /boot/vmlinuz-3.3.4-5.fc17.x86_64 root=/dev/sdb9
    initrd /boot/initramfs-3.3.4-5.fc17.x86_64.img
}

```



but not in Ubuntu

Here is the Ubuntu update-grub showing what it picks up ...... from the Asus hybrid machine using Ubuntu 
note no Fedora ( the sed errors appeared after loading Pear - loaded a second and a second sed appeared
so know it is relative to that one ..... the boot still works fine - but would be interesting to know what has 
caused this.

```
root@keith-K53SV:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-23-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-23-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-22-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-22-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-20-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-20-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-19-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-19-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
sed: -e expression #1, char 12: unterminated `s' command
sed: -e expression #1, char 12: unterminated `s' command
Found Windows Recovery Environment (loader) on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 11.04 (11.04) on /dev/sda6
Found Ubuntu precise (development branch) (12.04) on /dev/sda8
Found Ubuntu precise (development branch) (12.04) on /dev/sda9
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb10
Found Gentoo Base System release 2.0.3 on /dev/sdb11
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb12
Found Debian GNU/Linux (wheezy/sid) on /dev/sdb13
Found Debian GNU/Linux (wheezy/sid) on /dev/sdb14
Found Arch Linux (rolling) on /dev/sdb3
Found Ubuntu 12.04 LTS (12.04) on /dev/sdb5
Found Linux Mint Debian Edition (1) on /dev/sdb7
Found Dreamlinux-5 (1.0) on /dev/sdb8
done
root@keith-K53SV:/home/keith#
```

---

### Post by oldfred on 2012-06-03
I know in Ubuntu you have to install the lvm driver to get boot script to 'see' lvm partitions. Normal desktop installs of Ubuntu do not include LVM nor RAID drivers.
 for LVM:
sudo apt-get install lvm2
for RAID:
sudo apt-get install mdadm

then grub2's os-prober may see the boot files of Fedora. Some here have suggested to preformat before installing Fedora and not use LVM. LVM offers advantages (and complications) on resizing partition but with multiple booting and many other partitions having one small LVM just adds the complications without any of its potential advantage. I do not use LVM.

---

### Post by 23dornot23d on 2012-06-03
Cheers oldfred ty ..... thats probably it then

added both ( then rebooted ) then did update-grub - still does not see it.

 keith@keith-Aspire-7730ZG:~$ su
Password: 
root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
sed: -e expression #1, char 12: unterminated `s' command
sed: -e expression #1, char 12: unterminated `s' command
Found Ubuntu 12.04 LTS (12.04) on /dev/sda10
Found Gentoo Base System release 2.0.3 on /dev/sda11
Found Debian GNU/Linux (wheezy/sid) on /dev/sda13
Found Debian GNU/Linux (wheezy/sid) on /dev/sda14
Found Arch Linux (rolling) on /dev/sda3
Found Ubuntu 12.04 LTS (12.04) on /dev/sda5
Found Linux Mint Debian Edition (1) on /dev/sda7
Found Dreamlinux-5 (1.0) on /dev/sda8
done
root@keith-Aspire-7730ZG:/home/keith#

Might re-install Fedora and do as you say   -  with no LVM ....... 
and see if Ubuntu will find it then ...

---

### Post by carl4926 on 2012-06-04
If you mount the fedora /
then run update-grub
it'll pick it up

---

### Post by 23dornot23d on 2012-06-04
Give the man a CIGAR ..... yes ...... thats a winner Thank you ..... and wireless works too
8 distributions working in all - but with 4 distributions with wireless working out of the box now.

[IMG]http://img405.imageshack.us/img405/6458/screenshotfrom201206041i.png[/IMG]

Ubuntu 12.04 .... Arch ( Kahel OS ) ..... Comice 4 ( Pear ) and Fedora 17 ....... 

keith@keith-Aspire-7730ZG:~$ su
Password: 
root@keith-Aspire-7730ZG:/home/keith# update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found memtest86+ image: /boot/memtest86+.bin
sed: -e expression #1, char 12: unterminated `s' command
sed: -e expression #1, char 12: unterminated `s' command
Found Ubuntu 12.04 LTS (12.04) on /dev/sda10
Found Gentoo Base System release 2.0.3 on /dev/sda11
Found Debian GNU/Linux (wheezy/sid) on /dev/sda13
Found Debian GNU/Linux (wheezy/sid) on /dev/sda14
Found Arch Linux (rolling) on /dev/sda3
Found Ubuntu 12.04 LTS (12.04) on /dev/sda5
Found Linux Mint Debian Edition (1) on /dev/sda7
Found Dreamlinux-5 (1.0) on /dev/sda8
Found Fedora release 17 (Beefy Miracle) on /dev/sda9
done
root@keith-Aspire-7730ZG:/home/keith#

---

### Post by PeepNPope on 2012-06-06
Alright. After just a little more time to plan and Read the Friendly  Manuals, I'm currently sitting at 6 primary-installed, 2 Frugals, 1 heck  of a go at PC-BSD (I can mostly blame an outdated command and a  misspelling in the grub/btx scripting), 1 with issue post-install, and  the Win 8 preview in VMware as I wouldn't want any illegitimate MS  Certificates to go loading Flame on me... But I still had to glimpse  THAT train-wreck if we're gonna sell free like never before. I'd say a  premonition of the UEFI/MS sham prompted my recent fascination with  loading a ridiculous number of distros for the sake of catering to  multiple interests on-the-spot. At the moment, I'm looking at covering  at least one each of a Win-Like, Security, Studio, media center,  extra-light, Internet only, gaming only, cutting edge show-off,  No-maintainance, Novelty/Retro and one with a very modular installer for  no frills but features. In going for loosely defined types I've been  going through distrowatch with only a certain amount of concern for the  type of linux. However, all installed currently are Buntus/Mints/Debs.  Of them, with kernels from 2.6 to current stable, only Dream Studio  12.04 has been unsuccessful, and that due to "Low Graphics Mode" issue  which I'm not yet sure how to patch up. With an Intel Wimax 6150+,  typing 'sudo rmmod iwlwifi && sudo modprobe iwlagn  bt_coex_active=0' at startup has become habitual, albeit pretty  universally effective.

My next disk install will be Slackware 13.3.7. Reading just the Main  Readme and Hints, I'm looking very much forward as the documentation is  uniquely well written, first accusing the reader of being a n00b in  playfully dismissive way and then thoroughly explaining a topic in  detail under various contexts. Fun.

PC-BSD is made much easier by  xfs support as an intermediate, though I did find a GParted that  covered UFS/GPT and correctly identified the partition. I may build the  disk inside a partition manually with gdisk next go. I suspect however  that the 'FreeBSD' instead of 'kfreebsd', and the 'frebsd' in the Grub  Script indicate a likeliness that another typo might be present. It's  Grub-1.99 so it *should* be rather straightforward given the  circumstances.  The Frugals are Puppies, Arcade 10 and Slacko 5.3.3,  both installed without hint of issue, though I've been into Puppies  longer than most distros, and it can be unnerving or confusing the first  time you "install"  a squash and pupsave. Here's what my partition  madness looks like atm.

[IMG]http://img713.imageshack.us/img713/8197/screenshot2pb.png[/IMG]
By [kniknoo]("http://profile.imageshack.us/user/kniknoo") at 2012-06-06

1 is a gpt  bios-grub which is where I installed Burg so I'd notice immediately if  that Grub was overwritten. 2 is a placeholder for now. 5 is SWAP. 3 for  Frugals. 4 is first distro because most boot disks will at least look  that high. From there every ext4 has a grub on the partition and was  detected by my main grub's os-prober. 

Finally, 128 has the homes  of each install under unique names, as well as a public home so I can  access files in a uniform fashion and easily experiment with the  occasional unconventional setup in context. Also, while playing with  gdisk while the disk was empty, I apparently gdisked /dev/sda128 and  saved a GPT inside of it. The result is that every partition tool has  recognised it both as a partition on the disk and as a separate disk  named /sda128. A: Is this a disaster waiting to happen, and if so, only  if I deviate from accessing it the same way? B: As BSD does much the  same thing with a disklabel, would this be a viable way to trick some  special cases into installing on what it thinks is a single disk? C: Is  FS type label for my benefit or the installer's? Could I label it as,  say... DellRepair or something "rare" so that nothing bothers to probe  it as a partition with an ext2 GPT FS inside posing as a unique disk?  Prolly not a multi-Linux situation in which it would be necessary, but I  could see the use in several others along this thread... against all  odds, I wonder if the protective MBR is willing to believe that it's the  beginning of the first disk if it can't see anything but itself as the  hard drive. 

I get the feeling that a certain Proprietary OS just  determined Linux a bigger threat than the ages old commercial arch  rival. Dabbling in Open Source and mostly throwing low punches in the  process? I shall find a suitable, yet legal quarantine for what I'll dub  frontdoor.MS-CA.bs(FU.IE) It has a much nicer ring than Windows 8  Certified and is sure to scare off Mac Users when it's lovingly referred  to as such. Right now is the beginning of a perfect storm... I'm  already angling on the "too hard to learn Win4Lifers" by showing them  KDE next to the default desktop as they notice with disgust that "IE's  where the start menu's supposed to be" ;) 

Back to the 115 remaining partitions...

Edit: yep, total forum n00b. I'll figure out this simple picture posting business soon enough.

Edit: trying this again with a long-overdue photo host. Thank you @23D for "step 1-2-3" response. "get a host" could've taken hours of poring over near-clones instead of just doing it. :) I'll let you know how Slack goes, "newbie" install mode by itself is apparently a day-long read, but I may as well get a full description of everything in a logically dependent order.

---

### Post by 23dornot23d on 2012-06-06
Sounds great ....

To post the screenshots - use something like[[COLOR=Blue]_** imageshack**_[/COLOR]]("http://imageshack.us/content_round.php?page=done&l=img217/7107/b6av.jpg") .....

choose 640 x 480 and use jpgs ..... keeping the images at their lowest load up sizes - check using properties.

Pick the picture or image and use the direct link after you have set up a free account with them.

Cut and paste the direct link that they supply underneath your uploaded screenshot into the pop up that appears after selecting the only icon with what looks like a mountain and a sun on it in the ubuntu forum editor that pops up when creating a reply to a thread.

Hope that helps ..... let us know how slack picks up in the  grub .... 
I had lots of problems after a Slack install but maybe something else went wrong as it
is not the simplest of installs.

Will watch with interest see how many OS's you get upto ..... seems like the way you are doing it may be something I would consider for my desktop machine but not using removeable USB hard drives ..... as  I think that would not work using the method you
describe ..... but would love to find out I am wrong in that assumption.

I have similar feelings too about the way Microsoft is changing hardware.

Already its been proved that the System is still not secure - so what is the point in
them making computing more difficult for other OS's to get in ...... true control they have the lock and you have to get keys off of them ..... 

Then in the future they change the lock and upgrade their own keys easily , and maybe fail to do it for others ..... or do it after a brief wait ....... this sounds terrible.

Like someone having the lock to your garage and the only way you can get to your own things is to beg for a key ..... or pay for one. ( that you never really needed in the first place ) .......

[https://www.google.com/search?q=windows+8+Peter+Kleissner%27s]("https://www.google.com/search?q=windows+8+Peter+Kleissner%27s")

This proves its not effective - so its not for security as it fails to stop the real hackers
and it only needs one hacker to get in and thats it - like he gives his own keys to everyone ......  a skeleton key .......

More linux Distros More linux users ...... then Linux can start to lock Windows users out ...... in the same way they are attempting to do it now.

Now would that be fair ..... shame Linux plays by all the rules and someone else is constantly setting new ones to make the game go in their  favour.

I do not mind any competition as long as its fair ..... maybe linux should start making new rules ..... Keys to their Servers that Microsoft has to buy.

---

### Post by tech291083 on 2012-06-25
ok Friends,
 
Sometimes things are just there to be seen and yet you do not see them. I was furiously looking for a list of distros with the latest Grub version 1.99 (Grub 2 I think) and was not able to get one. But now I have found it very easily on a popular site called distrowatch.com
 
Here how I found the list. 
 
[http://distrowatch.com/search.php?pkg=grub&pkgver=1.99](http://distrowatch.com/search.php?pkg=grub&pkgver=1.99)
 
One just has to search for distros using a certain package ie Grub etc with the version no. It is quite easy but it took me so many days. Hope you do not have to struggle like I do foolishly all the time.
 
Now I will now as to which distro I shall select for each of the 5 categories as discussed earlier by me. Thanks. 
 
I still want to install atleast one distro from each of the 5 categories to the same hard drive. The goal is still very much alive. wish me luck and shower me with your suggestions. Thanks.

Hi Friends,
 
I have decided to install the following 5 distros and each of them represents one each from the original 5 categories/code base as I stated at the start of the thread.
 
Ubuntu 12.04 LTS (Debian-based)
Sabayon 8 (Gentoo-based)
Chakra Linux 2012.05 (Pacman-based) 
Fedora 16 (RPM-based)
Vector Linux 7 (Slackware-based)
 
Now I am ready to install all the above 5 distros to a new SATA 500 GB HDD. I have not created an exact order in which I am going to install them, but I know that each of them has the latest Grub2 so they should install and work easily with each other. Correct me if I am wrong here. 
 
Thanks.

Latest:
 
I have already successfully installed the following...
 
First I created a swap partition with 5 GB space.
 
Then I created a primary partition with about 92 GB of space. Here I installed Vector Linux 7 (Slackware-based) and its grub to MBR.
 
I then created another primary partition of around 92 GB and here I installed Chakra Linux 2012.05 (Pacman-based) and its Grub to /boot folder as mentioned during the installation by the install package called Tribe. The exact words were "Tribe will install Grub2 on the same hard drive where your /boot folder is located"
 
Both are working fine with each other, both are being displayed on the boot menu and boot are easy to boot so far so good.
 
Now I am going to install Sabayon 8 (Gentoo-based) to an extended partition (Standard partition within it) as 4 the primary partition is always an extended one. Let me know your views/suggestions. 
 
Thanks.

---

