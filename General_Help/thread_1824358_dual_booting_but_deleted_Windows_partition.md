---
title: "dual booting but deleted Windows partition?"
date: 2011-08-13
forum: General Help
---

### Post by garyed on 2011-08-13
I got an old Sony Vaio from a friend & wanted to keep a stripped down version of windows along side 10.04. During installation when I saw two Windows partitions. I saved the first one which was about 5 gig & deleted the other bigger partition & used ext4 on the free space for Ubuntu. I assume I only kept the recovery partition so basically I have sda1 (recovery partition)ntfs & the rest ext4. If I pick Windows from the grub menu at start-up the recovery starts but then shuts down with an error. I'm assuming its looking for the other ntfs partition to install & can't find it but I'm not sure what to do. I haven't done anything with Ubuntu yet so deleting & reinstalling is not a problem but if I do getting back to the restore menu probably will be. I don't have any disks that came with the computer either. Any ideas

---

### Post by garyed on 2011-08-21
I haven't gotten any replies so I guess its hopeless but I did use Gparted live to make another ntfs partition right after the recovery partition & then installed Ubuntu onto an ext4 parttition.
Now I have sda1(recovery partition)  & sda2 (empty ntfs partition) then
extended & ext4 partions. When I choose Widows from Grub the recovery starts
but I still get an error when Windows tries to start the recovery.
Any ideas?

---

### Post by ClientAlive on 2011-08-21
What version of Windows is it?
------------------------------

By the way, if the sticker with the license key is still on the bottom of the computer you can use it to reinstall windoze and activate it. All you'd have to do is find someone with the disc so you can install it again.

I don't recommend it (for several reasons, one of them being it's illegal) but you might be able to find a torrent of the Windows o/s. I don't know if you can do an Md5sum check for Windows operating systems but it's something to think about.

---

### Post by Megaptera on 2011-08-22
I think it would help if you posted the results of Boot Info Script.
Instructions in #1 here: [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by L a r r y on 2011-08-22
If you have the license key for Windows, you might be able to obtain a copy from the computer manufacturer, They might want like $50 but if you have no other legal option, that might be the way to go.

Many new computers with Windows installed have you do a one-time burn of a backup set of discs, rather than they provide them.

You can always get a free download of your OS from the Internet when the OS is Linux!

---

### Post by asomad on 2011-08-22
> **ClientAlive said:**
> What version of Windows is it?
------------------------------

By the way, if the sticker with the license key is still on the bottom of the computer you can use it to reinstall windoze and activate it. All you'd have to do is find someone with the disc so you can install it again.

I don't recommend it (for several reasons, one of them being it's illegal) but you might be able to find a torrent of the Windows o/s. I don't know if you can do an Md5sum check for Windows operating systems but it's something to think about.

was gonna say the same thing. except, what's illegal? If he has a license ON his machine for windows, ANY windows install disk (of the same version as the license) can be used to install windows, and it will accept his license key. And it is 100% legal! (you may need to phone-call microsoft for a special activation code when you are done with your install, but this literally takes seconds, and is a totally automated system.)

The windows install media can even be downloaded as an ISO, legally! (from microsoft themselves) You just need a license to actually install and use it! (which you have, if the sticker is present)

edited to say: I would AVOID any .torrent iso's of any OS with the exception of ones listed BY THE MAKER ON THEIR SITE, for the reason that many copies out there will have ugly things like root kits, and so so much more, embedded in the code....

---

### Post by YesWeCan on 2011-08-22
> **garyed said:**
> I got an old Sony Vaio from a friend & wanted to keep a stripped down version of windows along side 10.04. During installation when I saw two Windows partitions. I saved the first one which was about 5 gig & deleted the other bigger partition & used ext4 on the free space for Ubuntu. I assume I only kept the recovery partition so basically I have sda1 (recovery partition)ntfs & the rest ext4. If I pick Windows from the grub menu at start-up the recovery starts but then shuts down with an error. I'm assuming its looking for the other ntfs partition to install & can't find it but I'm not sure what to do. I haven't done anything with Ubuntu yet so deleting & reinstalling is not a problem but if I do getting back to the restore menu probably will be. I don't have any disks that came with the computer either. Any ideas

Hi. What error does it give?

You might try deleting the Ubuntu partition to leave the rest of the disk unallocated.

It probably doesnt help that your standard MBR has been blown away by Grub. Also, some vendors use the area just after the MBR for files. What you should have done was to backup the first 63 sectors of the disk. But there is no way you would have known to do this and the Ubuntu installer doesnt do this automatically which I think is a gross omission.

It may make no difference but you can restore the MBR boot code using lilo:
[COLOR="Navy"]sudo apt-get install lilo
sudo lilo -M /dev/sda mbr[/COLOR]
assuming your disk is named sda

---

### Post by asomad on 2011-08-22
Most vendors use a small partition for backup. (Windows oem license requires manufacturers to include a backup copy of windows, They do this with a partition, cause its cheaper than making CD's (I despise this practice, I feel it's space theft)). So when I have a store bought computer, one of the first things I do (after adding hardware lol), is reformat the drive and start CLEAN.
  In your case, between grub eating the MBR, and the primary windows partition (assumably) being removed, I think your best bet is to start over. When making a dual booter with Single HDD, its a good rule to always install windows first. 
Best of luck!

---

### Post by Megaptera on 2011-08-22
> **asomad said:**
> Most vendors use a small partition for backup. (Windows oem license requires manufacturers to include a backup copy of windows, They do this with a partition, cause its cheaper than making CD's!.....

Most unusually, my Dell came with a restore partition _and_ recovery discs! So, I tested the discs (did a restore) and then deleted the 12GB recovery partition on which I installed Ubuntu. 

However, I agree recovery discs are best!!

Anyway ... any news from garyed??? :)

---

### Post by garyed on 2011-10-10
I apologize to all those who tried to help me for not getting back sooner.
I kind of gave up trying to put Windows on & have just been running Ubuntu.
I rarely have a need for Windows so its not that big a deal but it would be nice to have it for those occasions when I need it. I do have an OEM CD of XP that I use on my desktop that I could install but then I'd probably be violating some terms with MS & have to deal with registering too. It just seems to me that if my Rescue partition is in tact then there should be a way to reinstall everything like it was when it was new.

---

### Post by Mark Phelps on 2011-10-11
The OEM version of Windows that came with your desktop is only legal to use on that PC -- OEM licenses are actually matched to individual PCs.  If you want to reinstall that copy on that PC, you can do that.  What you can't do is use that copy on a different PC.

As to restore, every OEM does it differently, and even for different PCs from the same OEM.  Generally, you either press a special key combination, or you insert a Recovery CD, to start the Restore operation.  The sequence depends on your particular PC -- and is documented with the PC.

If you change or move the partitions on the drive, that will often prevent an OEM restore from working. In that case, you generally have to remove all the partitions except the Recovery partition (the one containing the Windows image file) and try the Restore again.

---

### Post by garyed on 2011-10-11
> **Mark Phelps said:**
> .......
If you change or move the partitions on the drive, that will often prevent an OEM restore from working. In that case, you generally have to remove all the partitions except the Recovery partition (the one containing the Windows image file) and try the Restore again.

That sounds like what the problem is. I can start the Windows recovery from Grub & it looks like its going to work & then all of a sudden a fatal error & blue screen pops up & the computer just locks up & has to be powered off.
The reason I was given this computer was because it wouldn't boot up into Windows so the guy bought a new laptop & I got data he needed off the HD first before I tried to do anything. I thought the HD was going bad because Ubuntu wouldn't install from a live CD. It gave me an error & couldn't partition the drive. I had to use Gparted live to do it.
By the way its a Toshiba Satellite Pro with Win XP. I made the mistake of not doing my research first & didn't realize it had a recovery partition until it was too late.     
Now that I have my LAMP server & everything else setup I'm not sure whether I want to go through deleting everything to see if it will work. If I do I'll post back the results.
Thanks

---

### Post by ClientAlive on 2011-10-12
> **asomad said:**
> was gonna say the same thing. except, what's illegal? If he has a license ON his machine for windows, ANY windows install disk (of the same version as the license) can be used to install windows, and it will accept his license key. And it is 100% legal! (you may need to phone-call microsoft for a special activation code when you are done with your install, but this literally takes seconds, and is a totally automated system.)

The windows install media can even be downloaded as an ISO, legally! (from microsoft themselves) You just need a license to actually install and use it! (which you have, if the sticker is present)

edited to say: I would AVOID any .torrent iso's of any OS with the exception of ones listed BY THE MAKER ON THEIR SITE, for the reason that many copies out there will have ugly things like root kits, and so so much more, embedded in the code....


Downloading torrents is.  ;)

I think there's a little wiggle room with regard to the licence and what version you have. Maybe this is a little off from what you meant but I'm pretty sure you can use an XP Pro licence with and XP Home install and it'll take it.

> **garyed said:**
> I apologize to all those who tried to help me for not getting back sooner.
I kind of gave up trying to put Windows on & have just been running Ubuntu.
I rarely have a need for Windows so its not that big a deal but it would be nice to have it for those occasions when I need it. I do have an OEM CD of XP that I use on my desktop that I could install but then I'd probably be violating some terms with MS & have to deal with registering too. It just seems to me that if my Rescue partition is in tact then there should be a way to reinstall everything like it was when it was new.


Have you heard of Bart PE? I just found out about it and it seems interesting. Apparently, you have to have an install cd but it makes an installation of Widows on a usb/ that will run from usb. I like the idea that it could, possibly save me in situations where I'm forced (by circumstance) to have a Windows install. That way, at least a guy can still have a choice over what he wants to use his internal hardware/ machine for.

---

### Post by cryptotheslow on 2011-10-12
Downloading torrents is not illegal per se. It depends on the content of said torrent and one's local laws regarding copyright and IP protection. Some jurisdictions target the downloader, some the publisher / seeder, some couldn't give an overripe fig for such things. It's generally best to avoid any discussion on the matter IMHO, usually just ends in aimless circular debates.

The advice to not use a download (torrent or otherwise) of an OS install image from anywhere other than the orginal distributor or trusted mirror is sage. Whether one is in possession of a valid key for said OS or not, you have no idea what may have been slipstreamed into the image.

Now back on topic..... we need to know what version of Windows the OP (garyed?) had installed initially i.e. win2K, XP, Vista, 7, 8 etc. The most latterly versions seem to use two partitions (akin to a /boot and / setup familiar to *nix users).... so the talk of a "recovery" partition may well be just smoke and BS as actually more likely all that remains is the equivalent of the Win /boot partition with an ext4 partition being blasted over the top of the major part of the Win install.

---

### Post by garyed on 2011-10-12
The sticker on the bottom of the computer says XP Home but it doesn't say what version. I do have XP SP2 Home OEM CD that I bought for a new system build but I don't want to have to deal with the license crap from MS.
Evidently the recovery is looking for something it can't find to do the install. Whether it's the because the partitioning is different or whether there's some bad sectors on that partition I have no idea.

---

### Post by cryptotheslow on 2011-10-12
OK - so it would seem the laptop was originally installed with WinXP, but we are not sure what Win version was installed at the point you decided to blow away that second partition (it may have been upgraded etc.). Everything that follows assumes that the orignal WinXP was the installed OS in force and you don't wish to try to save anything (files etc.) that was on the laptop. If you wish to recover files **stop reading here and desist further action - just post up stating your wish to recover files.**

Best guess as you seem to be able to access some kind of Win recovery mode is that the first partition holds the manufacturer's recovery and you blew away the actual install of XP in the 2nd partition.

1. Boot from the Ubuntu LiveCD / USB and use GParted to remove every other partition other than the 1st. Remove CD, reboot and try the Win recovery option.

2. If unsuccessful. Boot from the Ubuntu LiveCD and use GParted to create an NTFS formatted primary partition (sda2) using the rest of the drive that is after the 1st partition (sda1). Remove CD, reboot and try Win recovery option.

For those picking this up - My fundamental approach here is to try to get a vanilla Win install done then once successful look to put Ubuntu alongside.

Beer quotient now nearing > sense limit here so departing for a few hours. :D

---

### Post by garyed on 2011-10-14
> **cryptotheslow said:**
> )........ Remove CD, reboot and try Win recovery option........


I haven't found a way to access the recovery partition other than through Grub. I've been Googling forever trying to find a way to boot into the recovery partition & none of the advice so far has worked. I either get into the bios or end up in a Grub menu. If anyone knows how to boot into the recovery partition on a Sony Vaio PCG-7A2L please enlighten me.

---

### Post by asomad on 2012-02-19
> **Mark Phelps said:**
> The OEM version of Windows that came with your desktop is only legal to use on that PC -- OEM licenses are actually matched to individual PCs.  If you want to reinstall that copy on that PC, you can do that.  What you can't do is use that copy on a different PC.

As to restore, every OEM does it differently, and even for different PCs from the same OEM.  Generally, you either press a special key combination, or you insert a Recovery CD, to start the Restore operation.  The sequence depends on your particular PC -- and is documented with the PC.

If you change or move the partitions on the drive, that will often prevent an OEM restore from working. In that case, you generally have to remove all the partitions except the Recovery partition (the one containing the Windows image file) and try the Restore again.

A manufactured pc with windows has a license for one copy of windows on it. even without a restore partition, he is entitled one license for windows as long as that MACHNE is the one running it. meaning XP can be installed on it, using a Windows xp install cd, and microsoft activation will see that his machine is entitled to a copy of  windows, and activation will be allowed. 

That said. what you CANNOT do is use a license from an OEM machine to install windows on ANY other machine. 

But simply put, if you have a computer that came with windows, microsoft activation will work to activate the same version of windows reinstalled. you just may need to make a 30 second phone call to a computerized system for a key.
Only catch is you need a disk to use that's not someone else's manufacturers disk, but instead a microsoft windows install disk, or the disk that came with your pc.

---

