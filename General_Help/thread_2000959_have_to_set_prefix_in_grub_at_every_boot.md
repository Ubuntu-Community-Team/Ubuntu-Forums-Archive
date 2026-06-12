---
title: "have to set prefix in grub at every boot"
date: 2012-06-10
forum: General Help
---

### Post by Xenosis on 2012-06-10
Hello ubuntu community, I'm a first time poster but a long time reader.
[QUOTE="backstory"]
Originally I installed Ubuntu onto a separate harddrive (sdc) with windows 7 on sdd and had to muck about with reinstalling windows MBR and bootmanager and then reinstalling grub back over it again. - Got that all working.

Then I had the bright idea to create a separate boot partition for ubuntu to make it safer for me to use grub as a pre-bootloader to the windows 7 loader in a physical disk virtual machine. - Got that all working.[/QUOTE]

Whats wrong is that in the process of creating and setting up the new "GRUB Loader" partition, I must have missed something because now every time I boot I am first prompted with grub rescue> and have to set the prefix from (hd0,1)/boot/grub to (hd0,4)/grub. (hd0,1) is the primary ubuntu ext4 partition while (hd0,4) is the 600mb boot partition that was set to mount at /boot viewable both in gparted and in /etc/fstab.

When I set the prefix correctly and use the commands "insmod normal" and "normal", it boots right up into the modified grub2 loader and I can get into either OS. I have to use these 3 commands every time I boot my PC up which isn't too bad but I'd really like it to just go to grub.

The problem, as I see it, is that the boot partition simply isn't being mounted so that the grub folder is accessible when the loader looks in /boot on (hd0,1). "ls (hd0,1)/boot" shows an empty folder.

Any help would be appreciated. I already re-installed grub-pc grub-common and all that. Once my machine is booted into ubuntu /boot is properly filled with what is in the boot partition meaning it got mounted but its not getting mounted early enough.

Would something as simple as a symbolic link to / in the boot partition be enough? Or would that then cause problems when it is mounted properly?

---

### Post by oldfred on 2012-06-10
I think the grub you have in the MBR is not for your new grub only boot partition. You just may need to reinstall grub2's boot loader to the MBR.

Since it is a grub only partition I do not know a way to directly install. Change sda5 in example to your grub only partition.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

If it is a grub only partition any update-grub commands will not work on that partition. You can update the version in each install but that will not change your boot menu.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Each install also remembers where it originally installed. On major updates it may automatically reinstall to that location.
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates: Uncheck everything if you do not want it to reinstall to the MBR.
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by Xenosis on 2012-06-12
> **oldfred said:**
> I think the grub you have in the MBR is not for your new grub only boot partition. You just may need to reinstall grub2's boot loader to the MBR.

Since it is a grub only partition I do not know a way to directly install. Change sda5 in example to your grub only partition.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda

If it is a grub only partition any update-grub commands will not work on that partition. You can update the version in each install but that will not change your boot menu.
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

Each install also remembers where it originally installed. On major updates it may automatically reinstall to that location.
#To see what drive grub2 uses see this  - grub-pc/install_devices:
sudo debconf-show grub-pc

#to get grub2 to remember where to reinstall on updates: Uncheck everything if you do not want it to reinstall to the MBR.
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

I installed it to the mbr from within ubuntu using grub-customizer with no success. can I use the commands you give from within ubuntu to re-install it? will this pull the actual device that the grub folder is on since its mounted in /boot? ie /dev/sdc4 or (hd0,4) and set that to the prefix?

Is there no way to just edit it in text form and change where it looks from (hd0,1)/boot/grub to (hd0,4)/grub ?

---

### Post by idoitprone on 2012-06-13
> **Xenosis said:**
> I installed it to the mbr from within ubuntu using grub-customizer with no success. can I use the commands you give from within ubuntu to re-install it? will this pull the actual device that the grub folder is on since its mounted in /boot? ie /dev/sdc4 or (hd0,4) and set that to the prefix?

Is there no way to just edit it in text form and change where it looks from (hd0,1)/boot/grub to (hd0,4)/grub ?

you can run this bootscript to tell us about your setup
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

You cannot just edit the mbr, there are programs and application for that job because if you mess up, you have to create a new mbr. Those commands the [SIZE=4]**wise**[/SIZE] oldfred is telling you to use is meant to change the partition that the mbr is looking for. Make sure that boot partition have all the bootfiles or else your computer wont boot

(hd0,1) is actully linux's way of identifying drives and partition

---

### Post by Xenosis on 2012-06-27
I had no luck with that method, but I tried selecting the partition in grub-customizer and then installing the MBR again and it worked.

Can dual boot windows and ubuntu from a separate /boot partition.

---

