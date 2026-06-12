---
title: "Need Default Grub menu.lst text for 9.10 RC"
date: 2009-10-24
forum: General Help
---

### Post by steelcommuter on 2009-10-24
As subject states, I would like someone to kindly post their default grub text for a clean install of Ubuntu 9.10 RC.  The installer did not overwrite the bootloader, and I cannot boot into the system.  I know I have to change a few things, but the default text would help me out.

---

### Post by mike555 on 2009-10-24
If you mean that you installed grub to the same partition as the install , you could use a different boot manager , like GAG ......  [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by ranch hand on 2009-10-25
Read the link in my sig and the links to good information.

Grub2 is new and different and does not use a /boot/grub/menu.lst for a start.

---

### Post by blwizard on 2009-10-25
You are not supposed to write your own menu.list in grub2. You need some sort of tool to generate it. It works quite differently than legacy grub. As the guy above suggested, do some research and get it to work. YOU DON"T GENERATE THE CFG FILE BY HAND.

---

### Post by steelcommuter on 2009-10-25
> **ranch hand said:**
> Read the link in my sig and the links to good information.

Grub2 is new and different and does not use a /boot/grub/menu.lst for a start.

I appreciate the point, but I should have been more clear about this: despite an install of Ubuntu 9.10, it still has not written Grub2 over the previous Grub bootloader.  When my system boots, it continues to use the Mint Linux Grub configuration.  The installer has not updated it.  I don't know why.

I have two hard disks, and one has Mint Linux (hd1) and the other should have Ubuntu 9.10 (hd0).  But after intalling Ubuntu 9.10, the system reboots and shows the Grub1 bootloader with options for Mint and for Slackware (which used to be on hd0).

I tried reinstalling Ubuntu 9.10 again on hd0, and it still left the old Grub untouched.  I have no idea why, but I am willing to use Grub1 if I can get it to start Ubuntu 9.10. 

It's a weird issue, and I suspect it is a bug.

---

### Post by ranch hand on 2009-10-25
If you read the link you would see that before freaking  you should run sudo grub-install /dev/<your chosen mbr drive> (in my case sda) from within 9.10

It should be bootable by adding;
```

title        Ubuntu karmic (development branch), kernel 2.6.31-3-generic
uuid        037e8099-d605-4315-b637-f60c6ff692ed
kernel        /boot/vmlinuz-2.6.31-3-generic root=UUID=037e8099-d605-4315-b637-f60c6ff692ed ro quiet splash 
initrd        /boot/initrd.img-2.6.31-3-generic
quiet

```
to the mint menu.lst edited to fit your box.

For the uuid of your partition run;
```

blkid

```
That entry is on a 9.04 install on my test drive and old be sure to change the kernel to 31-14.

---

### Post by steelcommuter on 2009-10-25
All I needed was the blkid command information to find out the partition ID number.  Once I had that and placed it in the Grub1 file, it worked.  Ranchhand, thanks for the command tip.  There was no "freaking," though; your link was for Grub2, and for all I knew Grub2 may have used different syntax.  Anyway, problem solved.

Does anyone have ANY idea why the Ubuntu 9.10 did not install over the old Grub bootloader?

---

### Post by QIII on 2009-10-25
Did you do a fresh install or or did you upgrade?

Upgrading from Jaunty does not cause GRUB2 to be used.  It will maintain GRUB in "legacy mode".

---

### Post by steelcommuter on 2009-10-26
> **QIII said:**
> Did you do a fresh install or or did you upgrade?

Upgrading from Jaunty does not cause GRUB2 to be used.  It will maintain GRUB in "legacy mode".

I installed it from the CD, formatting a partition that previously contained Slackware 12.2.

---

### Post by QIII on 2009-10-26
Did you create a separate /boot partition when you were running Slackware?

---

### Post by oldfred on 2009-10-26
You do not need to post results.txt but if you are interested in how your system is configured run the bootinfo script. For me I have grub2 in a partition and the script does not seem to correctly identify it but I like knowing what is where.

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory.

---

### Post by louieb on 2009-10-26
> **steelcommuter said:**
> Does anyone have ANY idea why the Ubuntu 9.10 did not install over the old Grub bootloader?

Just a guess, you said you have 2 hard drives. That means you have 2 MBRs. 
Have you tried switching the boot drive? 
Run the script like **oldfred** suggested.  Think you'll find the answer in there somewhere.

---

