---
title: "How to uninstall Ubuntu 11.10 without using windows"
date: 2011-10-14
forum: General Help
---

### Post by jsantos28 on 2011-10-14
Hello i searched threw all the forums and could not find the answer.

This is a dual boot and i wanted to know how or if i can uninstall my version of Ubuntu without using my windows. Unfortunately i forgot my password as i haven't used windows since ive downloaded Ubuntu but now i need to get on it and have no way to uninstall Ubuntu and replace it with 10.4. Any help will be much appreciated.

---

### Post by MG&amp;TL on 2011-10-14
So....you want to get back to a dual-boot with windows and ubuntu 10.04?

---

### Post by jsantos28 on 2011-10-14
No i just want to know how to uninstall my current version of Ubuntu but do that without using windows since i cant get in windows because i lost my windows password

---

### Post by coffeecat on 2011-10-14
> **jsantos28 said:**
> No i just want to know how to uninstall my current version of Ubuntu but do that without using windows since i cant get in windows because i lost my windows password

Hmmm.. Welcome to the forum, by the way.

I must admit to being mystified by this. If you uninstall Ubuntu you won't be able to boot into any operating system. Is this what you want? Anyway, I have a feeling that you have a wubi installation which will be an interesting challenge to uninstall if you cannot log into Windows. So that we can see whether you have a wubi install or a conventional dual-boot, boot into Ubuntu, open a terminal and post the output of these two commands:

```
mount
sudo fdisk -lu
```

---

### Post by jsantos28 on 2011-10-14
```
/dev/sda5 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=600)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/julius/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=julius)
/dev/sdb1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
```


```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x427c8947

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    82835455    41416704    7  HPFS/NTFS/exFAT
/dev/sda2        82835456   287338629   102251587    7  HPFS/NTFS/exFAT
/dev/sda3       287340542   488396799   100528129    5  Extended
/dev/sda5       287340544   484218879    98439168   83  Linux
/dev/sda6       484220928   488396799     2087936   82  Linux swap / Solaris

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cfad0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     7821311     3910640    b  W95 FAT32
```




Well i was going to use the try Ubuntu thing that i already have on my flash drive once i uninstall this current version.

---

### Post by jsantos28 on 2011-10-14
Woa sorry all the numbers kind of merged there but hoped that helped

---

### Post by mick222 on 2011-10-14
Why not try to recover your windows password. This program might help [http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/) download the live cd or download from software centre

---

### Post by jsantos28 on 2011-10-14
Woa ummm im probably not capable to do this without instructions and such im no Linux expert so i dont think i can pull that off

---

### Post by westie457 on 2011-10-14
> **mick222 said:**
> Why not try to recover your windows password. This program might help [http://ophcrack.sourceforge.net/](http://ophcrack.sourceforge.net/) download the live cd or download from software centre

+1 

On the web-site there is also the option to download a live cd.

---

### Post by coffeecat on 2011-10-14
> **jsantos28 said:**
> Woa sorry all the numbers kind of merged there but hoped that helped

I've added code tags for you. :)

Your output shows that you have Ubuntu on its own partition. This means that grub will be installed to the mbr of the hard drive. To "uninstall" Ubuntu you would need to delete the Ubuntu partitions. However this would make Windows unbootable until you repaired the Windows bootloader in the mbr. This is easily done, but since others are helping you with your Windows password, I suggest we defer removing Ubuntu - if you still want to - until you've solved that issue. Is that OK?

---

### Post by jsantos28 on 2011-10-14
> **westie457 said:**
> +1 

On the web-site there is also the option to download a live cd.
Well i would do that but i do not have any CD's anymore just USB and it appears i cant do anything

---

### Post by jsantos28 on 2011-10-14
> **coffeecat said:**
> I've added code tags for you. :)

Your output shows that you have Ubuntu on its own partition. This means that grub will be installed to the mbr of the hard drive. To "uninstall" Ubuntu you would need to delete the Ubuntu partitions. However this would make Windows unbootable until you repaired the Windows bootloader in the mbr. This is easily done, but since others are helping you with your Windows password, I suggest we defer removing Ubuntu - if you still want to - until you've solved that issue. Is that OK?
It seems others cannot help me so can you still try helping me out with my issue

---

### Post by CharlesA on 2011-10-14
Hi,

Do you have a Windows cd you can boot off of?

You'd need one to fix the mbr after removing Ubuntu.

As for the password thing, you can probably reset it from Ubuntu, but that's not something we support here. Your best bet would be to boot into Windows and check to see what the password hint says since it should have asked you for one when you created your account.

---

### Post by coffeecat on 2011-10-14
> **jsantos28 said:**
> It seems others cannot help me so can you still try helping me out with my issue

People are trying to help, but do you see why I am hesitant to tell you how to remove Ubuntu before you have solved your Windows password problem? I don't want to leave you with an unusable computer.

If the password hint that CharlesA suggests helps, let us know which version of Windows you are using and whether you have a repair or installation CD. It is possible to repair the Windows MBR with an Ubuntu CD, if you don't have one.

---

### Post by jsantos28 on 2011-10-14
> **CharlesA said:**
> Hi,

Do you have a Windows cd you can boot off of?

You'd need one to fix the mbr after removing Ubuntu.

As for the password thing, you can probably reset it from Ubuntu, but that's not something we support here. Your best bet would be to boot into Windows and check to see what the password hint says since it should have asked you for one when you created your account.
To answer your question unfortunantly no i do not have the windows CD. and i am aware of thing you can do to change your password from using Ubuntu but i guess the new version that i just downloaded does not have the same time of things as the other ones had(sorry if that was unclear)

---

### Post by CharlesA on 2011-10-14
> **jsantos28 said:**
> To answer your question unfortunantly no i do not have the windows CD. and i am aware of thing you can do to change your password from using Ubuntu but i guess the new version that i just downloaded does not have the same time of things as the other ones had(sorry if that was unclear)
What version of Windows are you using?

---

### Post by jsantos28 on 2011-10-14
> **CharlesA said:**
> What version of Windows are you using?
Windows xp

---

### Post by CharlesA on 2011-10-14
> **jsantos28 said:**
> Windows xp
Ok - I cannot recall if that had a password hint or not, but I don't think it did.

I thought you had to fix the mbr from a windows cd. I haven't done a dual boot in a while.

---

### Post by jsantos28 on 2011-10-14
> **CharlesA said:**
> Ok - I cannot recall if that had a password hint or not, but I don't think it did.

I thought you had to fix the mbr from a windows cd. I haven't done a dual boot in a while.
Yes there is a password hint but its not very useful information. and i did a dual boot from a USb flash drive

---

### Post by jsantos28 on 2011-10-14
Would i be in violation of the terms of service if i posted a new thread of the password finder threw Ubuntu as you mentioned before????

---

### Post by CharlesA on 2011-10-14
> **jsantos28 said:**
> Yes there is a password hint but its not very useful information. and i did a dual boot from a USb flash drive
Ah ok. I guess you can give Ophcrack a shot, and if that doesn't work, try posting over on the sevenforums (they support xp too!)

> **jsantos28 said:**
> Would i be in violation of the terms of service if i posted a new thread of the password finder threw Ubuntu as you mentioned before????

It would probably get closed since we don't really support cracking here. Check out the sevenforums tho, they might have a better way to get access to XP.

---

### Post by jsantos28 on 2011-10-14
Okay well thanks for the help anyways.

---

### Post by cmcanulty on 2011-10-14
If I remember correctly you can boot windows in safe mode and change password in XP also can enter bios and change passwords. Bios usually starts as soon as power on with hitting, esc, del, or one of the F numbered keys.

---

### Post by CharlesA on 2011-10-14
> **cmcanulty said:**
> If I remember correctly you can boot windows in safe mode and change password in XP also can enter bios and change passwords. Bios usually starts as soon as power on with hitting, esc, del, or one of the F numbered keys.
That only works if you know what the Administrator password is.

Also, the bios password wouldn't affect the OS. :)

---

### Post by Is Mise on 2011-10-14
> **jsantos28 said:**
> Hello i searched threw all the forums and could not find the answer.

This is a dual boot and i wanted to know how or if i can uninstall my version of Ubuntu without using my windows. Unfortunately i forgot my password as i haven't used windows since ive downloaded Ubuntu but now i need to get on it and have no way to uninstall Ubuntu and replace it with 10.4. Any help will be much appreciated.

If all you want to do is replace your current Ubuntu install with Ubuntu 10.04 you can just install it over your existing Ubuntu partition using the live USB you created. There's no need to uninstall your old partition first, just make sure to back up your data before you do this.

---

### Post by jsantos28 on 2011-10-14
> **Is Mise said:**
> If all you want to do is replace your current Ubuntu install with Ubuntu 10.04 you can just install it over your existing Ubuntu partition using the live USB you created. There's no need to uninstall your old partition first, just make sure to back up your data before you do this.
I already tried that and nothing happened

---

### Post by CharlesA on 2011-10-14
> **jsantos28 said:**
> I already tried that and nothing happened
What do you mean nothing happened?

---

### Post by mixmastamyk on 2011-10-14
Take the older Ubuntu Live CD, boot it and run the installer.

During the install, select manual partition editing.  Then do what you need to.  Remove the partition, format it, or just install 10.04 over the top of it.  

The last choice should wipe out the OS and keep your home folder.

---

### Post by jsantos28 on 2011-10-14
> **CharlesA said:**
> What do you mean nothing happened?
I i installed a version on my usb but when i booted it up it just went to the normal setup

---

### Post by Mark Phelps on 2011-10-14
There's no app or utility you can find that will "recover" your Windows password -- no matter what they say.

If you do some Googling, you will be able to find tools that will "reset" your windows password -- but they all require being booted to CD.

So, if you don't have any CDs, or are unwilling to buy any, you've pretty much eliminated the options that will work.

---

### Post by CharlesA on 2011-10-15
> **Mark Phelps said:**
> There's no app or utility you can find that will "recover" your Windows password -- no matter what they say.

If you do some Googling, you will be able to find tools that will "reset" your windows password -- but they all require being booted to CD.

So, if you don't have any CDs, or are unwilling to buy any, you've pretty much eliminated the options that will work.

That's true. Outside of cracking said password, there isn't a way to "recover" it - but there are ways to reset - using an Administrator account in Windows to reset that user's password, for example.

---

### Post by MG&amp;TL on 2011-10-17
How long is the password? 

I find that <5 chars passwords can be cracked inside of 20 minutes (I've had to do it myself), using the SAM files in Linux from the Windows partition.

Although OF COURSE this would only apply to your own password.

---

### Post by manusweet23 on 2011-11-28
i have installed ubuntu 11.10 on my acer netbook as dual boot with builtin windows XP in that netbook, now i need only windows XP in that and completely uninstall ubuntu 11.10, there is no cd drive in my net book, so any one can please help me how to uninstall ubuntu in it..

---

### Post by cmcanulty on 2011-11-28
did you install it through wubi? If so just go to add remove programs in control panel and remove.

---

### Post by TCity on 2011-12-28
I'm not sure if I should open a new post, but nobody has answered the original poster's question. It seems like there is a reluctance to answer the original question. Also, using the search phrase, "How to uninstall Ubuntu 11.10" in all forums yielded no results! Here are my specifics: I'm running XP Home and Ubuntu 11.10 on a custom built desktop with two hard drives. XP was installed first and is on the 250GB and Ubuntu 11.10 decided to install itself on the 1TB hard drive. I used the default choice to install along side Windows and always choose which OS to boot into. I had hoped there would be one more step before Ubuntu installed itself using that choice, but alas it just started installing. I kept 100GB free on the 250GB drive to install Ubuntu and was going to keep the 1TB drive free for use with both OSes. So how do I uninstall Ubuntu without messing up the current Windows install? I am going to re-install Ubuntu afterwards using my choices on the 250GB in the unallocated portion of the drive. Please, I just want to know how to uninstall Ubuntu 11.10 without messing up Windows and remove the bootloader. Thanks very much, Chuck

---

### Post by TCity on 2011-12-28
Here's additional info to my/the question directly above. I used a CD with Ubuntu 11.10 burned onto it to install Ubuntu 11.10. I did not use Wubi. The default install choice is the top/first in the list.

---

### Post by TCity on 2011-12-29
I went ahead and took care of this myself. I booted the computer with the XP CD and waited for it finish loading. I then pressed "R" for the Recovery Console. I chose "1" for the C:\Windows installation and pressed "Enter" for the non-existent Administrator password. I typed "fixmbr" and typed "y" when asked if I wanted to fix/replace the master boot record. I typed "exit" and the computer restarted straight into Windows. I then used a Western Digital app to re-partition the 1TB hard drive. (It is a WD hard drive). Then I finally installed Ubuntu 11.10 in the free space on the 250GB hard drive using the manual or third choice after booting from the burned Ubuntu CD. All commands above do not include the quotation marks.

---

### Post by PlsNoAbreviations on 2012-01-02
I am experiencing a mixture of the same problems as manusweet23 and Tcity and obviously we really need to know the answers to this question.  

I found one partial solution here [http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/) however since I am running a netbook originally running Windows 7 I can not boot into a cd and so can not enter the commands to rebuild the master boot record.  I did thankfully backup my system on a pen drive but I don't want to go through the hours and hours of reconfiguring my system and that backup drive does not have the option to go into command prompt.

I have been trying out different versions of Ubuntu.  I originally had Ubuntu 11.10 installed by Wubi but uninstalled it (which was beautifully easy) because I wanted to try an older version.  I booted that older version to pendrive and decided I didn't like it and thought I'd just go back to 11.10.  The second time I installed 11.10 I still chose to do it through Wubi but it told me to restart my computer and install it after booting from the pen drive.  I had done this the first time too and it installed through WUBI.  However, the only difference I can recall I made this time is I selected the option to make the home (?) folder secure and so it made its own partitiions.  For some reason the OS did not install properly and I really wanted to install the WUBI verion, however, I am unable to find a practical way to uninstall Ubuntu 11.10.  It seems to have made two new partitions for itself in addition to the 3 existing windows 7 ones.

---

### Post by PlsNoAbreviations on 2012-01-02
I found a solution to this.  

[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

What the instructions say (that are conveniently placed on the main page with links) is that if your windows os is corrupted you can attach your harddrive as a slave to another computer running windows and run all the commands.

1. To be cautious using the utility I rebuilt the master boot record (MBR) before deleting any partitians so I wouldn't have to fool around with any boot "disks" or dos prompts that don't respond to commands.  note:BE SURE TO CLICK APPLY TO MAKE THE CHANGES AFTER EACH OPERATION, or it will sit in pending mode and later try to do everything all at once which can cause an error.

2.  Wipe each of the unneeded partitions that the linux os was using.  This takes some time.  And be very careful not to wipe any of the windows or backup partitions.

[edit] 3.  Partition the unallocated space.

4.  Use the merge partition function so your harddrive is whole again.   This requires a reboot.  It reboots again after performing the operation.  Do it carefully and it will work.  Make sure you run it from an admin and have no other programs running and no power saving options being used.

5.  Next time use Wubi.

---

### Post by nickdc on 2012-01-04
> **mixmastamyk said:**
> Take the older Ubuntu Live CD, boot it and run the installer.

During the install, select manual partition editing.  Then do what you need to.  Remove the partition, format it, or just install 10.04 over the top of it.  

The last choice should wipe out the OS and keep your home folder.

If only it was that simple!

I found my way here, like others, after searching for what I thought would be straightforward guidance for a straightforward task. I'm reluctant to use the Windows repair option from the WinXP cd to restore the mbr as I've hit problems with it in the past and I'm having to be extra cautious as it's not my own pc I'm working on; I'd prefer to do everything from within Ubuntu. But when I try to install 10.04 over 11.10, choosing the manual option as you suggest, mixmastamyk, there is no option to simply write the older version over the newer, installed one. I can delete the two linux partitions, but then I'm lost when I'm confronted with all the options re choosing mount points etc, about which I have little idea (presumably why the manual option is labeled "advanced"). I thought I might get round it by quitting the installation after deleting the partitions and then starting again so the freed up unallocated space would be available second time round; but no, the installer cleverly (and I understand why and commend it!) puts everything back as it was before quitting!
Please could someone provide or point me to some clear instructions for relative beginners on how to configure the partitions, mount points etc when installing Ubuntu using the manual option?

---

### Post by cmcanulty on 2012-01-04
Under advanced pick these options from the drop down boxes.Setup a partition with around 5-20GB for / and make it ext4. Mark it to format. Set up a small partition 1-5GB as linux swap.Setup or keep your home partition mark it to be ext4 and mount point /home. Don't format that partition if you want to keep your settings.If you need to delete a partition select it rt click and delete. You can have a max of 4 primary partitions. If you need more make one or 2 logical partitions. Backup everything 1st in case you make a mistake.

---

### Post by nickdc on 2012-01-04
> **cmcanulty said:**
> Under advanced pick these options from the drop down boxes.Setup a partition with around 5-20GB for / and make it ext4. Mark it to format. Set up a small partition 1-5GB as linux swap.Setup or keep your home partition mark it to be ext4 and mount point /home. Don't format that partition if you want to keep your settings.If you need to delete a partition select it rt click and delete. You can have a max of 4 primary partitions. If you need more make one or 2 logical partitions. Backup everything 1st in case you make a mistake.

Hi, and thanks for responding so quickly! I'm not sure which version or stage of the installer you're referring to, but your instructions don't quite fit what I see on my screen. 

I'm trying to install U 10.04 over 11.10. At step 4 of 7 ("Prepare disk space"), when I chose the third option (Specify partitions manually (advanced)), the next screen (step 5 of 8, "Prepare partitions"), presents a table of the existing installations with six columns, four of which identify the different partitions, file systems and sizes, while the middle two, headed "Mount point" and "Format?" are blank/awaiting input. Below are some buttons, only two of which are active*: "New partition table" and "Revert". The table shows my two physical drives, /dev/sda and /dev/sdb. I want to leave sdb well alone. On sda there are partitions as follows: sda1 and 2 are both clearly Windows (fat32 and NTFS respectively), the others linux: sda5 is an ext4 partition and 6 is identified as swap. (I don't see any sda3 or 4 - are they hidden/do they exist ...? )
What do I need to do on this screen, in order to install Ub.10.04  exactly where the 11.10 is now? :confused:

Edit: * Have just realised the active buttons change when I highlight an individual partition rather than the entire disk. On individual partitions the "new partition table" option is greyed out and the active options become: "Change", "Delete" or "Revert". (There's also, of course, "Quit", "Back" and "Forward" at the bottom.)
Even more unsure what to do next!

---

