---
title: "installing ubuntu on a fake raid"
date: 2011-09-22
forum: General Help
---

### Post by Someone uk on 2011-09-22
hi, i have a computer with 4 hard drives on a fake raid 5 and i have been trying to install ubuntu

when i run the 11.04 live cd the first time gparted like it should recognises 1 large hard drive and manages to partition it and as long as i don't shutdown i the hard drives work like they should and i have the all the separate partitions visible in /dev/mapper (Terminal1.png)
after an apparently successful install i start running into problems when i try to reboot and boot ubuntu from the hard disks is when i run into problems

firstly ubuntu just will not boot from the hard disks, then when i try to boot the live CD i gparted reports that it "can't find valid filesystem superblock" (GPartedError.png) and when i look in /dev/mapper there is only 1 volume (Terminal2.png) and i am completely unable to mount the hard drives

is there a way to get this working?

ps i am using the fake raid setting found on a gigabyte motherboard aka XHD

---

### Post by raja.genupula on 2011-09-22
Hi 
these are the direct solutions to your issue , have a look at them

[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by Someone uk on 2011-09-22
hmm i will follow the first guide

but wouldn't i be right if i said that if i couldn't mount the filesystem on a live CD then the bios would be unable to boot from it?

---

### Post by raja.genupula on 2011-09-22
Hey man,
        I think file system should mount .

---

### Post by Someone uk on 2011-09-22
i tried the first guide and got an error message at step 8 (installing grub)
> 
Unknown partition table signature
/dev/mapper/../dm-0 does not have any corresponding BIOS drive.


---

### Post by YesWeCan on 2011-09-22
Try this, perhaps: [http://www.techspot.com/vb/topic153346.html](http://www.techspot.com/vb/topic153346.html)

---

### Post by Jagoly on 2011-09-23
Yes, grub can't be installed on a fake raid. If you aren't dual booting,  then use a linux software raid. Remove all raid settings in the bios, then use the ubuntu alternate installer to set up Raid 5. I do believe that the method linked above works too, but with a GUI if you need one.

---

### Post by Someone uk on 2011-09-26
i have tried a software raid but believe it or not the alternative cd gives a worse problem (it basically says it can't mount the CD and stops there)

is there a way to run the ubuntu graphical installer without it installing grub? the graphical installer is horribly buggy, half the time you specify where to install grub it'll just install it in /dev/sda (regardless of selection) and if it fails to install grub the error message will pop up but it's ALWAYS unresponsive

---

### Post by YesWeCan on 2011-09-27
What do you want to do exactly?
It looks like you initially tried to install Ubuntu to a Fake RAID (aka SATA/mobo/Windows/dm RAID). It is a little tricky to do this.

Unless you wish to install Windows too there is no advantage to using Fake RAID and I would discourage it. You'll have a much easier life if you use linux mdraid.

But I don't know why you have chosen Fake RAID.

If you decide to use md raid and you have nothing of value on the existing RAID,
1. Disable all RAID options on your mobo
2. From live CD remove the dm RAID superblocks so the Ubuntu installer doesn't get confused (it is easily confused ;) )
[COLOR="DarkSlateBlue"]sudo dmraid -E -r /dev/sdX[/COLOR]  (repeat for X = each drive letter)
3. Boot the alternate Ubuntu CD.
4. Reformat each drive with a single partition, empty, with type "linux raid autodetect" (the type doesn't matter but it is handy when using fdisk to see what your partitions are being used for)
5. Add an LVM layer so you can make volumes for root, home, swap, etc.

That's one way to skin a cat, anyhow.

If you cannot boot your alternate CD you may need to reburn it. When you first boot it and get the main menu, select "check disc for errors" to make sure it has been written ok.

---

### Post by NHclimber on 2012-12-16
> **raja.genupula said:**
> Hi 
these are the direct solutions to your issue , have a look at them

[http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Neither of these solutions apply to Ubuntu release in the last 3 years.

---

### Post by NHclimber on 2012-12-16
> **YesWeCan said:**
> What do you want to do exactly?
It looks like you initially tried to install Ubuntu to a Fake RAID (aka SATA/mobo/Windows/dm RAID). It is a little tricky to do this.

Unless you wish to install Windows too [...]

Since the OP wants to install fakeraid, does 'tricky' mean 'impossible'?

---

