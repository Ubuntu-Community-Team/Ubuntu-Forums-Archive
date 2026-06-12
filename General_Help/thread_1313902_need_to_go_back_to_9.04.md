---
title: "need to go back to 9.04"
date: 2009-11-04
forum: General Help
---

### Post by calfee1 on 2009-11-04
installed 9.10 and the internet is just crawling. Can't do anything. Want to go back to 9.04. How do I do this? I have a live cd ready to go but have no idea how to proceed with getting rid of one and replacing it. Thanks

---

### Post by dvlchd3 on 2009-11-04
Make sure you have all your files backed up in 9.10.

Proceed with the installation as normal.  This will erase 9.10 and install 9.04.

---

### Post by calfee1 on 2009-11-04
Using the live CD how do I get rid of 9.10. It does not seem to let me do that. It will let me decrease my XP but not 9.10....I am missing something here???

---

### Post by ColdFFF on 2009-11-04
Choose the manually configure partitions option and choose to use your existing / partition as the new / partition. If you have separate /boot, /home etc. partitions make sure to use them as such as well. A default install will not have these separate partitions though.

---

### Post by calfee1 on 2009-11-04
OK I choose manual and it get me to prepare partitions.......No idea what to do here. I can ID my XP, 9.10 and swap partitions.

---

### Post by ColdFFF on 2009-11-04
Select the 9.10 partition, and I think there was an edit button. Click that.

In the window that pops up, you can choose the filesystem (default for 9.04 is ext3, though you can use ext4), choose whether to format the partition (forced if you change the filesystem), and choose where to mount the partition. You want to mount it as the root partition, indicated by /

---

### Post by calfee1 on 2009-11-04
so am I using the same ext as 9.10 to overwrite with 9.04....](*,)

in the preparing partitions section. Is it the fat16 that is 9.04. If so, I hit edit. Make it the same size as current 9.10. The choice file system is ext/journaling or something like that.

---

### Post by coffeecat on 2009-11-04
> **calfee1 said:**
> so am I using the same ext as 9.10 to overwrite with 9.04....](*,)

Not quite sure what you mean there. You can use either ext3 or ext4 for either 9.10 or 9.04. It's just that the default (if you didn't make a choice yourself) was ext3 in 9.04 and the default is now ext4 in 9.10.

---

### Post by calfee1 on 2009-11-04
> **coffeecat said:**
> Not quite sure what you mean there. You can use either ext3 or ext4 for either 9.10 or 9.04. It's just that the default (if you didn't make a choice yourself) was ext3 in 9.04 and the default is now ext4 in 9.10.
ext3 is the one assigned to 9.10. Where I get lost at is which one is now 9.04(i assuming fat16) and I want to change that to the size of 9.10 and make it the ext3 as root. But the edit box does not give the ext3 as an option. Do i have to delete the 9.10 partition first. Wish I could make screen shots. to make my questions clearer.

would it be any easier to delete/uninstall 9.10. Leaving XP as the only OS and then install 9.04.....of course, I have no idea how to do this either. I have no data on 9.10 i need to keep.

---

### Post by ColdFFF on 2009-11-04
Currently there is no 9.04 on your system.

Select the ext3 partition and choose to use that as root.

---

### Post by coffeecat on 2009-11-04
> **calfee1 said:**
> ext3 is the one assigned to 9.10. Where I get lost at is which one is now 9.04(i assuming fat16) and I want to change that to the size of 9.10 and make it the ext3 as root. But the edit box does not give the ext3 as an option. Do i have to delete the 9.10 partition first. Wish I could make screen shots. to make my questions clearer.

I think you've got in a bit of a muddle. :) If I read this thread correctly, you've been advised to mark your current 9.10 root partition (/) as the root partition for the 9.04 install. Whether you choose ext3 or ext4 doesn't really matter that much - except for people really interested in filesystem performance. If you change from ext3>ext4 or vice versa a reformat of that partition will be forced. If you keep the same ext3 or ext4 and do not mark for reformatting the installer will ask you if you are sure, and will then erase all system files, but will retain your /home directory on the partition. This is a little known feature of the installer and can be useful. But if you've not done much configuring in 9.10, I wouldn't bother with that - it's probably safer and better to tell the installer to reformat the / partition whatever filesystem you choose.

Now - **DO NOT TOUCH THAT FAT16 PARTITION**. Or at least until we get more information. I'm surprised that you have a FAT16 partition on a modern hard-drive. FAT16 is ancient. I guess it may be something to do with a manufacturer's restore utility and you may need it to repair Windows - or something like that.

Here's a suggestion: from the live CD*, open a terminal and post the output of:

```
sudo fdisk -l
```(That's a lower-case L). Do a copy and paste from the terminal. You don't want to be typing all that stuff. That will give us your partition layout and we can advise you better.

***Edit**: If you still have a working 9.10 (I'm not sure - I've slightly lost the plot here :p ) then you can do a fdisk from your working 9.10. No need to boot into the live CD if so.

---

### Post by calfee1 on 2009-11-04
using 9.10 as its still working. Have not touched anything as you can tell I have no idea for the most part what I am doung. Here is the result from terminal.

   Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       31680   254413372+   7  HPFS/NTFS
/dev/sda3           32007       60801   231295837+   5  Extended
/dev/sda5           32007       60686   230372068+  83  Linux
/dev/sda6           60687       60801      923706   82  Linux swap / Solaris

---

### Post by coffeecat on 2009-11-04
Good. All we need to know is here.

> **calfee1 said:**
> /dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8       31680   254413372+   7  HPFS/NTFS
/dev/sda3           32007       60801   231295837+   5  Extended
/dev/sda5           32007       60686   230372068+  83  Linux
/dev/sda6           60687       60801      923706   82  Linux swap / Solaris

I'll explain it.

I guess the FAT16 partition is sda1, (partiton #1) the Dell Utility. **Leave it alone.** :wink:

sda2 is your Windows C: partition, and sda3 is an extended partition which is simply a "container" for your two logical Linux partitions, sda5 and sda6. When you get to the installer, leave sda2 and sda3 alone.

If you're still running 9.10, then its root (/) partition is sda5. So, if you want to install 9.04 and replace 9.10 in one go, all you need do is choose 'Manual' in the installer, highlight sda5, click on "edit" or "change" (I can't remember which), set that as ext3 or ext4 - whichever you wish, tick the box for reformatting, and set the mountpoint as "/". But re-read the earlier posts - this has already been explained. You need do nothing else, except proceed with the installation. The swap partition will be picked up automatically. At the last page, just before the installer proper starts, you will be prompted with all the formatting and filesystem changes. Check that those are correct and that it's pointing to sda5 for /, and proceed if you are happy.

---

### Post by calfee1 on 2009-11-04
Thanks for the instructions in last response. I will try this later today and post results. I do have one other question. Could this SLOW internet issue be because of a conflict with upgrade. Would it be worth to do a clean install and if so how is this done.

---

### Post by sillyfishyboy on 2009-11-04
I dont know if a clean install would work any better unless you have messed with network settings.  Although if you have not done a clean install in a while it is always a good idea to occasionally clear out any redundant files etc.

Doing a clean install is a pleasure with ubuntu.  just download the required iso from the ubuntu site (or torrent to save bandwidth), burn it to cd, then restart your computer with the cd in and follow the directions to 'install'.  Usually only takes 20 minutes or so and if you havnt done it in a while your computer will be lightening fast and a pleasure to use.  You may have to do a bit of tweaking post install depending on your hardware to ensure your graphics / sound is working properly.

---

### Post by coffeecat on 2009-11-04
> **calfee1 said:**
> I do have one other question. Could this SLOW internet issue be because of a conflict with upgrade. Would it be worth to do a clean install and if so how is this done.

That's two questions! Even without the question marks. :p

Yes we did rather forget the slow internet. How do you connect, wired or wireless? If wireless, details of the chipset of your wireless device are needed to be able to make any useful answer.

By the way, you **are** doing a clean install - if you follow the advice I and others have given you. Why are you asking how it is done?

---

### Post by calfee1 on 2009-11-04
> **coffeecat said:**
> That's two questions! Even without the question marks. :p

Yes we did rather forget the slow internet. How do you connect, wired or wireless? If wireless, details of the chipset of your wireless device are needed to be able to make any useful answer.

By the way, you **are** doing a clean install - if you follow the advice I and others have given you. Why are you asking how it is done?

The computer is a wired desktop. I guess I was asking is it worth trying to do a reinstall with 9.10 as I had upgraded from 9.04. Thanks for all the assistance. I will post result of what I did. Keep fiingers crossed.......

---

### Post by calfee1 on 2009-11-05
> **coffeecat said:**
> Good. All we need to know is here.



I'll explain it.

I guess the FAT16 partition is sda1, (partiton #1) the Dell Utility. **Leave it alone.** :wink:

sda2 is your Windows C: partition, and sda3 is an extended partition which is simply a "container" for your two logical Linux partitions, sda5 and sda6. When you get to the installer, leave sda2 and sda3 alone.

If you're still running 9.10, then its root (/) partition is sda5. So, if you want to install 9.04 and replace 9.10 in one go, all you need do is choose 'Manual' in the installer, highlight sda5, click on "edit" or "change" (I can't remember which), set that as ext3 or ext4 - whichever you wish, tick the box for reformatting, and set the mountpoint as "/". But re-read the earlier posts - this has already been explained. You need do nothing else, except proceed with the installation. The swap partition will be picked up automatically. At the last page, just before the installer proper starts, you will be prompted with all the formatting and filesystem changes. Check that those are correct and that it's pointing to sda5 for /, and proceed if you are happy.


So I do not screw this up. In the box where set the ext3 or ext3 that choice is not that exactly. The choices similiar to that is:

Ext3 journaling file sytem
Ext4 journaling file system
ext2 file systtem

Which one do I use

Thanks

---

### Post by Monotoko on 2009-11-05
Ext3 journaling file system :)

---

### Post by calfee1 on 2009-11-05
Success!!!!!!!!!!!!!!!Thanks to everyone who helped. Will mark as solved......YAHOOOOO

---

