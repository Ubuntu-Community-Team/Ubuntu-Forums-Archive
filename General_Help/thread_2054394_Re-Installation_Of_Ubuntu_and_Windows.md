---
title: "Re-Installation Of Ubuntu and Windows"
date: 2012-09-07
forum: General Help
---

### Post by tkamdar on 2012-09-07
My system was running fine on 10.10 and upgraded to 12.04 it was extremely slow (may be because of less hard disk or RAM)so I decided to go back to 9.04 as i had a bootable cd for that and when they ask for partition I agreed to use my whole hard disk as a file system without any partition and now that 9.04 is not running properly and every time the Grub is coming up I am not even able to have a flash player even :( 

**So could you please advice how can I make partition as I am not able to use Gparted from 9.04 and then how to re-install Windows 7 and format all other drives along with installed Ubuntu 9.04 and delete all Grubs and stuff and then after installing Windows 7 properly I would Like again re-install 10.10.**

Or if you guys have any other way for that please advice me on that but remember I want remove all the other grub stuff and start it from fresh. I also dont mind to have just ubuntu on my system.

Please any one can provide step by step procedure for that.

---

### Post by MARP1961 on 2012-09-07
Both Ubuntu 10.10 and 9.04 are old unsupported versions of Ubuntu. You will encounter problems installing and running them now. 

Ubuntu 10.04 will still work but I recommend 12.04. If you have low RAM then try to add more or try out Lubuntu 12.04

---

### Post by MARP1961 on 2012-09-07
If you are happy just to have Ubuntu on your computer then don't worry about partitions. If you boot from your newly burnt disk the installer will partition the drive and install the Grub bootloader itself. If Ubuntu 12.04 is slow then your computer is probably low spec and you should try Lubuntu instead:

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by MARP1961 on 2012-09-07
If you want to reinstall Windows, then you will need a Windows disk. Give Windows about 50GB and leave the rest of the drive unallocated ready for Ubuntu later on.

If Windows is still on your drive then reinstall Ubuntu but make sure it doesn't install on the ntfs partition. Reinstalling Ubuntu will give you back a working bootloader.

---

### Post by tkamdar on 2012-09-07
thanks, 

So you are saying me that if I put a bootable CD fro Ubuntu or Lubuntu 12.04 it will solve the problem and it would be working fine again 

One question how about if i use fdisk and make a partition and then install the Windows 7 and completely wipe 9.04 along with the Grub and other unuseful stuff 

would this be possible? Please advice.

Thanks,
Taraq

---

### Post by MARP1961 on 2012-09-07
If you have a Windows 7 disk (either a new one you've bought or a recovery disk for the version on your computer) then** put Windows back on first.**

The Windows disk should be able to delete and reformat your hard drive easily. If you want you can then set up two partitions:

One **Primary ntfs partition  for Windows 7 **(50GB should be OK) and leave the rest as **unallocated space**. Once you have installed Windows 7,  reboot several times to make sure it is OK and apply all the updates (good luck)!!

When you are ready, get your Ubuntu, Xubuntu or Lubuntu 12.04 disk and **boot from the disk**. Then select 'Try Ubuntu' to make sure everything works. If it does then select 'Install Ubuntu' and let the Installer guide you through. it will give you the option of keeping Windows. The installer will find the free space you left and will set up the Ubuntu partitions. It will also install a fresh Grub bootloader that will give you a choice of Windows or Ubuntu at bootup.

---

### Post by tkamdar on 2012-09-07
i tried to boot my Windows vista but as i think i have no partition and the whole hard disk has been taken by ubuntu 9.04 what you suggest me to do first. 

so i can delete all and install windows again after installing or during installation wiping out that ubuntu 9.04 completely and just having that windows version as you said for a while and checking and then installing ubuntu 12.04

I am sorry to bother you again here but I need steps as I think dont want to ruin my system again.

Thanks 

Taraq

---

### Post by MARP1961 on 2012-09-07
If you have no files of any value on your hard drive and you want to get rid of a broken Ubuntu 9.04 install, then just reinstall Windows (XP, Vista or 7). If you have the proper Windows disk for that computer (or you have bought your own retail disk) then you simply use it to boot and reinstall Windows. If you do not have the correct disk for Windows on your particular computer, you will not be able to activate or update it.

If you can reinstall then just allow the Windows disk to reformat the hard drive. Once Windows is on then Ubuntu can also be put on (if you've left enough unallocated space).

If you just want Ubuntu then it's really easy. Just use another computer to burn a disk for the latest Ubuntu 12.04 then let your computer boot this disk. Ubuntu installer will ask  you whether you want to delete everything and install just Ubuntu. It's dead easy! It's only a little trickier if you still have stuff on the hard drive you want to keep.

---

### Post by MARP1961 on 2012-09-07
A Windows reinstall is much more difficult than Ubuntu. Make sure you have bought your own Windows Product Number or are reinstalling exactly the same Windows version that was originally on the computer.

---

### Post by tkamdar on 2012-09-10
Thanks for the previous help, but now I have completed the first stage but not able to do the other

I was able to install Windows 7 (originally I had Vista but this Windows 7 is from my friend and genuine, hopefully)and it is running fine but you know it is no fun at all I need ubuntu but I am tried to install ubuntu 12.04 and as well as 10.10 with a CD it is not working, I tried everything but with CD it was not working (I did not tried with USB), I have 3 partitions 
1. Windows partition Primary NTFS
2. Empty Primary Partition NTFS
3. Logical Partition which I made it through Disk Management and Shrink the Volume.

But any how I am not able to boot up the CD and install Ubuntu

Please Assist

P.S: Without Ubuntu it feels so empty  :(

---

### Post by MARP1961 on 2012-09-10
Your computer BIOS settings may need to be changed to alter the boot order. Set the boot order to look for the CD/DVD drive before the Hard Drive. Pressing one of the F keys on startup should bring you to the BIOS screen. Go careful what you change!

Alternatively you may be able to select startup/boot options by pressing F12 or similar as the computer is booting. Your computer may briefly show a message on the screen about startup options as it boots.

Have you tried switching on when the CD is already in the drive?

---

### Post by MARP1961 on 2012-09-10
Please Note: If you used your friend's Windows 7 disk to install onto your computer and your computer has a Product Sticker for Windows Vista you will probably not be able to Activate Windows and apply all the updates. It will give you a fixed time to activate after which it will no longer work.

You either need to buy a fresh retail copy of Windows 7 (with it's new Product Number) or reinstall Vista by using a Vista Upgrade Disk and re-entering the original Product Number on the sticker somewhere on your computer. Microsoft don't give things away free.

---

### Post by Mark Phelps on 2012-09-10
To further expand on what MARP1961 said ...

A vista key will NOT work in Win7.  So, anything you have in terms of a product sticker on your Vista-preinstalled PC is not going to work in Win7.

If no product key is entered when Win7 is installed, it will work for 30 days before it shuts down.  There are ways to extend that, but if you really want to use Win7 in the long run, you need to purchase a new key for it.

If you really want to upgrade your Vista-preinstalled PC to Win7, you should check with the PC supplier.  They will often offer discounts on upgrade versions -- which will be a LOT cheaper than going out and purchasing a retail version.

---

### Post by tkamdar on 2012-09-11
Thanks ....

I solved the Issue

---

### Post by MARP1961 on 2012-09-11
If you have time perhaps you can tell us what you did. This is how people find out how to do things with Ubuntu.

---

