---
title: "Grub won't go away, can no longer boot windows"
date: 2012-06-22
forum: General Help
---

### Post by jmoney47 on 2012-06-22
Hey guys

I recently installed Ubuntu onto my new laptop, but I had to redo it because I accidently used a 10.10 disc instead of my 12.04 disc.  After installing 12.04, booting up normally gives me an error saying something isn't found and I have a grub rescue prompt.  If I boot into the recovery partition (press f3 on boot), I get the Grub bootloader for 12.04 from which I can choose all the linux options, windows recovery, and windows 7 loader.  However, if I choose the Windows 7 loader, it says it cannot find the drive.  This might be due to the fact that my first two SSD's are running RAID 0.  I tried the recovery option hoping it would fix the mbr for the normal boot, but it did not work.  How can I get rid of the grub bootloader so that I can boot into windows again?????

---

### Post by oldfred on 2012-06-22
With multiple drives are you booting the correct drive? Each MBR or RAID root partition may have different boot loader.

Best to post detailed info using this:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by jmoney47 on 2012-06-22
Here's the link to the boot repair thing: [http://paste.ubuntu.com/1054950/](http://paste.ubuntu.com/1054950/).  I am going to try to restore the MBR of the drive through a Windows 7 disc (assuming I can find one) and see if that works.  There are two logical hard drives in my computer, three physically.  The first two are in raid appearing as one.  Windows 7 is on that one and I cannot get to it because there is a broken GRUB loader there.  The other one has a recovery partition, an NTFS data partition, and an ext4 linux partition.  Booting normally goes to the first GRUB loader, and booting to the recovery partition goes to the second, working GRUB loader and works fine except that I cannot get to the Windows 7 os.  Looking at the boot repair menu, it only gives me the option of putting an MBR on the sdc drive.  However, that would prevent me from ever accessing the recovery partition again and it would not necessarily work, as it did not in the GRUB loader.  Then I would be kind of stuck with an nonoperational system.  Do you have any recommendations?

---

### Post by oldfred on 2012-06-22
The standard Ubuntu desktop  does not include the RAID drivers and I do not think then the os-prober can find or finds the Windows install inside the RAID.

Try installing this and then rerun the update.

sudo apt-get install mdadm

sudo update-grub

Did you run Boot-Repair from your Ubuntu install or a liveCD/USB?

---

### Post by jmoney47 on 2012-06-22
Ran it, gave me a couple errors about not being able to remove directories, but nothing else changed.  I ran it inside my ubuntu install.

---

### Post by oldfred on 2012-06-22
Were you booting Windows thru sdc1 or /dev/mapper/isw_dafijaajfa_Volume0p2 ?

Both seem to have bootmgr & BCD file. The other Windows is a recovery.

---

### Post by jmoney47 on 2012-06-23
Figured out how to do it.  I took a Windows 7 disc, selected the repair my computer option, selected to open a command prompt, and typed "Bootrec.exe/FixMbr."  It worked perfectly and there are no longer any problems.  Thanks for your help though!

---

