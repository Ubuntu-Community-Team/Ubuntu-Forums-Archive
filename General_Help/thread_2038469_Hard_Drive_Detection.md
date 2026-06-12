---
title: "Hard Drive Detection"
date: 2012-08-06
forum: General Help
---

### Post by Maliibu on 2012-08-06
I have two hard drives in my computer. The first is a 128GB ssd with windows 7 installed. The second is a 1TB, used for file storage etc. I decided to wipe the second hard drive and install ubuntu onto it. Installation went fine, until my computer restarted.

In my bios settings the disk with ubuntu was set as the master boot. So on reset i figured my computer would boot off the same disk, and load ubuntu. Instead, Windows booted off my ssd. I checked under 'My Computer' and my 1TB hdd was no longer listed.

I reset my computer and opened up the BIOS settings, and the hdd was no longer listed there either. So I booted Windows up again to do some research. 

Under 'My Devices', Windows does detect the drive. I went to disk management and it is also shown there, without an assigned letter.

Windows does not allow me to assign the drive a new letter, the only option that is available is to convert the disk into a dynamic drive, which supposedly will wipe the whole drive.

Any help would be greatly appreciated.
Thanks, Maliibu.

---

### Post by oldfred on 2012-08-06
Welcome to the forums.

If BIOS does not show drive then check physical connections, power, SATA port etc. Neither Windows nor Linux will see a drive if BIOS does not see it. But Windows will not normally see Linux formated partitions. And you do not want to let Windows convert to dynamic as that does not work with Linux.

What BIOS mode are you in. It should be AHCI for a new computer. If Window 7 not configured for AHCI, you may need to install drivers before changing the setting in Windows.

Do not run repairs just yet, but if drive found run the BootInfo and post the link it gives you, then we can suggest options:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Maliibu on 2012-08-06
Thanks for the response, and sorry i am so late to respond. 

Everything is fairly new, within the last year or so.

Here is the link from the Boot Repair

[http://paste.ubuntu.com/1133519/](http://paste.ubuntu.com/1133519/)

---

### Post by oldfred on 2012-08-06
How much RAM do you have? If more than 3GB, I would reinstall with the 64bit version as you have the 32bit PAE version.

Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)
[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

Another reason to reinstall is to change from one very large / (root) partition to a small root partition and separate /home.

You have the standard default install which is fine for many. I used it for 2 years. But with new very large hard drives, you end up with a very large root partition.  Some installs are having issues booting with one / partition on large drives and either a separate /boot or a much smaller / with separate /home works.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I like to partition in advance with gparted either form the Ubuntu liveCD or from a gparted liveCD. And if dual booting with Windows having another NTFS partition for shared data is a good idea. I have my Firefox & Thunderbird profiles still in my shared NTFS even though I now do not boot XP.  But that lets me have same bookmarks, settings for Firefox and email in which ever system I boot.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Maliibu on 2012-08-08
I have 8 GB memory currently. As far as the partitioning goes, would that be the reason why i cannot access my HDD?

I re-installed ubuntu as the 64-bit version. Then i ran Boot Repair. When i reset my computer, bios still did not recognize the HDD, but now during start up, i am taken to a GRUB screen, where i can choose to load ubuntu or Windows 7, and some other functions. 

Here is the new Boot Repair info:

[http://paste.ubuntu.com/1136652/](http://paste.ubuntu.com/1136652/)

Neither Windows nor ubuntu recognizes my HDD now, but when i use the ubuntu CD for the download, the HDD is recognized.

So at this point, does it come down to the partitioning like you said?

Note: Boot Repair told me to remember to make BIOS boot on my 1TB HDD

---

### Post by oldfred on 2012-08-08
Boot script looks normal. It does look like you have grub2's boot loader in both sda & sdb, do both work to get grub menu?  I would install the Windows boot loader to sda, so if you have issue with sdb, you can in BIOS choose to boot sda and Windows directly. But set BIOS to boot sdb as then from the grub menu you can choose Ubuntu or Windows.

If still having boot issues, it may be video issues. What video card do you have? I have nVidia and have to use nomodeset on first boot or until I install nVidia drivers.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

