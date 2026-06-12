---
title: "Ubuntu 10.10 installation doesn't detect hard drive"
date: 2010-10-28
forum: General Help
---

### Post by aeromorph on 2010-10-28
When I try to install Ubuntu 10.10 on my desktop, the partitions menu that appears during the installation doesn't detect my sata hard drive. I have Windows 7 on a partition, left a space unpartitioned, then tried to install it. Couçdn't detect the disk, so I booted to live ubuntu, and created a ext3 partiton with Gparted, it still doesn't detect. Also tried completly formating the disc. Still Doesn't detect. The strange thing is that in the ubuntu desktop when i boot with Live usb, the disk is there. I was also able to create the partition as i described before.

---

### Post by Mark Phelps on 2010-10-28
Couple of ideas ...

First, 10.10 uses Ext4, not Ext3.  That could be why it won't let you select the partition even if it DOES see it.  Reformat it as Ext4 and see if that makes any difference.

Second, I've first-hand experience with situations in which the alternate CD installer handles partitioning a lot better than the desktop CD.  Don't ask me why -- as they are both supposed to be using the same installer -- but I've seen that myself.

So, if the first change doesn't work, download the Alternate CD and see if that installer is able to see either the Ext4 partition, or after you remove it, the free space.

---

### Post by darkhelmetchris on 2010-10-28
> **Mark Phelps said:**
> First, 10.10 uses Ext4, not Ext3.  That could be why it won't let you select the partition even if it DOES see it.  Reformat it as Ext4 and see if that makes any difference.

I'll add my 2 cents..  I have my 10.10 installed using partition1(/) as ext3 and partition2(/home) also as ext3.  I did this simply out of personal choice.  That said, 10.10 seems to have no issues running under ext3 as far as I'm aware.

Still, some other things come to mind...

> **aeromorph said:**
> When I try to install Ubuntu 10.10 on my  desktop, the partitions menu that appears during the installation  doesn't detect my sata hard drive. I have Windows 7 on a partition, left  a space unpartitioned, then tried to install it. Couçdn't detect the  disk, so I booted to live ubuntu, and created a ext3 partiton with  Gparted, it still doesn't detect. Also tried completly formating the  disc. Still Doesn't detect. The strange thing is that in the ubuntu  desktop when i boot with Live usb, the disk is there. I was also able to  create the partition as i described before.

First one that pops in my head is that I have had some problems installing Ubuntu (and other distros) if the storage devices are in what I call "unexpected" order.  For example, on one of my systems, for some reason, if I use primary IDE master for the hard disk, and Secondary IDE slave for the DVD, things go wonky.  But, as soon as I put the DVD on Secondary IDE master, the problem goes away.

You say that you have the LiveUSB loaded and you see your hard disk.  Could you simply click on install in the LiveUSB session and go forward or does it also not see your hard disk at this point?  Also, keeping my first thought in mind, and since you are on LiveUSB and not LiveCD, I would suggest disconnecting all SATA/IDE storage devices except your hard disk, keep the hard disk on SATA port 1 (or zero depending on your mainboard numbering scheme) or Primary IDE master - making your hard disk the first and only drive on those channels, and test the result.

I have also had some trouble with certain CD/DVD drives - no matter where they are.  An older Sony CD-ROM caused me no end to trouble that is similar to this, so perhaps just disconnect your CD/DVD drive for the heck of it.

---

### Post by aeromorph on 2010-10-29
First of all, thanks for the replies... I'm going crazy with this problem, as I'm enjoying so much to use Ubuntu on my laptop. =)
I already tried running the installation from the Live , and it still didn't see the drive. If i have the external drives connected, they all appear in the partitions menu. Also tried formatin entire HD, just leaving all space unallocated, spliting in two partitions, ont with windows and other with ext3 (as I said before) but also tried ext4... I'll try to connect the disc to other SATA port then I'll let you know if it was any good...


No.. Connecting the disk to other sata ports didn't help...

---

### Post by darkhelmetchris on 2010-10-29
> **aeromorph said:**
> Couçdn't detect the disk, so I booted to live ubuntu, and created a ext3 partiton with Gparted, it still doesn't detect ... with Live usb, the disk is there. I was also able to create the partition as i described before.

So I am just a little bit confused here, and need some clarification.  You say you booted in to live Ubuntu and created an ext3 partition with GParted - at which time your hard disk must have been detected or you wouldn't be able to create the partition.  Perhaps you could explain a little more what you mean by "doesn't detect"?  Do you mean that you can't see your hard disk at all (like /dev/sda) during install, or that when you try to load after installation, it doesn't detect your install?

---

### Post by aeromorph on 2010-10-29
Theat's the weird part... I can boot with live usb, and Ubuntu and G-parted both see the disk, but the partitions menu that appears only during the instalation doesn't!(the one where we choose the disk ad manage the partitions where we want to intall) The partitions list is empty and the deviced list is also empty. But, Ubuntu and G-parted still can see the disk.

---

### Post by darkhelmetchris on 2010-10-29
> **aeromorph said:**
> I can boot with live usb, and Ubuntu and G-parted both see the disk, but  the partitions menu that appears only during the instalation doesn't.

Okay, probably the next thing to try would be to download the "Alternate" install image and try with that.  I have had to do this a few times with some hardware.  Give that a go and post your results.  In the meantime, I will see what else I can come up with.

Hm, it occurs to me that you might also set your BIOS for "legacy" or "compatible" mode for the hard disk controller and see if the same problem still exists.  We could be seeing a hardware combination that is slightly incompatible.  Since it's just the installer having the issue, changing the BIOS setting might let you install, and you can change it back later to regain your performance.

---

### Post by paklah on 2010-11-15
I also have similar problem. But the different is Gpart not detect my partition. I really glad because i found this forum :).. (sorry for my broken English)

---

### Post by aeromorph on 2010-11-16
Sorry for the late reply, I didn't abandon the post, just was in a short time period.. =) 
I tried everything described by this far... Still doesn't work. I'll probably quit trying... Thanks for all the help!

---

### Post by aklinc on 2010-11-20
hi i have been haveing the sme problem i can mount the drives i can view the files and folders on the drives i also have windows vista installed on the drive but when i run the install i will get as far as slecting a partition page but it dosent seem to load the partition table

---

### Post by dnel on 2010-11-25
I am also having this problem using a Seagate 150GB sata disk. I've tried using the on-board controller and a PCI sata 150 controller, neither configuration detects the disk. I first found the issue trying to install Linux Mint 10 so whatever it is, the bug is present downstream too.

---

### Post by Rick Myers on 2010-12-08
I was having the exact same problem on a 1 year old Dell T3500. No hard drive detected during installation of 10.10 at all.

What worked for me:
During LiveCD boot, press the space bar, select your language, then hit the F6 key and select;
acpi=off
noapic

Then proceeded with installation.

The above was posted prematurely, my apologies. Strike the noapic requirement. In the end I had to install from the Alternate CD and acpi=off.

---

### Post by nutsy.ben on 2010-12-21
Same thing with the same PC ...

---

### Post by nutsy.ben on 2010-12-21
Same thing with the same PC ... 
ATI FIREPRO in addition that did not really help.

I just use an %% alternate %% CD of ubuntu 10.10 AMD64. The live CD did not work. I also wrote my image on a USB using UNETBOOTIN, in the package list. The disk creator making a CMR32 issue.

Then in the alternate menu. You hit tab. You add acpi=off. You follow the instructions. AND FINALLY APPEAR THE HARD DRIVES !!!! Hourra.


Perform installation.
Note that you may have in this case to install manually the desktop.
Login and then type: suo apt-get install ubuntu-desktop



Then it installs .... It took me 2 months. TO install old versions, trying to upgrade and so on. So believe me when I say that this is by far the simplest solution.

---

### Post by ajtolland on 2011-01-20
Hi,

I had the same problem the OP had -- gparted & fdisk could see /dev/sda, but for some reason, the 10.10 installer couldn't --  and was able to solve it by using the alternative installer, and choosing "NO" when it asked if I wanted to start SATA.

---

### Post by ajtolland on 2011-01-20
Hi,

I had the same problem the OP had -- gparted & fdisk could see /dev/sda, but for some reason, the 10.10 installer couldn't --  and was able to solve it by using the alternative installer, and choosing "NO" when it asked if I wanted to start SATA.

---

### Post by ajtolland on 2011-01-20
Hi,

I had the same problem the OP had -- gparted & fdisk could see /dev/sda, but for some reason, the 10.10 installer couldn't --  and was able to solve it by using the alternative installer, and choosing "NO" when it asked if I wanted to start SATA.

---

### Post by ajtolland on 2011-01-20
Hi,

I had the same problem the OP had -- gparted & fdisk could see /dev/sda, but for some reason, the 10.10 installer couldn't --  and was able to solve it by using the alternative installer, and choosing "NO" when it asked if I wanted to start SATA.

---

### Post by fake_cws01 on 2011-01-24
I also have same problem. I have a brand new System Unit with assembler parts.

1.) MSI H55M-E32 motherboard
2.) Intel i3 processor
3.) DDR3 RAM
4.) Seagate 500GB

I tried installing 8.04LTS version but it can't detect my hard disk, next i've tried 9.10 but it hangs up at the desktop when i click the task bar and the latest 10.10 but it doesn't load and can't detect my hard disk.

WHAT IS THE PROBLEM? CAN ANYONE EXPLAIN PROPERLY???....

---

### Post by fake_cws01 on 2011-01-24
Guys, i don't how but the 10.10 may just work with my new computer. i installed first the windows 7 then restart to install the WUBI because it won't boot directly. Maybe this 10.10 just works with the latest motherboard? i don't know if im correct but someone suggested to me to use 10.10 on my motherboard because its the latest and guess what, it worked. im currently installing it on my other computer.

---

### Post by erotavlas on 2011-01-25
Hi all,

I have the same problem, Ubuntu 10.10 32 bit recognizes my HDD with gparted and can mount the devices but inside the installation procedure the drive is invisible.

My configuration:
CPU: AMD Sempron 3000+
MB: Asus M2N-MX
HDD: Maxtor 6L08020
VC: ATI X300SE

Now I will try with the alternate CD...

---

### Post by mrkite38 on 2011-03-24
Same issue here. Using the alternate installer and choosing NOT to load SATA RAID drivers allowed that hard disk to be seen. I did not need to change my acpi settings.

---

### Post by stoopid_noob on 2011-04-22
I have been suffering with the same thing trying to install this on an SSD that previously had Windows 7 installed on it. I was able to install after going through liveCD the unmounting the mentioned drive, formatting it to ext4 and then continuing with the installation. I am not sure if that will work for everyone but it worked in my case so I thought I would respond.

---

### Post by aeromorph on 2013-02-18
Hello all. All this time has passed and still... Installation doesn't detect hard drive. Anyone get any news on this?

---

### Post by oldos2er on 2013-02-18
Closed.

10.10 is no longer supported. If this happens to you using a supported version of Ubuntu (12.04 or 12.10, for example), please start a new thread.

---

