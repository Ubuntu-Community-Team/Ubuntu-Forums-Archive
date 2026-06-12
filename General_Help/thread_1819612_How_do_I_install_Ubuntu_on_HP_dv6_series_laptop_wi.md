---
title: "How do I install Ubuntu on HP dv6 series laptop with 4 partitions already?"
date: 2011-08-06
forum: General Help
---

### Post by inameiname on 2011-08-06
A friend just got a computer and for now, wants to keep the already installed Windows there, but prefers Ubuntu, and wants to install it and use it mainly. Usually, this is a matter of just running the live usb of Ubuntu and selecting to install Ubuntu alongside Windows. Unfortunately, though, the Windows that is installed on the machine is already using 4 partitions. So before I erase one and install Ubuntu, I figured I'd get help on knowing just how to go about doing this the safest possible way.

Currently, the partition structure is as folllows for this HP Pavillion dv6 series laptop: 

```

1. System (NTFS) 209MB with the following folders -> /Boot, /Sys. Vol. Info, /Boot Manager
2. C Drive (NTFS) 624GB
3. Recovery (NTFS) 15GB with -> /Boot, /Fact. Update, /HP, /Preload, /Recovery, /RM_Reserve, /System Vol Info, /Boot Manager, /Desktop.ini
4. HP_Tools (FAT..I think) 108MB with -> /Hewlett Packard

```Reading other people's attempts to fix this, I think I have a solution, but it is a bit unclear. Here is how I think it will need to be:

```

1. Delete HP_Tools (copying first to C:// or somewhere else)
2. Shrink C://
3. Make new extended partition
4. Use HP_Tools and Linux Partitions as logical ones
5. Create new Fat32 for HP_Tools

```Now, i get those steps, but unsure if they are correct, as well as just how to go about doing them. So any help would be greatly appreciated.

---

### Post by mikewhatever on 2011-08-06
The plan sound about right, though I don't know what the HP Tools partition is for. You might want to contact HP tech support and ask if it is safe to delete it.
As for the practical side of the project, you can use a partition manager called Gparted from the Ubuntu CD. It has an easy graphical interface, but do not hesitate to ask if you get stuck at whatever point.

---

### Post by Quackers on 2011-08-06
Don't forget to defragment Windows before you shrink the C: drive.

---

### Post by inameiname on 2011-08-06
> **mikewhatever said:**
> The plan sound about right, though I don't know what the HP Tools partition is for. You might want to contact HP tech support and ask if it is safe to delete it.
As for the practical side of the project, you can use a partition manager called Gparted from the Ubuntu CD. It has an easy graphical interface, but do not hesitate to ask if you get stuck at whatever point.

Thanks for the tip. I was actually thinking of using Gparted as Im currently in my Remastered Ubuntu and am sort of familiar with Gparted already. And hp_tools does seem to be the one partition to get rid of, as it is indeed nothing especially important. Although, looking at the above steps, it sounds like I can copy it and put it back onto a logical partition or something? 

Anyway, Gparted seems to be the way to go, but I am currently not sure just what to do once in it. I mean I know how to shrink the main "C://" drive partition, but then how exactly am I to install Ubuntu and its three partitions as well as add a fat32 hp_tools partition back on it? Oh, and also a Boot Manager so I can dual boot. I've made several partitions on flash drives before, but never as complicated as this in figuring out, particularly logical, primary, extended drives and such. Typically I'm an Ubuntu only person so its much easier and avoids all of this. Hehe

---

### Post by inameiname on 2011-08-06
> **Quackers said:**
> Don't forget to defragment Windows before you shrink the C: drive.


Yep, already did that prior to restarting and booting up this Live Ubuntu USB.

---

### Post by mikewhatever on 2011-08-06
I doubt that recreating Hp Tools as a logical partition would do any good. In case it's used by Windows or something else, it likely won't be able to use the new logical partition. Not having to recreate HP Tools simplifies the matter. After deleting the partition, reboot and start the Ubuntu installation. You should be offered the usual 'side by side' option.

---

### Post by inameiname on 2011-08-06
> **mikewhatever said:**
> I doubt that recreating Hp Tools as a logical partition would do any good. In case it's used by Windows or something else, it likely won't be able to use the new logical partition. Not having to recreate HP Tools simplifies the matter. After deleting the partition, reboot and start the Ubuntu installation. You should be offered the usual 'side by side' option.


So minus keeping that hp_tools partition stuff, if I do delete that partition, sda4 in this case, I can then restart into the usual Ubuntu installation and it'll install all three partitions into that one primary partition slot and that's that? I know I'm just rehashing what you just told me, but I just wanna make sure as best as I can.

First step then would be to use Gparted to delete sda4, or the hp_tools partition. Should I also resize the C:// drive through it or will the actual Ubuntu installation allow me to do that too.

Also, technically, once I were to do that, couldn't I make a fourth partition inside that sda4 fourth partition, alongside the three Ubuntu ones, using Gparted through the live usb, and make a new hp_tools partition? I think that's what the other people who have had this issue found their solution as well.

Oh, and to better understand in general, each of the 3 (or 4) I would have inside that current /sda4 slot, which is called the primary, they would all be called 'extended', is that right?

---

### Post by inameiname on 2011-08-06
I ran across this Ubuntu Forums article that seems to be regarding my very issue:

[http://ubuntuforums.org/showthread.php?t=1556573](http://ubuntuforums.org/showthread.php?t=1556573)

I'm looking to see if it may help.

UPDATE:

Many seem to have followed a similar method as I am trying to do. Though, the original poster did so by deleting the actual Recovery partition and then manually installing each of the three Ubuntu partitions. But I guess its pretty much the same.

---

### Post by mikewhatever on 2011-08-06
> **inameiname said:**
> So minus keeping that hp_tools partition stuff, if I do delete that partition, sda4 in this case, I can then restart into the usual Ubuntu installation and it'll install all three partitions into that one primary partition slot and that's that? I know I'm just rehashing what you just told me, but I just wanna make sure as best as I can.

That's my guess, but if not, you'll need to go with the advanced option and partition manually. It's called 'something else' in 11.04. I'll look for examples of manual partitioning in a bit.

Edit: Check out the guide->[http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html](http://www.ubuntumini.com/2009/11/installing-ubuntu-910-karmic-koala.html)
He deletes an existing partition and then creates / and /home from the free space.

> First step then would be to use Gparted to delete sda4, or the hp_tools partition. Should I also resize the C:// drive through it or will the actual Ubuntu installation allow me to do that too.

The 'side by side' option should take care of resizing.

> Also, technically, once I were to do that, couldn't I make a fourth partition inside that sda4 fourth partition, alongside the three Ubuntu ones, using Gparted through the live usb, and make a new hp_tools partition? I think that's what the other people who have had this issue found their solution as well.

Sure. You can create whatever partitions you want. What three Ubuntu partitions are you talking about? Separate home?

> Oh, and to better understand in general, each of the 3 (or 4) I would have inside that current /sda4 slot, which is called the primary, they would all be called 'extended', is that right?

Not quite. Once you delete sda4 it will become unallocated space. Then, more unallocated space will be created by shrinking the Windows partition. That space is used to create an extended partition which is a container for logical ones. So all the Ubuntu partitions will be logical, and will live inside that extended partition.

---

### Post by CatKiller on 2011-08-06
That's what I did. The fourth (FAT) partition is only to mess up Linux users. It's easy enough to copy the stuff off that partition into a directory somewhere - there isn't much there and none of it especially useful - and blow that partition away. Once you've made your recovery DVDs there's not really much point keeping the other partitions either, IMO.

---

### Post by inameiname on 2011-08-06
> **mikewhatever said:**
> That's my guess, but if not, you'll need to go with the advanced option and partition manually. It's called 'something else' in 11.04. I'll look for examples of manual partitioning in a bit.

Ok, thanks for that.


> **mikewhatever said:**
> The 'side by side' option should take care of resizing.

Okie dokie. Awesome.


> **mikewhatever said:**
> Sure. You can create whatever partitions you want. What three Ubuntu partitions are you talking about? Separate home?

I meant the three Ubuntu partitions that get created: ext4 (/dev/sda1), extended (/dev/sda2), and linux_swap (/dev/sda5) one. Though, looking at them, seems its really only two partitions, with one being an extended.


> **mikewhatever said:**
> Not quite. Once you delete sda4 it will become unallocated space. Then, more unallocated space will be created by shrinking the Windows partition. That space is used to create an extended partition which is a container for logical ones. So all the Ubuntu partitions will be logical, and will live inside that extended partition.

Oh ok. So you can have four primaries, and only one can be called extended. And it is only through that extended one that you can have logical partitions. Does that sound about right? 



UPDATE:

I found another thread that seems quite informative: [http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741) . It actually suggest I resize the actual "C://" drive partition and make it an extended, not the HP_Tools ones. So now I'm conflicted on which of the two to choose.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> That's what I did. The fourth (FAT) partition is only to mess up Linux users. It's easy enough to copy the stuff off that partition into a directory somewhere - there isn't much there and none of it especially useful - and blow that partition away. Once you've made your recovery DVDs there's not really much point keeping the other partitions either, IMO.

Thanks for sharing! Now, out of curiosity, why did you choose to just remove that partition with hp_tools on it and not just convert the C:// drive one, as mentioned in this thread: 

[http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741)

The way the author said things it seemed this was an even better method. Just curious.


And how did you install Ubuntu? Manually or using the side-by-side option through the Ubuntu Live Disk installation? Also, did you have to delete the hp_tools partition and resize C:// partition beforehand in say Gparted?

---

### Post by Topsiho on 2011-08-06
I would suggest to make room for Ubuntu by reorganizing your disk not with GParted, but within Windows. If it is a Windows newer than XP, that has a tool to do this. And after precautions such as defragmenting a number of times.

I once borked Windows by using GParted for this, resulting in Windows not recognizing the partitions on the disk, which were changed (my conclusion, many, on this forum too, say the same thing).

With Windows XP I never had this problem.

After you have made room, unallocated space, you can use this while installing Ubuntu, which uses GParted. Then for Windows nothing changes, and Windows will boot OK.

Ubuntu can very well installed in logical partitions, partitions within an extended partition. I suggest a partition for / (10-15GB, swap (twice the working memory), and the rest of the free spave for /home.

Topsiho

---

### Post by CatKiller on 2011-08-06
The problem is that HP put too many partitions on, so I removed the most useless-seeming one so that there wouldn't be four. I copied the stuff off it first as a least-harm method. It wasn't my computer, otherwise I'd have just nuked all the partitions from orbit.

I used GParted to resize the partition Windows uses as C:. I'd have used the Microsoft tool to do that, but I couldn't find it. I found out afterwards that Windows whinges if you use something else to resize the partition, but after a check it was fine. Having made some unallocated space I created an extended partition to house the Ubuntu partitions as you're planning to do.

Booting to Windows for the first time (bearing in mind it was ostensibly already installed) took the best part of two hours. Installing Ubuntu after I'd sorted out HP's retarded partition scheme took 38 minutes. With the money & expertise that both Microsoft and HP like to crow about, you'd really think they could do better.

---

### Post by Topsiho on 2011-08-06
Glad to read that Windows did boot. Hope it won't take so long next time. Wouldn't know how to fix that.

Topsiho

---

### Post by inameiname on 2011-08-06
> **Topsiho said:**
> I would suggest to make room for Ubuntu by reorganizing your disk not with GParted, but within Windows. If it is a Windows newer than XP, that has a tool to do this. And after precautions such as defragmenting a number of times.

I once borked Windows by using GParted for this, resulting in Windows not recognizing the partitions on the disk, which were changed (my conclusion, many, on this forum too, say the same thing).

With Windows XP I never had this problem.

After you have made room, unallocated space, you can use this while installing Ubuntu, which uses GParted. Then for Windows nothing changes, and Windows will boot OK.

Ubuntu can very well installed in logical partitions, partitions within an extended partition. I suggest a partition for / (10-15GB, swap (twice the working memory), and the rest of the free spave for /home.

Topsiho


Thanks for the tips. So Windows 7 has a Gparted-like thing to do it? 

I am also curious if you could even delete the hp_tools from within Windows through its partitioning software you mentioned. I'm sure there are safeguards to make that hard to do.

PS, does making swap 10-15GB really make that much of a difference than the usual default amount? I've never tried to change it before in all of my past Ubuntu installations, through a half dozen different versions.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> The problem is that HP put too many partitions on, so I removed the most useless-seeming one so that there wouldn't be four. I copied the stuff off it first as a least-harm method. It wasn't my computer, otherwise I'd have just nuked all the partitions from orbit.

I used GParted to resize the partition Windows uses as C:. I'd have used the Microsoft tool to do that, but I couldn't find it. I found out afterwards that Windows whinges if you use something else to resize the partition, but after a check it was fine. Having made some unallocated space I created an extended partition to house the Ubuntu partitions as you're planning to do.

Booting to Windows for the first time (bearing in mind it was ostensibly already installed) took the best part of two hours. Installing Ubuntu after I'd sorted out HP's retarded partition scheme took 38 minutes. With the money & expertise that both Microsoft and HP like to crow about, you'd really think they could do better.



"Windows whinges if you use something else to resize the partition"...?

Hmmmm, so Gparted worked, and Windows still booted, ehy? Hmmm, I am now debating on using Gparted, something I know, or trying the Windows version.

---

### Post by mikewhatever on 2011-08-06
> **inameiname said:**
> ...

Oh ok. So you can have four primaries, and only one can be called extended. And it is only through that extended one that you can have logical partitions. Does that sound about right? 


Yep.


> 

I found another thread that seems quite informative: [http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741](http://h30434.www3.hp.com/t5/Notebook-Operating-systems-and/Tip-amp-Trick-How-to-partition-H-D-D-in-Preloaded-Windows-7/td-p/143741) . It actually suggest I resize the actual "C://" drive partition and make it an extended, not the HP_Tools ones. So now I'm conflicted on which of the two to choose.

You'll also have to resize C:\, as that's where most of the disk space is. Hp Tools is only relevant because there are four primary partitions already and one has to be deleted.

---

### Post by inameiname on 2011-08-06
> **mikewhatever said:**
> Yep.




You'll also have to resize C:\, as that's where most of the disk space is. Hp Tolls is only relevant because there are four primary partitions already and one has to be deleted.


Yeah, but I would have to resize that C:// drive partition anyway, whether I install Ubuntu on it, or on hp_tools partition. I'm not sure what you mean by "HP Tolls", but the four primary partitions already there and that one has to be deleted is sort of the issue I'm referring about trying to fix so I can add Ubuntu.

---

### Post by Topsiho on 2011-08-06
> **inameiname said:**
> Thanks for the tips. So Windows 7 has a Gparted-like thing to do it? 

I am also curious if you could even delete the hp_tools from within Windows through its partitioning software you mentioned. I'm sure there are safeguards to make that hard to do.

PS, does making swap 10-15GB really make that much of a difference than the usual default amount? I've never tried to change it before in all of my past Ubuntu installations, through a half dozen different versions.

That depends. I never used more than, say, 8 GB for /, having a separate /home partition. But if you have space enough on your hard disk, making a partition of 15 GB (or even more) gives you room enough for installing tons of applications, without any fear that you have not room enough for them. So it depends on the available disk space. I also run Ubuntu in a total of 8 GB on a netbook. But can not install many applications, and have no separate /home partition, on this netbook.

Topsiho

---

### Post by inameiname on 2011-08-06
> **Topsiho said:**
> That depends. I never used more than, say, 8 GB for /, having a separate /home partition. But if you have space enough on your hard disk, making a partition of 15 GB (or even more) gives you room enough for installing tons of applications, without any fear that you have not room enough for them. So it depends on the available disk space. I also run Ubuntu in a total of 8 GB on a netbook. But can not install many applications, and have no separate /home partition, on this netbook.

Topsiho

Oh ok. Well nice to get a better understanding of the benefits for that. This is a new large hard drive so 15GB is nothing, so I'll have to look more into it.

---

### Post by CatKiller on 2011-08-06
> **Topsiho said:**
> Glad to read that Windows did boot. Hope it won't take so long next time. Wouldn't know how to fix that.

Yeah, it was fine. The problem is that you can't possibly be allowed access to their precious until you've signed away your firstborn. So out-of-the-box most of the drive is unallocated but useless because of the partitioning nonsense. When you boot it up for the first time it expands and decrypts those hidden partitions into what becomes the C: drive. Complete waste of time.

> **inameiname said:**
> Thanks for the tips. So Windows 7 has a Gparted-like thing to do it? 

I am also curious if you could even delete the hp_tools from within Windows through its partitioning software you mentioned. I'm sure there are safeguards to make that hard to do. 
It's not as good as gparted, but I'd imagine it's capable of that.
> 

PS, does making swap 10-15GB really make that much of a difference than the usual default amount? I've never tried to change it before in all of my past Ubuntu installations, through a half dozen different versions.

Absolutely none. For general use, more than 2 GB is completely wasted. If you'll be hibernating your computer, you'll want the same size as the amount of RAM you have.
> **inameiname said:**
> "Windows whinges if you use something else to resize the partition"...?

Hmmmm, so Gparted worked, and Windows still booted, ehy? Hmmm, I am now debating on using Gparted, something I know, or trying the Windows version. I understand (now) that it's recommended to use the Windows tools to fiddle with the Windows drives and Linux tools to fiddle with the Linux drives.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> Yeah, it was fine. The problem is that you can't possibly be allowed access to their precious until you've signed away your firstborn. So out-of-the-box most of the drive is unallocated but useless because of the partitioning nonsense. When you boot it up for the first time it expands and decrypts those hidden partitions into what becomes the C: drive. Complete waste of time.

haha, I hear ya. ;)


> **CatKiller said:**
> Absolutely none. For general use, more than 2 GB is completely wasted. If you'll be hibernating your computer, you'll want the same size as the amount of RAM you have.

Oh, interesting. Nice to get two differing opinions here. I never hibernate so that wouldn't be an issue. 

 > **CatKiller said:**
> I understand (now) that it's recommended to use the Windows tools to fiddle with the Windows drives and Linux tools to fiddle with the Linux drives.

Yeah, that makes sense. Though, I really don't see why it'd be any riskier inside Gparted. Didn't seem like you had an issue so who knows.

---

### Post by mikewhatever on 2011-08-06
> **inameiname said:**
> Yeah, but I would have to resize that C:// drive partition anyway, whether I install Ubuntu on it, or on hp_tools partition. I'm not sure what you mean by "HP Tolls", but the four primary partitions already there and that one has to be deleted is sort of the issue I'm referring about trying to fix so I can add Ubuntu.

You can't install Ubuntu on C:\ because Ubuntu needs a Linux file system, and C:\ probably has NTFS - a Windows file system. Same goes for the HP_Tools partition. You are gonna resize C:\ to make space for Ubuntu, and delete HP_Tools to bypass the four primary partitions limit. If HP_Tools was large enough, you could use its space to install Ubuntu, but 108MB is way too small.
Hope that makes sense.:P

---

### Post by inameiname on 2011-08-06
So my current plan is going to be restart into Windows and check out its Gparted-like partitioning thing. Then I'll resize Windows C:// drive and delete hp_tools partition if I can. Then finally, I'll install Ubuntu.

But before that, I am finishing up backing up the 3 out of four partitions currently on the hard drive, the System, the Recovery, and the HP_Tools ones, using a simple 'dd' method. I figure that will be good enough. Also, I think I should (maybe need) to also backup the MBR and the extended partition table. We'll see if all that will enable me to completely restore everything to factoring fresh if I wanted to. I just didn't want to 'dd' the whole several hundred gig hard drive, all four partitions and all.

---

### Post by inameiname on 2011-08-06
> **mikewhatever said:**
> You can't install Ubuntu on C:\ because Ubuntu needs a Linux file system, and C:\ probably has NTFS - a Windows file system. Same goes for the HP_Tools partition. You are gonna resize C:\ to make space for Ubuntu, and delete HP_Tools to bypass the four primary partitions limit. If HP_Tools was large enough, you could use its space to install Ubuntu, but 108MB is way too small.
Hope that makes sense.:P


My bad. I didn't mean install it on C://, but instead of deleting HP_Tools partition number 4, I'd resize C:// partition number 2 AND make it an extended partition, retaining the C:// NTFS partition and adding another Linux partition for Ubuntu. Sorry for the confusion. It just seemed like that was the method the second link I gave above mentioned they did.

---

### Post by CatKiller on 2011-08-06
> **inameiname said:**
> Though, I really don't see why it'd be any riskier inside Gparted. Didn't seem like you had an issue so who knows.
It stops Windows whinging :)

TBH, Windows is so absurdly fragile that it's possible that it might manage to break itself just because you resize a partition.

---

### Post by ramon.rha on 2011-08-06
[LEFT]   	 	 	 	 	> **inameiname said:**
> Thanks for the tips. So Windows 7 has a Gparted-like thing to do it? 

I am also curious if you could even delete the hp_tools from within Windows through its partitioning software you mentioned. I'm sure there are safeguards to make that hard to do.

PS, does making swap 10-15GB really make that much of a difference than the usual default amount? I've never tried to change it before in all of my past Ubuntu installations, through a half dozen different versions.


Don't get confused, there is a comma ',' what  he says is that you have a (/ 10 or 15 GB) and a (swap twice your RAM, 2GB most of the time) and the rest will be for (/ home).


 Surely you have win 7, this OS creates a 100 MB partition so win can work, and yea, is a primary one.
 

 I recommend you delete the RECOVERY and HP TOOLS so you can put / on a 3rd primary partition and a extended partition on a 4th primary partition. So that means that you will have “/home” and “swap” in the extended partition. And I would use Gparted, is my favorite.  
 

 Remember save your data in some DVDs or something like that. I never had data lost doing this kind of thing but is better be sure.


Sorry for my bad english. 

 

 [/LEFT]

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> It stops Windows whinging :)

TBH, Windows is so absurdly fragile that it's possible that it might manage to break itself just because you resize a partition.


Haha, touche. :)

---

### Post by ramon.rha on 2011-08-06
I think is better you delete all the HHDD after all, you already violate the guarantee when you deleted "hp_tools" so a this point does not matter if now you delete all.
 

 In the other and you can avoid the “independet home installation” and tray to install “/” and “/home” in the same partition (the 3 th one)  and the las one (the 4 th one) for the “swap”.

---

### Post by inameiname on 2011-08-06
> **ramon.rha said:**
> Don't get confused, there is a comma ',' what  he says is that you have a (/ 10 or 15 GB) and a (swap twice your RAM, 2GB most of the time) and the rest will be for (/ home).

Right. Thanks for that.
[LEFT] 

 > **ramon.rha said:**
> Surely you have win 7, this OS creates a 100 MB partition so win can work, and yea, is a primary one.

Yep, that's correct.
 

 > **ramon.rha said:**
> I recommend you delete the RECOVERY and HP TOOLS so you can put / on a 3rd primary partition and a extended partition on a 4th primary partition. So that means that you will have “/home” and “swap” in the extended partition. And I would use Gparted, is my favorite.  

True. That would make Ubuntu as having two partitions, just as it normally would require. Now just how much of a difference would it be if I didn't do that, and kept the Recovery one, meaning there'd be only one actual primary partition for Ubuntu?
 

 > **ramon.rha said:**
> Remember save your data in some DVDs or something like that. I never had data lost doing this kind of thing but is better be sure.

Yep. I backed 'dd' copied backups of partitions 1,3,4 via external hard drive. There is nothing to lose in the actual Windows C:// Partition to worry about for me.
[/LEFT]

---

### Post by inameiname on 2011-08-06
> **ramon.rha said:**
> I think is better you delete all the HHDD after all, you already violate the guarantee when you deleted "hp_tools" so a this point does not matter if now you delete all.
 

 In the other and you can avoid the “independet home installation” and tray to install “/” and “/home” in the same partition (the 3 th one)  and the las one (the 4 th one) for the “swap”.

Normally I'd 'dd' the whole bloody thing and just install Ubuntu, but as its not my computer, and I dont' wanna do that just yet since I'd like to be able to restore it back to factory fresh if a hardware issue comes up, I am cool with trying to just install Ubuntu alongside Windows. And as for a warranty, technically with full partition backups, and a lot more various of backups and images for the rest, I should be able to restore the whole thing back to the way it was just fine. Plus, for the person who I am doing this for, they might actually like having the original Windows on there on random occasion. Especially come tax time. 


And for the last bit you mentioned, it sounds like you are also telling me to delete the Recovery partition 3 AND the HP_Tools partition 4 so I can install both of Ubuntu's needed partitions. 

See I was under the impression from the numerous other similar threads that you can make due with just deleting HP_Tools partition 4. Now I'm not so sure.

---

### Post by CatKiller on 2011-08-06
> **inameiname said:**
>  Now I'm not so sure.

You can have as many partitions as you like inside an extended partition. Linux is perfectly fine having all its partitions inside an extended partition. Windows, not so much.

You only need to be able to create an extended partition. The way I did it was to delete a partition and create a new extended partition. The link you provided earlier implied that Windows' Disk Management tool is able to wrap an extended partition around an existing primary partition. Either will work.

---

### Post by westie457 on 2011-08-06
Hi just adding my 2 cents. Echoing previous answers here remove the HP Tools partition, it contains things which can be easily downloaded from HP if you ever need them again. Then do this.> This is what I would do and your choice is to agree or disagree.

1 Boot into Windows and Defrag the C:\ drive at least twice to force Windows into as small a space as possible.

2 Go to disc management and shrink C:\ by as much as Windows allows. Remember that windows is greedy and wants more space than it needs. Leave the free space unallocated for now. 

3 Boot into a Live desktop and run Gparted. In Gparted select the Windows and then move/resize. Shrink this by as much as you want but leaving Windows with enough space. Click okay and Apply. You will now have a lot of free space (unallocated). Again leave this as it is for now.

4 Reboot into Windows. It should immediately tell you your hard drive needs to be checked for errors. Allow this to go ahead and let it finish (better to do this now than later when real problems can occur). And let it finish booting.

5 Restart the computer into the LiveCD and select install. Set a few options relevant to your location and at the where to install screen select something else. You are choosing where to install.

6 In the partitioning window Select the unallocated space choose how large you want his to be; 25000-30000 MB is a good size _25-30GB).Click the first box and select EXT4, then mark the little box to format and then click Use As, select /.

7 Repeat step 6 selecting the remaining space (apart from a size that is equal to the amount of RAM in your computer. This small partition will be your Swap) using this as an EXT4 partition called /home. Remember to mark format.

8 At the bottom of this window is a section for where to install Grub. Make sure Grub goes to the MBR of the drive (the manufacturers name will be here correctly identifying the hard drive.

9 Click Finish and then Apply. The Install goes ahead. If any windows open for where to install Grub you can now accept the defaults.

10 Reboot into your dual-booting computer.

If I have missed anything or someone has other suggestions feel free to join in.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> You can have as many partitions as you like inside an extended partition. Linux is perfectly fine having all its partitions inside an extended partition. Windows, not so much.

You only need to be able to create an extended partition. The way I did it was to delete a partition and create a new extended partition. The link you provided earlier implied that Windows' Disk Management tool is able to wrap an extended partition around an existing primary partition. Either will work.


Oh, either way is fine. Thanks for the info. Though, I've looked into the Windows partitioning thing and the 'extend partition' option is greyed out for it so I guess I cannot for it. But the method below might work. Regardless, sounds like at least one partition currently on my computer will need to be erased. That's fine.

---

### Post by inameiname on 2011-08-06
> **westie457 said:**
> Hi just adding my 2 cents. Echoing previous answers here remove the HP Tools partition, it contains things which can be easily downloaded from HP if you ever need them again. Then do this.

Wow, thanks for that lovely step-by-step guide. It sounds like a very proper way to do it, and I will print it out and let you know how it goes.


I am curious about one thing, though. When do I delete HP_Tools in your guide? I'm asking because I read on several other threads that doing so too early would result in it just being readded back to the partition table, screwing things up. I could be wrong though.

---

### Post by westie457 on 2011-08-06
> **inameiname said:**
> Wow, thanks for that lovely step-by-step guide. It sounds like a very proper way to do it, and I will print it out and let you know how it goes.

Actually there is something missing. That is your /home folder does not need to be really huge. I personally use a NTFS partition shared so Windows can access whatever I really want to keep; music, films, pictures and things.

Enjoy and happy computing.

---

### Post by CatKiller on 2011-08-06
> **inameiname said:**
> 
I am curious about one thing, though. When do I delete HP_Tools in your guide? I'm asking because I read on several other threads that doing so too early would result in it just being readded back to the partition table, screwing things up. I could be wrong though.

It's possible that the stupid decryption step also re-creates this partition. Since Windows is already up-and-running, this shouldn't be a problem.

> **westie457 said:**
> Actually there is something missing. That is your /home folder does not need to be really huge. I personally use a NTFS partition shared so Windows can access whatever I really want to keep; music, films, pictures and things.

Don't be tempted to use NTFS for your /home partition. NTFS can't handle UNIX-style permissions, which will lead to breakage.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> It's possible that the stupid decryption step also re-creates this partition. Since Windows is already up-and-running, this shouldn't be a problem.



Don't be tempted to use NTFS for your /home partition. NTFS can't handle UNIX-style permissions, which will lead to breakage.




Ah. So does that mean I delete the HP_Tools one in what step, in Windows then somewhere?

And yeah, I figured as much. I'm cool with fully separating Ubuntu and Windows as best as I can, and using the appropriate file systems for each.

---

### Post by inameiname on 2011-08-06
So I started that step-by-step guide and after I successfully resized the C:// drive partition inside Windows, I restarted into Ubuntu Live USB, and tried resizing further to my liking inside Gparted, however, I keep getting the following error:

The shrink real resizing AND the grow real filling both fail over and over. I'll attach a screenshot.

---

### Post by CatKiller on 2011-08-06
> **inameiname said:**
> Ah. So does that mean I delete the HP_Tools one in what step, in Windows then somewhere?

Doesn't matter. As soon as you're finished with it. Wherever you happen to be at the time.

---

### Post by westie457 on 2011-08-06
> Quote:
Originally Posted by westie457  
Actually there is something missing. That is your /home folder does not need to be really huge. I personally use a NTFS partition shared so Windows can access whatever I really want to keep; music, films, pictures and things.

@ catkiller
Don't be tempted to use NTFS for your /home partition. NTFS can't handle UNIX-style permissions, which will lead to breakage.

My bad, I did not make it clear. The NTFS-shared partition is for data only and nothing to do with /home which is an EXT4 partition

---

### Post by inameiname on 2011-08-06
> **westie457 said:**
> My bad, I did not make it clear. The NTFS-shared partition is for data only and nothing to do with /home which is an EXT4 partition

Ok, I gotcha now. 



Now I just need to figure out why Gparted isn't letting me resize and then I can continue on installing it.

---

### Post by inameiname on 2011-08-06
> **CatKiller said:**
> Doesn't matter. As soon as you're finished with it. Wherever you happen to be at the time.


I see. Well then I will do it when I boot into Windows after I figure out how to resize my C:// drive partition in Gparted now.

---

### Post by oldfred on 2011-08-06
Gparted/Ubuntu will not mount a NTFS partition that needs chkdsk to prevent further damage. You probably did  not reboot into Window after its resize so it could run its chkdsk. 

Why did you not resize it fully in windows or did you run into the windows issues of unmoveable files at the end of the partition?

---

### Post by inameiname on 2011-08-06
> **oldfred said:**
> Gparted/Ubuntu will not mount a NTFS partition that needs chkdsk to prevent further damage. You probably did  not reboot into Window after its resize so it could run its chkdsk. 

Why did you not resize it fully in windows or did you run into the windows issues of unmoveable files at the end of the partition?


Following the steps in that guide above, I restarted into Windows, and resized as much as it allowed there. Then, following the guide, I rebooted into a Ubuntu Live Session, and tried to further resize. Unfortunately, it didn't work, as it seemed its supposed to according to that guide above. If its a chkdsk thing then that's another story. So i'm currently waiting post resizing in Windows, which went without a hitch, and am now in a Live Ubuntu Session. The plan was to resize further inside Gparted, and then restart into Windows so chkdsk and such would do its thing, as mentioned in that guide.

And as for not resizing it fully inside Windows, it wouldn't allow me to past a certain point for some reason. But that was already known from the guide. Oh, and no, I had issues whatsoever with unmoveable files the end of the partition or anything. Hope that helps.

---

### Post by westie457 on 2011-08-06
> **oldfred said:**
> Gparted/Ubuntu will not mount a NTFS partition that needs chkdsk to prevent further damage. You probably did  not reboot into Window after its resize so it could run its chkdsk. 

Why did you not resize it fully in windows or did you run into the windows issues of unmoveable files at the end of the partition?

+1

It is those unmovable files that cause Windows to throw a hissy fit when the partition is down sized using Gparted causing the CHKDSK to be run on the next Windows start. Windows will be able to handle this if only the end point of the partition is moved using a program not designed to run under Windows. If the start point is moved I have no idea what will happen as I have never tried it.

---

### Post by inameiname on 2011-08-06
> **westie457 said:**
> +1

It is those unmovable files that cause Windows to throw a hissy fit when the partition is down sized using Gparted causing the CHKDSK to be run on the next Windows start. Windows will be able to handle this if only the end point of the partition is moved using a program not designed to run under Windows. If the start point is moved I have no idea what will happen as I have never tried it.


I figured out my issue. I was supposed to restart after resizing from Windows to let it chkdsk it, and then go into Ubuntu, finish the resizing, and then restart, letting it chkdsk it again. Anyway, I'm through that, already deleted the hp_tools partition, and am now ready to restart and install Ubuntu.

---

### Post by inameiname on 2011-08-06
It seems to have installed correctly. I just ran the Ubuntu Installation normally, checking the 'run alongside Windows' option instead of customizing it, and it installed everything between the Windows partition and the Recovery one just as I wanted. Seems to be okay so far. As such, I will mark this thread as solved. Thanks to all who helped me out on what was quite a long and tedious thing to do on a Saturday. :P

And so far, the only issue I have is not having desktop effects. I know that's more a graphics/compiz issue so I'll stop with that on this thread.

---

### Post by inameiname on 2011-08-06
Okay, maybe I shouldn't have done the default settings in the Ubuntu install (which I thought would be the smartest and simplest ones) as now I can't even get into Windows at all. its not showing up in the grub default boot loader or anything. 

It does all look good in Gparted as far as the names of the drives, where they are, and their size and all that, including the C://, but nothing will load. I'm guessing its a grub thing, as it didn't update the right away so as to include Windows. 

Anybody know how I can change this?


UPDATE:

Nevermind. All I had to do was a 'sudo update-grub'/' sudo update-grub2' and it found the Windows Loader. Good enough. Now I need to find a prettier boot manager.

---

### Post by mikewhatever on 2011-08-07
> **inameiname said:**
> ...


UPDATE:

Nevermind. All I had to do was a 'sudo update-grub'/' sudo update-grub2' and it found the Windows Loader. Good enough. Now I need to find a prettier boot manager.

EasyBCD?
[https://secure.wikimedia.org/wikipedia/en/wiki/EasyBCD](https://secure.wikimedia.org/wikipedia/en/wiki/EasyBCD)

---

### Post by inameiname on 2011-08-07
> **mikewhatever said:**
> EasyBCD?
[https://secure.wikimedia.org/wikipedia/en/wiki/EasyBCD](https://secure.wikimedia.org/wikipedia/en/wiki/EasyBCD)


Thanks for the link. I didn't know about it. Although, it sounds like its just a GUI way to tweak certain grub things. I had just thought there were prettier-looking grub2 menus you can get for dual-booting. I have limited experience with this to know if that's true or not.


UPDATE:

Burg! This is what I was talking about. A way to pretty up grub2 or something. I knew I ran across articles about programs that do that, but couldn't remember the names. [http://www.techpraveen.com/2011/03/how-to-customize-your-grub2-boot-loader-on-ubuntu.html](http://www.techpraveen.com/2011/03/how-to-customize-your-grub2-boot-loader-on-ubuntu.html)

---

