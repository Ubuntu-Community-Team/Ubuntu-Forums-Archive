---
title: "which ubuntu is best for my system?"
date: 2010-05-01
forum: General Help
---

### Post by thegutterpoet on 2010-05-01
I have purchased a new desktop, which is running windows 7. The processor is a 64 bit duo core 3.oghz...4gb ram...I was going to set aside 100gb of the hard drive for the latest version of ubuntu.

Which one should I get? do i need a 64 bit version??? As i have a 64 bit chipset???

or is it best to get the latest release, which I think is 32 bit???

any advice appreicated...

---

### Post by cascade9 on 2010-05-01
You probably have a Core2Duo, in which case you have a 64bit CPU (the older core duo is 32bit only). 

Chipsets dont come in 32bit/64bit- if your CPU supports 64bit, the chipset will as well. 

All the newer ubuntus come in both 32bit and 64bit versions (I wouldnt be suprised if all the versions have a 62bit version, but the oldest ubuntus are no longer supported so dont use them). 

I'd use 64bit if your CPU supports it, but you can use 32bit on a 64bit x86 CPU.

---

### Post by dino99 on 2010-05-01
less trouble with many apps if you have a 32 bits distro, simply install the "pae" kernel to fully use the ram installed

---

### Post by thegutterpoet on 2010-05-01
so what are the advantages of a 64 bit version and the 32 bit version???

when i went to the
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) site, i could only see the 32 bit 10.04...(my processor is a core duo e8400)

---

### Post by polki@mac.com on 2010-05-01
If your puter is a 64 bit machine, then use 64!

---

### Post by polki@mac.com on 2010-05-01
On the subject:

[http://en.wikipedia.org/wiki/64-bit](http://en.wikipedia.org/wiki/64-bit)

---

### Post by cascade9 on 2010-05-01
> **dino99 said:**
> less trouble with many apps if you have a 32 bits distro, simply install the "pae" kernel to fully use the ram installed

There is *very* little trouble with 64bit programs these days...its not 2006 anymore. 

> **thegutterpoet said:**
> so what are the advantages of a 64 bit version and the 32 bit version???

when i went to the
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download) site, i could only see the 32 bit 10.04...(my processor is a core duo e8400)

The 32bit/64bit debate is long, and goes back years. To cut it short- 

32bit- The installer should work on any x86 computer that meets the minimum requirements, some programs only have 32bit version. Getting rare these days though....

64bit- can see 4GB+ of RAM (32bit can see 4GB+ with the PAE kernel, but it is a bit of a hack), faster (even if you have less than 4GB or RAM). 

There is options for 32bit and 64bit at the ubuntu site- click on "alternative download options" link to see the 64bit option. 

BTW, with 10.04 just coming out the direct d/l will be pretty slow due to traffic- torrents should be a lot faster (and its a better way to get .iso file in general IMO anyway).

---

### Post by polki@mac.com on 2010-05-01
I agree, 64bit and torrent is the way to go. If, and I really mean "IF", you have any trouble, just search these forums.

---

### Post by Dayofswords on 2010-05-01
and here is the torrent
[http://torrent.ubuntu.com:6969/file?info_hash=%A1B%5E%0Df03l%DD%9F%B3%20%F3%FF%F1%03%00%98%97Z](http://torrent.ubuntu.com:6969/file?info_hash=%A1B%5E%0Df03l%DD%9F%B3%20%F3%FF%F1%03%00%98%97Z)


(the same torrent already in .torrent)
[http://ubuntu.osuosl.org/releases/10.04/ubuntu-10.04-desktop-amd64.iso.torrent](http://ubuntu.osuosl.org/releases/10.04/ubuntu-10.04-desktop-amd64.iso.torrent)

seed if you can please

---

### Post by thegutterpoet on 2010-05-01
thankyou for the advice. i am downloading the 64 bit 10.04.

---

### Post by thegutterpoet on 2010-05-02
Ok...i have a 320gb hd. I need to repartition before installing ubuntu. I was going to use gparted program.

How much space should I leave for the alreadyinstalled windows 7 OS???

I was going to annex 80gb for ubuntu.
 Does this eeem enough?

Or does ubuntu 10.04 come with an option during install to repartition the hard drive for me automatically, whilst making sure that windows 7 isnt deleted or dAMAGED?"

---

### Post by Ginsu543 on 2010-05-02
It's somewhat difficult to answer your question because it really depends on how you intend to use your Windows 7 and Ubuntu OSes. Are you going to use Windows 7 primarily? or Ubuntu? Will you have files you need to access from both Windows 7 and Ubuntu?

If it were me, I'd maybe try this partition scheme:
1) 100 GB Windows 7 partition
2) 25 GB ext4 / partition
3) 75 GB ext4 /home partition
4) 120 GB NTFS data partition (accessible from both Windows 7 and Ubuntu)

It's a good idea to have separate / and /home partitions because it gives greater flexibility and ease of use when upgrading later.

Also, the above partitioning scheme neglects a swap partition (which you should have, especially if you want the ability to hibernate). The size of the partition depends on the amount of RAM you have installed. The size of the swap partition should be about twice the size of the installed RAM. So, if you have 2 GB of system RAM, you should set aside ~4 GB of swap space.

---

### Post by thegutterpoet on 2010-05-02
I willprobably use ubuntu more often, for everytning other than dreamweaver work for a website forum I run and maintain.

I have 4gb RAM installed.

Can ubuntu installer do the repartitioning for me? or should I use the G-parted program??

---

### Post by dino99 on 2010-05-02
> **thegutterpoet said:**
> Ok...i have a 320gb hd. I need to repartition before installing ubuntu. I was going to use gparted program.

How much space should I leave for the alreadyinstalled windows 7 OS???

I was going to annex 80gb for ubuntu.
 Does this eeem enough?

Or does ubuntu 10.04 come with an option during install to repartition the hard drive for me automatically, whilst making sure that windows 7 isnt deleted or dAMAGED?"

first you need to choose a good formatting tool: [http://partedmagic.com/](http://partedmagic.com/), install it on cd or usb stick, its a nice tool in case of trouble in future.

usually Ubuntu is installed that way :

- prepare partitions with external prog (partedmagic)
- built 3 partitions:
1) / which is the main one (root), need to be bootable and is ext3 or ext4 formated with about 12 go
2) swap: about twice the real ram but max 2 go
3) /home which is your data partition: as much go that you need

- download the "alternate" image and install it on usb ( unetbootin) if you are able to boot on usb, or burn it on cd (4x max speed). the "alternate" let you customize your installation, so as you have previously prepared your partitions and noted their names (/dev/sda or so), its easier to make a safe installation and place grub, when asked, on the / mbr partition.

if you still have other distro installed (windows, ...), after reboot with ubuntu, open a terminal (alt+f2) and run:

sudo grub-mkconfig && update-grub

on next reboot you will see grub menu to choose on which distro you want to boot, on single installation you need to hold "shift" key down at end of bios process to popup grub menu (hidden by default)

---

### Post by SnickerSnack on 2010-05-02
> **Ginsu543 said:**
> The size of the partition depends on the amount of RAM you have installed. The size of the swap partition should be about twice the size of the installed RAM. So, if you have 2 GB of system RAM, you should set aside ~4 GB of swap space.

Why?

---

### Post by thegutterpoet on 2010-05-02
damn. i thought it would be more simple...on my old xp based laptop i used gparted to make a new partition, then chucked in the ubuntu disk, it installed on the free partition, then after installation i had the option of booting ubuntu or windows every time i turned the laptop ON.

I guess I cannot use that routine this time around?

---

### Post by dino99 on 2010-05-02
> **SnickerSnack said:**
> Why?

ubuntu and all Linux distro use the ram as much they can, and only if needed, they use swap, but not so often and its very rare to use more than 1 go in normal use, of course it can be different with very heavy prog (design, virtual 3d, ...) but every one prefer to add more ram than more swap (swap is far slower)

---

### Post by Ginsu543 on 2010-05-02
You certainly can use the same routine. It's just that if you do it that way, your / and /home directories will be on the same partition, and I've just found it beneficial to have them on separate partitions. A separate /home partition allows you to install upgrades (for example, when 10.10 comes out) without having to reset all your personal settings which are stored in your /home directory. It makes upgrading a lot easier and faster.

---

### Post by dino99 on 2010-05-02
> **thegutterpoet said:**
> damn. i thought it would be more simple...on my old xp based laptop i used gparted to make a new partition, then chucked in the ubuntu disk, it installed on the free partition, then after installation i had the option of booting ubuntu or windows every time i turned the laptop ON.

I guess I cannot use that routine this time around?

that's was the old time  :P

---

### Post by Ginsu543 on 2010-05-02
> **SnickerSnack said:**
> Why?
I realize that with large RAM sizes available today, you really don't need a large swap partition. You need a swap file at least the same size as system RAM if you want to hibernate. For me, I just use the x2 rule and be done with it since hard drive space is so ridiculously huge these days, 1 or 2 extra GB of swap space doesn't really matter.

---

### Post by zaphod777 on 2010-05-02
> **dino99 said:**
> first you need to choose a good formatting tool: [http://partedmagic.com/](http://partedmagic.com/), install it on cd or usb stick, its a nice tool in case of trouble in future.

usually Ubuntu is installed that way :

- prepare partitions with external prog (partedmagic)
- built 3 partitions:
1) / which is the main one (root), need to be bootable and is ext3 or ext4 formated with about 12 go
2) swap: about twice the real ram but max 2 go
3) /home which is your data partition: as much go that you need

- download the "alternate" image and install it on usb ( unetbootin) if you are able to boot on usb, or burn it on cd (4x max speed). the "alternate" let you customize your installation, so as you have previously prepared your partitions and noted their names (/dev/sda or so), its easier to make a safe installation and place grub, when asked, on the / mbr partition.

if you still have other distro installed (windows, ...), after reboot with ubuntu, open a terminal (alt+f2) and run:

sudo grub-mkconfig && update-grub

on next reboot you will see grub menu to choose on which distro you want to boot

I thought the Ubuntu installer will prompt to use the unused space on the HDD alongside the existing install. 

I would say just go with the defaults and don't over think partitioning. I always use the default and I have no issues. 

I have 4 GB of RAM and rarely ever use the swap I could do a separate partition for /home but just never bothered. 

Also one problem with x64 can be flash please see this guide for installing flash. 

[http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/](http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/)

I run x64 and flash is really the only problem I ever have and the guide I posted is how to install it properly.

---

### Post by dino99 on 2010-05-02
> **Ginsu543 said:**
> I realize that with large RAM sizes available today, you really don't need a large swap partition. You need a swap file at least the same size as system RAM if you want to hibernate. For me, I just use the x2 rule and be done with it since hard drive space is so ridiculously huge these days, 1 or 2 extra GB of swap space doesn't really matter.

even with hibernate, only settings are saved, not the whole system

---

### Post by dino99 on 2010-05-02
> **zaphod777 said:**
> I thought the Ubuntu installer will prompt to use the unused space on the HDD alongside the existing install. 

I would say just go with the defaults and don't over think partitioning. I always use the default and I have no issues. 

I have 4 GB of RAM and rarely ever use the swap I could do a separate partition for /home but just never bothered. 

Also one problem with x64 can be flash please see this guide for installing flash. 

[http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/](http://astoryworthtelling.wordpress.com/2009/12/11/flash-broke-again/)

I run x64 and flash is really the only problem I ever have and the guide I posted is how to install it properly.

That's why i'm giving the safest way to make an install. There is so much users following the default installer and blindly press the "enter" key and then come back here to complaint and are whining because they have overwrite their other distro or drop grub over windows bootloader  :lolflag:

---

### Post by zaphod777 on 2010-05-02
True true. The installer should ask you which bootloader to use. But I think over complicating it with partitioning first using a different CD and all of the cl stuff can turn of new users depending on how techie they are. 

I'm just sayin ... :)

I guess there are ups and downs to any way you do it.

---

### Post by cascade9 on 2010-05-02
> **Ginsu543 said:**
> If it were me, I'd maybe try this partition scheme:
1) 100 GB Windows 7 partition
2) 25 GB ext4 / partition
3) 75 GB ext4 /home partition
4) 120 GB NTFS data partition (accessible from both Windows 7 and Ubuntu)


Bit too much for / IMO (I'm using 4.1GB for / here) I wouldnt go past about 10-12GB. 

/home might be a bit bigger than needed as well, but thats not so important (and a swap would be good as well, but you mentioned that). 

If it was me...this is what I would do (and no, I'm not suggesting this is the 'best' way, just how I would do it)- 
50-75GB NTFS win7
Ram x 2.5 NTFS Win7 Swap (just the NTFS partition, with the swapfile forced to use this. You wont be able to use the whole avaible space unless you do various hacks...so you make it RAM x 2.5 and set the swap at Ram x 2)
12GB / (probably EXT4)
RAM x 2 Linux swap.
25-50GB /home (EXT3 or 4)
Everything else NTFS data partition. 

> **zaphod777 said:**
> I thought the Ubuntu installer will prompt to use the unused space on the HDD alongside the existing install. 

I would say just go with the defaults and don't over think partitioning. I always use the default and I have no issues. 

There is no 'defaults' just 'automatic partitioning'. It works.....sort of....but it slices up the HDD based on the amount of avaible spce. I cant recall the exactly mathamatical way it does that (eg 25% for /, 10% for sawp, 65% for /home...just made them up). 

I never use automatic partitioning as it hasnt got a brain, and can make stupid decisions. Better to let think it out and do things manually IMO.

---

### Post by zaphod777 on 2010-05-02
This is what I have for my partitions I suppose the swap size is overkill but I never needed to change it. I rarely use more than a couple hundred MB of swap. 

[IMG]http://lh6.ggpht.com/_sjlVRfKJcmw/S9078rgWL_I/AAAAAAAABAg/VxV-66daBIs/s800/Screenshot.png[/IMG]

---

### Post by Hobodavel on 2010-05-02
Is ubuntu, xbuntu or kubuntu still friendly to low end machines as i have a mecer (223ll0) laptop with: 
1GB of ram,
2GHz single core processor,
not sure what graphics but runs 9.10 fine.

but having problems with installing 10.04 as it cant even reach installation the screen goes black.

Please Help..

---

### Post by thegutterpoet on 2010-05-02
Does ubuntu 10.04 installer come with a program to repartition??

or am i better off using g-parted first to create three partitions...One for windows 7, one for my files...and a third for ubuntu???

then sticking in the ubuntu image on a disc, and pointing it to the partition i want.

I was going to give 100 for windows 7, 100 for files, and 100 for ubuntu...???

---

### Post by cascade9 on 2010-05-02
> **Hobodavel said:**
> Is ubuntu, xbuntu or kubuntu still friendly to low end machines as i have a mecer (223ll0) laptop with: 
1GB of ram,
2GHz single core processor,
not sure what graphics but runs 9.10 fine.

but having problems with installing 10.04 as it cant even reach installation the screen goes black.

Please Help..

You would do better to create your own thread. But in short, ubuntu/xubuntu would work fine on that system...kde4 might be sluggish unless you have a decent video card

> **thegutterpoet said:**
> Does ubuntu 10.04 installer come with a program to repartition??

or am i better off using g-parted first to create three partitions...One for windows 7, one for my files...and a third for ubuntu???

then sticking in the ubuntu image on a disc, and pointing it to the partition i want.

I was going to give 100 for windows 7, 100 for files, and 100 for ubuntu...???

Ubuntu comes with a partitioner. 

Really, you want more than 3 partititions. 100 for windows 7? OK. !00 for a data partiton? Not a problem (though I would put the data partition at the end of the drive, the closer to the end the slower the partition is- better to have OSes early on the drive, they need the speed more than a data partition). 

100 for ubuntu? Possible- if you have no swap partition and have only a / partition. Better to have /, /home and swap.

---

### Post by thegutterpoet on 2010-05-02
will I need a swap partition????

---

### Post by dino99 on 2010-05-02
> **thegutterpoet said:**
> will I need a swap partition????

really have you read post 14 or am i wasted time  :lolflag:

ubuntu, linux are "free" and you too , but without swap, if needed and dont found, well you get a nice crash and lost your current work , thats all, not the end of world anyway.

---

### Post by Hobodavel on 2010-05-02
you do not need a swap partition if you have more than a gig and a half of ram

---

### Post by dino99 on 2010-05-02
> **Hobodavel said:**
> you do not need a swap partition if you have more than a gig and a half of ram

do you need a brain

---

### Post by cascade9 on 2010-05-02
> **thegutterpoet said:**
> will I need a swap partition????

'Need'? No. Is it a very good idea to have a swap partition? Yes. 300GB to use...who is going to notice 4-8GB of HDD sapce 'missing'? 

Please tell me you arent going to not have a swap just because you dont want to make any more partitions. 

> **Hobodavel said:**
> you do not need a swap partition if you have more than a gig and a half of ram

The amount of RAM has got very little to do with it.......there isnt some point where you can go 'I now have XXXX sized RAM, I dont need swap anymore'.

---

### Post by tristan.cole on 2010-05-02
in my experience with using ubuntu, the only thing the swap partition does is make my system freeze up and slow down. so what i have found is that if you are an average user there is no reason to have a swap partition if you have alot of RAM

---

### Post by Ginsu543 on 2010-05-02
I can vouch for the fact that you don't need a swap partition in that both my Dell netbooks (one with 4GB SSD and the other with 8GB) are currently running great without swap. My portable has 2GB of ram while my server only has 1GB. Yet, neither has ever crashed or frozen. But as cascade9 said, for my desktop 4-8GB (or 15GB in my case) of hard drive space isn't going to be missed at all when I have 4TB (plus a 1.5TB external backup drive) at my disposal.

---

### Post by Animal X on 2010-05-04
> **Ginsu543 said:**
> It's somewhat difficult to answer your question because it really depends on how you intend to use your Windows 7 and Ubuntu OSes. Are you going to use Windows 7 primarily? or Ubuntu? Will you have files you need to access from both Windows 7 and Ubuntu?

If it were me, I'd maybe try this partition scheme:
1) 100 GB Windows 7 partition
2) 25 GB ext4 / partition
3) 75 GB ext4 /home partition
4) 120 GB NTFS data partition (accessible from both Windows 7 and Ubuntu)

It's a good idea to have separate / and /home partitions because it gives greater flexibility and ease of use when upgrading later.

Also, the above partitioning scheme neglects a swap partition (which you should have, especially if you want the ability to hibernate). The size of the partition depends on the amount of RAM you have installed. The size of the swap partition should be about twice the size of the installed RAM. So, if you have 2 GB of system RAM, you should set aside ~4 GB of swap space.
similar to what i have:
1)100G Vista Aero
2)85G Mepis ext3 
3)215G Data NTFS
4)100G Ubuntu

i notice ubuntu takes care of all it's own partitions inside of a logical volume automatically when installed to unallocated space, so i make the first 3 partitions, install ubuntu, then windows, then mepis, and i use the grub from mepis. this has been the most hassle-free setup for my situation.

---

### Post by CoreyB. on 2010-05-04
> **Ginsu543 said:**
> The size of the partition depends on the amount of RAM you have installed. The size of the swap partition should be about twice the size of the installed RAM. So, if you have 2 GB of system RAM, you should set aside ~4 GB of swap space.

The formula I use is mentioned here: [http://kbase.redhat.com/faq/docs/DOC-15252]("http://kbase.redhat.com/faq/docs/DOC-15252")

In summary, twice your RAM if your ram <= 2GB, if > 2GB, amount of RAM + 2GB.

---

### Post by pete_m on 2010-05-15
Thanks to all for the interesting material in this thread .  .

I'm an EEE PC user planning an imminent move to Ubuntu Lucid  .  . 
in the hope of performance improvements and the benefit of tieing in to a fresh LTS release.

i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all

i'm therefore hoping to be able to upgrade my machine rather than do a fresh install.  .i've been following some threads about this and i'm swapping repositories in and out while running apt-get -s to preview forthcoming upgrades. . .

on the basis of it's not broken  don't fix it -  i shall probably wait for the next release of Lucid before taking the plunge. . there are only a few areas where i feel my present set-up may be a little behind the times.

I've been setting up repositories for individual packages to get the stuff i'm particualrly interested in directly from the development repos. 

Incidentally my present system with 1Gb RAM  has no swap space but has been consistently stable if not always fast .. the worst that happens is that firefox gives up the ghost 

i'm still comparitively new to Linux so any observations and guidance will be much appreciated .. 

First screenshots - more soon - of my work in progress at 

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

---

