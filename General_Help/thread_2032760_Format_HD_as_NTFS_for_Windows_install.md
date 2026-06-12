---
title: "Format HD as NTFS for Windows install"
date: 2012-07-24
forum: General Help
---

### Post by mychack on 2012-07-24
backstory: I bought a netbook w/ Windows7 installed, royally screwed something up three hours later when editing shellstyles, lost all ability to use Windows. I installed Ubuntu using a USB, and I've been using 12.04 for the past couple days. Windows7 simply runs better on this netbook, so I want to switch back. I've got my copy of Windows7 on a USB, and got it to boot through BIOS, but when it comes time to pick the HD for install, I get this message:

**Windows cannot be loaded on this HD space. Windows must be installed to a partition formatted as NTFS. Windows cannot install on HD, the partition is an unrecognized type.**

I imagine this means I need to format my 500GB HD as NTFS-- but I cannot do it with gparted. The option to partition the main HD simply isn't an option. (note: I installed the NTFS drivers to format my USB, and it worked. It just won't allow me to partition the HD with NTFS)

Is there a way to partition my HD as NTFS with gparted or some other process?

---

### Post by coffeecat on 2012-07-24
> **mychack said:**
> 
I imagine this means I need to format my 500GB HD as NTFS-- but I cannot do it with gparted. The option to partition the main HD simply isn't an option.


You need to explain this better. Creating one partition and formatting it NTFS in your 500GB HD is perfectly possible in Gparted.

Let me make a guess. Are you running Ubuntu from the 500GB hard drive and Gparted from that installation of Ubuntu? If so, you cannot format a drive/partition that is mounted. You would need to run Ubuntu from a live USB or CD and use Gparted in the live session. Also - if you have a swap partition on the 500GB drive, this will be automatically mounted by the live session and in Gparted you would need to right-click on it and "swapoff" before you could delete it.

**EDIT**: now you've added an edit saying that you installed ntfs drivers. You need to explain what you mean. The ntfs-3g driver comes as default in Ubuntu.

---

### Post by mychack on 2012-07-24
> **coffeecat said:**
> You need to explain this better. Creating one partition and formatting it NTFS in your 500GB HD is perfectly possible in Gparted.

Let me make a guess. Are you running Ubuntu from the 500GB hard drive and Gparted from that installation of Ubuntu? If so, you cannot format a drive/partition that is mounted. You would need to run Ubuntu from a live USB or CD and use Gparted in the live session. Also - if you have a swap partition on the 500GB drive, this will be automatically mounted by the live session and in Gparted you would need to right-click on it and "swapoff" before you could delete it.

**EDIT**: now you've added an edit saying that you installed ntfs drivers. You need to explain what you mean. The ntfs-3g driver comes as default in Ubuntu.

Yes, gparted/Ubuntu on the same install.

I was operating under the assumption that you had to install some NTFS drivers for them to be an option (like on Mac). I was just saying that I installed them so that I could format my USB as NTFS to install Windows.

Here's a screenshot, if it helps: [IMG]http://s12.postimage.org/i1lklv8gt/Screenshot_from_2012_07_24_17_15_28.png[/IMG]

---

### Post by coffeecat on 2012-07-24
I thought so. You can't do it that way. Just boot from a live CD/USB and everything you need will be there in the live session. Just remember to right-click on sda5 and "swapoff" and the padlock will disappear from it and the sda2 extended. sda1 won't be locked in the live session.

You'll then be able to delete all those partitions and then create NTFS partitions. If someone tells you that you shouldn't use Gparted for creating NTFS paritions for installing Windows to, all I can say is that I've installed Windows XP, Vista and 7 to NTFS partitions created by Gparted and they've run just fine.

---

### Post by mychack on 2012-07-24
> **coffeecat said:**
> I thought so. You can't do it that way. Just boot from a live CD/USB and everything you need will be there in the live session. Just remember to right-click on sda5 and "swapoff" and the padlock will disappear from it and the sda2 extended. sda1 won't be locked in the live session.

I don't know anything about live USB's... I imagine its Ubuntu run from a USB? I only have one USB and it is 8 gigs--it has my Windows7 (maybe that's a live usb?!) on it (setup with UNetbootin)-- is it possible to have both on the one USB?

---

### Post by coffeecat on 2012-07-24
> **mychack said:**
> I don't know anything about live USB's...

You used one to install Ubuntu in the first place:

> **mychack said:**
> I installed Ubuntu using a USB,

If you have only one USB stick then you're a bit stuck, but you cannot delete or reformat your Ubuntu partitions from within the Ubuntu system that's running from those partitions. That's a bit like asking Windows to delete its own C: partition. It won't do it.

Do you have still have the Ubuntu desktop ISO you downloaded to create the live USB? If so, you can burn this to CD and boot up from the CD - **if** you have or can borrow an external USB optical drive. It's somewhat slower but works quite OK. See:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Before you delete your current Ubuntu, you can use Brasero to burn the CD if you want.

---

### Post by mychack on 2012-07-24
> **coffeecat said:**
> You used one to install Ubuntu in the first place:



If you have only one USB stick then you're a bit stuck, but you cannot delete or reformat your Ubuntu partitions from within the Ubuntu system that's running from those partitions. That's a bit like asking Windows to delete its own C: partition. It won't do it.

Do you have still have the Ubuntu desktop ISO you downloaded to create the live USB? If so, you can burn this to CD and boot up from the CD - **if** you have or can borrow an external USB optical drive. It's somewhat slower but works quite OK. See:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Before you delete your current Ubuntu, you can use Brasero to burn the CD if you want.

Actually, while you responded, I found this: [http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/) which appears to be the answer to my problem.

The Ubuntu 12.04 Desktop .iso appears to be about 700MB, and the Windows .iso is 3.5GB, so it should fit on the one USB.

This should work, in theory, right?

---

### Post by coffeecat on 2012-07-24
Will that allow you to boot your saved Windows? I don't see any mention of that.

By the way - when you say you have your copy of Windows on the USB, is that the OEM restore image for your netbook?

---

### Post by oldfred on 2012-07-24
It is a bit tricky.

I had a 2GB flash and only was able to install Windows repairCD to it from a CD, but it only took about 300MB, so I had room for more.

I installed grub to the MBR and made sure that I did not have two /boot folders. Windows likes a /Boot and grub a /boot and if you have both Windows will not work. I then manually edited grub to add a chainload entry to the Windows partition and it worked. I was actually surprised it worked. 

Then I have used grub to loopmount the ISO and shrunk the Windows partition and created another just for the ISOs.

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

---

### Post by mychack on 2012-07-24
> **coffeecat said:**
> Will that allow you to boot your saved Windows? I don't see any mention of that.

By the way - when you say you have your copy of Windows on the USB, is that the OEM restore image for your netbook?

To be completely honest, it is a copy of Windows7 Ultimate that I obtained illegally. I know: I'm a terrible person! But, if I buy a netbook and have no installation CD (or options, really), I don't feel *that bad* about obtaining a copy through other means.

---

### Post by mychack on 2012-07-24
> **oldfred said:**
> 

MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

This appears to be the same process that I link to above?

---

### Post by coffeecat on 2012-07-24
> **mychack said:**
> To be completely honest, it is a copy of Windows7 Ultimate that I obtained illegally. 

In which case we can't go any further.

See the forum [Code of Conduct](http://ubuntuforums.org/index.php?page=policy) to which you agreed when you created your forum account. In particular:

> Material that suggests illegal activity or contains illegal content is also forbidden. We do not support circumventing TOS, EULA, etc here.

I've closed the thread.

---

