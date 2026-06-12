---
title: "Is a 10GB 3.5 IDE HHD good for Xubuntu"
date: 2012-08-04
forum: General Help
---

### Post by argonvegell on 2012-08-04
Hello, I'm a newbie to Linux in general, so I want to try it out, however, I don't want to touch the 320GB Hard Drive installed on my family's Gateway GT5432 Desktop, which has Windows Vista installed on it. Here's the specs of my family's computer:

Computer Type: Tower (Mini)
Included Drives: DVD+-RW DL
Operating System: Microsoft Windows Vista Home Premium
Included Devices: Keyboard, Mouse
Video Chipset: NVIDIA GeForce 6150 SE
Processor Type: AMD Athlon 64 X2
Processor Speed: 2600
Installed Memory: 1GB
Hard Drive Size    320GB

Okay, I have this old broken HP Vectra Pentium III Desktop and have managed to  remove the Maxtor 10GB 3.5 IDE HHD, I'm planning on buying a 3.5 External  IDE/SATA HHD Enclosure for it and doing a full installation  of Xubuntu on it, using the VirtualBox tutorial from Youtube (I will provide a link below).
My questions:
(1) is Maxtor 10GB 3.5 IDE HHD good for Xubuntu since it's lightweight? I have heard of Lubuntu, but the only thing that bugs me is that there's no LTS, I don't want to upgrade every 18 months.
(2) is Gateway GT5432 Desktop good for Xubuntu?
(3) the Maxtor 10GB 3.5 IDE HHD's filesystem is NTFS, because Windows XP is  installed on it, can the Xubuntu installer remove Windows XP during installation?
(4) is the VirtualBox tutorial from Youtube good? I would like to know from the experts. The reason I want to use the VirtualBox method is because I don't want to touch or even remove the 320GB Hard Drive installed on my family's Gateway GT5432 Desktop.

Here's the link to the VirtualBox tutorial: [http://www.youtube.com/watch?v=SnB4NrJrw3Q&](http://www.youtube.com/watch?v=SnB4NrJrw3Q&)
And the author of this tutorial even provided a video of the finished product, Ubuntu installed on an External USB Hard Drive: [http://www.youtube.com/watch?v=HEDu7Ti3M00](http://www.youtube.com/watch?v=HEDu7Ti3M00)

Thanks, will be waiting for a reply.

---

### Post by Dylan1473 on 2012-08-04
1) Xubuntu should do fine on a 10 gig drive as long as you don't want to do too much on it. Storing tons of games or videos or whatever will obviously not work well. An external drive will probably be slower than an internal one, though.

2) 1GB memory is very low for a computer in general but Xubuntu's minimum is I believe 256MB so it should be fine. Otherwise your specs should be more than sufficient for Xubuntu. What you're doing with Vista on only 1GB of RAM or what 1GB of RAM is doing next to some of your other specs I don't know. Was that a typo?

3) Xubuntu can remove Windows XP during installation or be configured to boot alongside it. Given the small size of the drive and the fact you're apparently not concerned about keeping XP I'd overwrite it. Xubuntu will also format the drive properly during install.

4) I admit I didn't watch the VirtualBox tutorial but I'm not sure why you'd need VirtualBox to install it on a physical machine. Xubuntu can run from a liveCD (meaning you can try it from a flash drive or disc without having to install it first) and then be installed to a drive of your choice. It's also possible to literally install it within Windows using the Wubi installer without risk to Windows then choose to boot into either at start - no new partitions needed or anything.

---

### Post by critin on 2012-08-04
Sure, it will work on 10 GB, it won't leave much room for photos, videos etc., but it will work fine with files.  

Are you going to install on a virtual on the 10GB?  Or directly on the HDD?  You're talking of both here, so...if you use the 10 gb, it won't touch the other drive.  Be sure you've chosen the correct drive when in the install.

Yes, burn the iso to dc or usb flash and boot to TRY first, to check things out.  See if things are working ok, then install it to USE ENTIRE DISK and it will install over XP if that's what you're wanting to do.

buntu's work on almost any pc, brand doesn't matter.  

Enjoy, it's easy to install.

---

### Post by dcstar on 2012-08-04
> **argonvegell said:**
> 
...........
Okay, I have this old broken HP Vectra Pentium III Desktop and have managed to  remove the Maxtor 10GB 3.5 IDE HHD, I'm planning on buying a 3.5 External  IDE/SATA HHD Enclosure for it and doing a full installation  of Xubuntu on it, using the VirtualBox tutorial from Youtube (I will provide a link below).
..........

You would have to be half way to mad to use an ancient, probably 90% worn out drive.

If you care about your time and the data that will exist, get some decent hardware rather than rely on old rubbish.

---

### Post by mastablasta on 2012-08-04
> **argonvegell said:**
> 
Installed Memory: 1GB


> 
(4) is the VirtualBox tutorial from Youtube good? I would like to know from the experts. The reason I want to use the VirtualBox method is because I don't want to touch or even remove the 320GB Hard Drive installed on my family's Gateway GT5432 Desktop.


this will present a problem. you won't be able to run it inside virtual box if that was your plan. because host (vista) needs it's ram (porbably the whole 1GB) and guest (linux) needs it's ram. for xubuntu to run decently in vbox you would need at least 3 GB with that vista. if not more.,

i have XP with 2GB ram and can only give 512MB (well maybe a bit more) to Xubuntu. because XP needs 1 GB ram to run fluently+vbox needs it ram and then what is left is used for xubuntu.

in my opinion it is better to simply to boot from CD/USB and install it on that external disk. it has the same risk that you need to select the porpper disk where you will install as well as select the propper disk where you will pu the GRUB boto loader. this will also use the ext4 file system rather than virtual disk on NTFS as is the case in wubi or vbox.

if you aboslutelly od not want to touch you family disk i suggest you simply unplug it during installation, install to external HD and then plug it back in. then to boot in ubuntu you need to set the second (external) disk to boot first from the bios boot menu. that way vista disk won't be touched and i will stay "safe".

GRUB can also recognise winodws so you can permanently set it to boot from external disk and then update it's grub so it adds windows to it. a menu will then appear on boot asking you which system you want to use. you can also modify it so that first system is windows and if no one touches it for example for 10 seconds it will boot windows.

---

### Post by argonvegell on 2012-08-04
> **Dylan1473 said:**
> 1)

4) I admit I didn't watch the VirtualBox tutorial but I'm not sure why you'd need VirtualBox to install it on a physical machine. Xubuntu can run from a liveCD (meaning you can try it from a flash drive or disc without having to install it first) and then be installed to a drive of your choice. It's also possible to literally install it within Windows using the Wubi installer without risk to Windows then choose to boot into either at start - no new partitions needed or anything.

Thank for the the reply, the author of the tutorial said that using  VirtualBox to install on an External HHD is the safest method.

> **critin said:**
> 
Are you going to install on a virtual on the 10GB?  Or directly on the  HDD?  You're talking of both here, so...if you use the 10 gb, it won't  touch the other drive.  Be sure you've chosen the correct drive when in  the install.


Directly on the External HHD, this is what the author said on the video description, "Note: When setting up the virtual machine, don't create a virtual hard  drive as this will cause Ubuntu to install on the virtual HDD and not on  the external HDD".

> **dcstar said:**
> You would have to be half way to mad to use an ancient, probably 90% worn out drive.

If you care about your time and the data that will exist, get some decent hardware rather than rely on old rubbish.

I would buy a new HHD if I could, but I don't have the money.

> **mastablasta said:**
> this will present a problem. you won't be  able to run it inside virtual box if that was your plan.

My plan is to install directly on HHD and not run it inside VirtualBox.

> **mastablasta said:**
> if you aboslutelly od not want to touch you family disk i suggest you  simply unplug it during installation, install to external HD and then  plug it back in. then to boot in ubuntu you need to set the second  (external) disk to boot first from the bios boot menu. that way vista  disk won't be touched and i will stay "safe".

That's the problem, unplugging it is a no no, my family doesn't want me to touch the insides of the computer.

---

### Post by Dylan1473 on 2012-08-04
Technically, there's less risk to actually opening the computer and detaching the drive temporarily than there is to installing with the drive inside. However, neither method is particularly dangerous - it's just a matter of selecting the right disk, which shouldn't be a problem. You'll be fine as long as you take note of the differences between the drives, and you should be informed both of the size of the drives and the operating systems installed during the installation. As long as you pay attention to what you're doing you won't overwrite Vista.

Having actually watched the video now, I wouldn't really recommend this VirtualBox thing - it seems like it  just adds a bunch of extra steps to eliminate a virtually nonexistent  risk. That said, the bits of the tutorial actually shown in the video (he doesn't seem to elaborate on the process of starting the virtual machine in VirtualBox at all which is odd since this is probably more difficult than the Ubuntu install itself) are valid. Of course, if you want to use this method you can; it may marginally reduce the risk of installing, but it will be slower and more complicated than it needs to be.

Note that, like mastablasta said, 1GB of RAM will present a problem. While technically better than the absolute minimum required for Vista this is less than ideal even for Vista alone, and it certainly won't be enough to handle both Vista and a Virtual Machine without very serious problems. If you really are running on 1GB of RAM (next to a dual core 64 bit processor and a discrete graphics card? Did someone take some memory out of the computer or something? Or was that a typo?) a memory upgrade might be a wise purchase for Vista's sake, though I suppose this would involve opening up your computer as well. If that's an option you can easily find an extra 2 to 4 gigs to put in your computer on [_Newegg_]("http://www.newegg.com") or other sites for $10-$20. Barring a memory upgrade you should probably just use the conventional installer.

---

### Post by mastablasta on 2012-08-05
> **argonvegell said:**
> Thank for the the reply, the author of the tutorial said that using  VirtualBox to install on an External HHD is the safest method.

The author of the tutorial should know i mean they made a video after all and have a youtube account ;-) 

> 
Directly on the External HHD, this is what the author said on the video description, "Note: When setting up the virtual machine, don't create a virtual hard  drive as this will cause Ubuntu to install on the virtual HDD and not on  the external HDD".

I guess that's an option. never tried it myself.

> 
I would buy a new HHD if I could, but I don't have the money.

Don't worry, 10 GB is enough. i set aside 8 GB and it still has about 3GB left after some cleaning. a cheap option to fiddle arround is to get a 16 or 32GB USB stick and install to that.

> 
My plan is to install directly on HHD and not run it inside VirtualBox.

on the video the guy runs it in virtual box as i see. it might be easier to simply install 
it to your external disk. like i said all you need to take care is to choose the correct disk on install (the 10GB one) and to put grub (boot loader) on external disk.
[/QUOTE]

here is how install looks like: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)
here is how install in vbox looks like: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)

i hope oyu get the pictures as they are not loading for me again :-/

---

### Post by argonvegell on 2012-08-05
> **Dylan1473 said:**
> Technically, there's less risk to actually  opening the computer and detaching the drive temporarily than there is  to installing with the drive inside. However, neither method is  particularly dangerous - it's just a matter of selecting the right disk,  which shouldn't be a problem. You'll be fine as long as you take note  of the differences between the drives, and you should be informed both  of the size of the drives and the operating systems installed during the  installation. As long as you pay attention to what you're doing you  won't overwrite Vista.
> **mastablasta said:**
> it might be easier to simply install 
it to your external disk. like i said all you need to take care is to  choose the correct disk on install (the 10GB one) and to put grub (boot  loader) on external disk.

Thanks for the reply guys, that is one of my fears, installing it on the wrong HHD, and screwing up the MBR on the internal HHD. A lot of the guides I see using Google, are strongly recommending I disconnect the Internal HHD, which as I said before, I'm not allowed to do, so how do I make sure I'm installing it in the right HHD and how do I make sure I'm installing GRUB in the external HHD? Are there guides that can show me how to install on an External HHD without removing the Internal HHD?

> **Dylan1473 said:**
> If you really are running on 1GB of RAM (next to a dual core 64 bit  processor and a discrete graphics card? Did someone take some memory out  of the computer or something? Or was that a typo?

After re-reading my post, yes it was a typo, my bad, my memory is 2GB RAM.

> **mastablasta said:**
> here is how install looks like: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)
here is how install in vbox looks like: [http://www.psychocats.net/ubuntu/installing/](http://www.psychocats.net/ubuntu/installing/)

i hope oyu get the pictures as they are not loading for me again :-/

Thanks for the additional information, unfortunately I cannot get the screenshots, so I will read them if and when I can see the images, thanks!

---

### Post by Ubun2to on 2012-08-05
> **Dylan1473 said:**
> It's also possible to literally install it within Windows using the Wubi installer without risk to Windows then choose to boot into either at start - no new partitions needed or anything.

I dislike Wubi, as it stores all the data on the actual Windows partition. You never can remove Windows if you have Wubi, unless you have another partition ready to move your virtual drive to.

---

### Post by Dylan1473 on 2012-08-05
I don't really remember for sure, but I believe in the install you'll be asked which disc to put grub on. They'll be labelled by size again and the external one will probably be labelled as /dev/sdb. I have not used the automatic installer in some time, though.

If you have 2 gigs of RAM you will probably be able to run Vista and the virtual Xubuntu machine. I'd say assign only 512MB of RAM to the virtual machine tops - that should be plenty for Xubuntu anyway. Vista claims the minimum is 512MB I believe but I wouldn't care to test that. It may be painfully slow, but you'll only need to use it for the time you take to install Xubuntu if you're set on doing it that way. It will remove the need to put any thought into what disc you're installing it on and what disc you place GRUB on. Worst case scenario you put your boot loader onto the virtual machine and have to reinstall/fix GRUB before you can use Ubuntu. Just remember that the boot loader will go on /dev/sdb with the virtual machine (assuming you don't have any other USB devices or disk drives mounted) and you should be fine. Also, be sure to mount the USB drive within the virtual machine from your devices menu or the second drive won't appear.

---

### Post by argonvegell on 2012-08-06
> **Dylan1473 said:**
> I don't really remember for sure, but I believe in the install you'll be asked which disc to put grub on. They'll be labelled by size again and the external one will probably be labelled as /dev/sdb. I have not used the automatic installer in some time, though.

If you have 2 gigs of RAM you will probably be able to run Vista and the virtual Xubuntu machine. I'd say assign only 512MB of RAM to the virtual machine tops - that should be plenty for Xubuntu anyway. Vista claims the minimum is 512MB I believe but I wouldn't care to test that. It may be painfully slow, but you'll only need to use it for the time you take to install Xubuntu if you're set on doing it that way. It will remove the need to put any thought into what disc you're installing it on and what disc you place GRUB on. Worst case scenario you put your boot loader onto the virtual machine and have to reinstall/fix GRUB before you can use Ubuntu. Just remember that the boot loader will go on /dev/sdb with the virtual machine (assuming you don't have any other USB devices or disk drives mounted) and you should be fine. Also, be sure to mount the USB drive within the virtual machine from your devices menu or the second drive won't appear.

Okay thanks everyone, I will try to install Xubuntu, when I get a HHD Enclosure, thanks!:)

---

### Post by argonvegell on 2012-08-06
I have some more questions and inquiries, using Windows Vista, is it possible to format my External HHD in Windows Explorer, in order to avoid having to deal with the old Windows XP installation on my HHD during Xubuntu installation? Will formatting delete everything on my HHD, including Windows XP? I would like to have a clean HHD when doing this.

When I have installed Xubuntu on my External HHD, what is the first things I should do? And is there a Xubuntu User Manual available? I have downloaded the Ubuntu 12.04  manual from here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) Is that manual compatible with Xubuntu?

---

### Post by Dylan1473 on 2012-08-06
I don't know how to do partitioning from within Windows (though yes, it is possible) but the LiveCD you've got includes with it a tool called GParted that you can use to empty the disc. All you have to do is delete the partition with Windows XP on it (it'll be listed as the 10GB one). The Xubuntu installer is also capable of doing this on its own, but if you'd prefer not to deal with two Windows installations during the install you can just run GParted. You can try your luck at partitioning the disc as well if you so choose, but again, this can be handled by the Xubuntu installer. Feel free to come back and ask here before finalizing your partitions if you want to double check that everything is okay, regardless of which method you used.

Regarding the user manual: the Ubuntu manual will be somewhat applicable within Xubuntu, but Xubuntu uses a totally different desktop environment so some instructions based on doing stuff within the GUI might be harder to follow. You may actually find Xubuntu easier to get a hang of anyway though as the desktop environment it uses (XFCE) is a bit more traditional than the Ubuntu default, Unity.

---

### Post by kurt18947 on 2012-08-06
> **argonvegell said:**
> I have some more questions and inquiries, using Windows Vista, is it possible to format my External HHD in Windows Explorer, in order to avoid having to deal with the old Windows XP installation on my HHD during Xubuntu installation? Will formatting delete everything on my HHD, including Windows XP? I would like to have a clean HHD when doing this.

When I have installed Xubuntu on my External HHD, what is the first things I should do? And is there a Xubuntu User Manual available? I have downloaded the Ubuntu 12.04  manual from here: [http://ubuntu-manual.org/](http://ubuntu-manual.org/) Is that manual compatible with Xubuntu?

The desktop is different (Xfce) than Ubuntu but I think the installer is the same.  I'd second the suggestion to boot a live session and use Gparted to prepare the 10 GB. drive.  Just make VERY sure you're dealing with the correct drive.  Most like NOT sda, more like sdb, sdc etc.  The sure give-away will be disk size.  

You might also consider creating a backup of the Vista partition(s) with clonezilla.  If the Vista partition is behaving well, now is a good time to back it up.  With a backup - or two - if something does happen for example the hard drive dies through no fault of your own, you can buy a new hard drive, restore the clonezilla image and look like a hero :KS.

---

