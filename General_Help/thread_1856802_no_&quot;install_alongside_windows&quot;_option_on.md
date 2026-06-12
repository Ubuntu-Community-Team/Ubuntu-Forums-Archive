---
title: "no &quot;install alongside windows&quot; option on disk"
date: 2011-10-09
forum: General Help
---

### Post by cllewis91592 on 2011-10-09
well here's the story.
first i had 11.04 dual booted on my computer with windows 7. i was searching the software center and saw the Edubuntu desktop app, i installed it, didn't like it, and i tried to remove it. but when i did something went wrong and the boot splash image was all messed up(most likely my fault). also the software center was gone. so i un-installed Ubuntu by using the recovery console in windows. now i want to re-install Ubuntu from a disk but it wont show a dual boot option. anything i did wrong? 

p.s when i removed Ubuntu i used 
```
bootrec.exe /fixmbr
bootrec.exe /fixboot
```then i formated the partition it was on and expanded windows partition. if that helps.

---

### Post by cllewis91592 on 2011-10-09
also i don't want to use the partition manager on the Ubuntu disk because i have had some very bad experiences with it. A.K.A complete and total hard drive corruption(again probably my fault)

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> also i don't want to use the partition manager on the Ubuntu disk because i have had some very bad experiences with it. A.K.A complete and total hard drive corruption(again probably my fault)

If (since) you had problems, it was your fault.  It wasn't the computer's fault.  It'll work if use according to the instructions.  The partition manager won't cause any corruption.

You don't have to partition the drive if it's already partitioned.  Just boot to the Ubuntu Live disk and follow the steps for installing Ubuntu on the partition you already have allocated for it.

I don't know of words that will say along side Windows or anything else that is on other partitions.  It's just install Ubuntu on the partition you specify.  When you boot, you'll see options to select which OS to boot to if you have other OS' on the disk.  In this case, after you install Ubuntu, when you boot you'll be able to select Windows or Ubuntu at boot time.

The only partition(s) that will be affected is the partition(s) that you select during the setup process for Ubuntu.  I suggest that you select two partitions.  One for the Ubuntu OS and one for Swap (at least equal in size to your total memory).  The swap partition isn't a requirement but will improve performance on most systems.

What you use for partitioning your disk is totally up to you.  I find gparted to be the absolute easiest and most reliable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> If (since) you had problems, it was your fault.  It wasn't the computer's fault.  It'll work if use according to the instructions.  The partition manager won't cause any corruption.

You don't have to partition the drive if it's already partitioned.  Just boot to the Ubuntu Live disk and follow the steps for installing Ubuntu on the partition you already have allocated for it.

I don't know of words that will say along side Windows or anything else that is on other partitions.  It's just install Ubuntu on the partition you specify.  When you boot, you'll see options to select which OS to boot to if you have other OS' on the disk.  In this case, after you install Ubuntu, when you boot you'll be able to select Windows or Ubuntu at boot time.

The only partition(s) that will be affected is the partition(s) that you select during the setup process for Ubuntu.  I suggest that you select two partitions.  One for the Ubuntu OS and one for Swap (at least equal in size to your total memory).  The swap partition isn't a requirement but will improve performance on most systems.

What you use for partitioning your disk is totally up to you.  I find gparted to be the absolute easiest and most reliable.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
i dont have my drive partitioned already. i had used the "install along side windows" option on the boot disk. but now it wont show up when i boot the disk. i have no experience with gparted or any other partition manager(including the one on the install disk) so i don't feel comfortable enough using it. i'm sure its very easy, but i just don't feel confident enough using them.
sorry for my lack of confidence. :(

---

### Post by mrjoeyman on 2011-10-09
Is your bios still set to boot from the cd? If not try that. I don't quite understand how you removed Ubunut. Can you explain that a little better? It sounds like you just deleted the partition it was on? And then tried to re-allocate that partition space back to your windows install?

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> i dont have my drive partitioned already. i had used the "install along side windows" option on the boot disk. but now it wont show up when i boot the disk. i have no experience with gparted or any other partition manager(including the one on the install disk) so i don't feel comfortable enough using it. i'm sure its very easy, but i just don't feel confident enough using them.
sorry for my lack of confidence. :(

If you don't have Ubuntu installed on it's own partition, you're looking for more trouble in the future.  There's a chance you don't actually have ubuntu installed.  You might be running wubi, which is basically a way to sample Ubuntu by running it as a Windows application from Windows.

That probably explains why you can't see the USB installation any more.

I recommend that you consider creating partitions on your hard drive.  Make a partition for Windows and a partition for Ubuntu.  While you're at it, make a small partition of around 8 gigs for Linux swap (to enhance performance).  Then borrow your friend's external CD drive and perform a real Ubuntu installation on it's own partition.

If you're running Wubi (which I'm sure you are) and Windows crash, you might lose all the work you've done in Linux.  If you install Ubuntu on it's own partition what you do with Windows wouldn't effect Ubuntu.

By the way, this might explain what happened to your other installation when you removed/reinstalled Windows XP.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cllewis91592 on 2011-10-09
> **mrjoeyman said:**
> Is your bios still set to boot from the cd? If not try that. I don't quite understand how you removed Ubunut. Can you explain that a little better? It sounds like you just deleted the partition it was on? And then tried to re-allocate that partition space back to your windows install?
when i messed up ubuntu i booted into the recovery console of windows 7 by pressing f8 when it was booting. 

then i ran the bootrec /fixmbr and bootrec/ fixboot command in the console. then i used disk management in windows to delete the partition and then stretched out the windows partition. 

now i want to re-install Ubuntu 11.04 back on the same drive that has not been re-partitioned, but i don't feel confident enough using the partition manager built in to the install disk. also i don't know how much is safe to partition so thats another reason.

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> If you don't have Ubuntu installed on it's own partition, you're looking for more trouble in the future.  There's a chance you don't actually have ubuntu installed.  You might be running wubi, which is basically a way to sample Ubuntu by running it as a Windows application from Windows.

That probably explains why you can't see the USB installation any more.

I recommend that you consider creating partitions on your hard drive.  Make a partition for Windows and a partition for Ubuntu.  While you're at it, make a small partition of around 8 gigs for Linux swap (to enhance performance).  Then borrow your friend's external CD drive and perform a real Ubuntu installation on it's own partition.

If you're running Wubi (which I'm sure you are) and Windows crash, you might lose all the work you've done in Linux.  If you install Ubuntu on it's own partition what you do with Windows wouldn't effect Ubuntu.

By the way, this might explain what happened to your other installation when you removed/reinstalled Windows XP.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
ok firstly i already said i dont have ubuntu installed, i removed it from the drive and expanded the windows partition to fill in the space. 

secondly i am not using wubi, i am using a live cd and trying to install ubuntu back on my hard drive.

thirdly i am not using windows xp, i am running windows 7.

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> when i messed up ubuntu i booted into the recovery console of windows 7 by pressing f8 when it was booting. 

then i ran the bootrec /fixmbr and bootrec/ fixboot command in the console. then i used disk management in windows to delete the partition and then stretched out the windows partition. 

now i want to re-install Ubuntu 11.04 back on the same drive that has not been re-partitioned, but i don't feel confident enough using the partition manager built in to the install disk. also i don't know how much is safe to partition so thats another reason.

I might be missing something.  But if you have a drive and want to install Ubuntu and are afraid to give it space (a partition for the installation), then there's something wrong with that scenario.  You'll have to be willing to give the OS space for the installation to install it.  Install it in it's own space (partition) and you won't have any problems.

The process is easy using the install disk.  It'll ask you were to install it.  Browse the install menus to go to the space or partition and install it there.  You have to do this by booting to the live CD, not by running the live CD from Windows which will give you an option to perform an installation into Windows (Wubi) which will be a new source of problems... depending on the stability of Windows.

You can use any program to create your partitions.  But you have to have the partition.  You can boot into the live CD and run gparted.  I believe that's the best partitioning manager around at this time... when you take ease and robust into consideration.  But again, it doesn't matter which program you use for partitioning your drive.  Use whatever you're most comfortable with.  But if you want the OS to work properly you'll have to give it it's own space.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> I might be missing something.  But if you have a drive and want to install Ubuntu and are afraid to give it space (a partition for the installation), then there's something wrong with that scenario.  You'll have to be willing to give the OS space for the installation to install it.  Install it in it's own space (partition) and you won't have any problems.

The process is easy using the install disk.  It'll ask you were to install it.  Browse the install menus to go to the space or partition and install it there.  You have to do this by booting to the live CD, not by running the live CD from Windows which will give you an option to perform an installation into Windows (Wubi) which will be a new source of problems... depending on the stability of Windows.

You can use any program to create your partitions.  But you have to have the partition.  You can boot into the live CD and run gparted.  I believe that's the best partitioning manager around at this time... when you take ease and robust into consideration.  But again, it doesn't matter which program you use for partitioning your drive.  Use whatever you're most comfortable with.  But if you want the OS to work properly you'll have to give it it's own space.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
i understand i need a new partition to install it on, i just dont know how much drive space to partition off because the last time i did i crapped out my hard drive and had to re-install windows 7 back and lost everything.  on the install disk before it had an option to dual boot windows 7 and ubuntu and it automatically, and safely partition the hard drive.

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> i understand i need a new partition to install it on, i just dont know how much drive space to partition off because the last time i did i crapped out my hard drive and had to re-install windows 7 back and lost everything.  on the install disk before it had an option to dual boot windows 7 and ubuntu and it automatically, and safely partition the hard drive.

I don't think you ever had Ubuntu installed on a partition.  You appear to have been running Wubi.  This is running Ubuntu under Windows as a Windows application.  You had a glitch.  Instead of fixing Windows (which may or may not have been fixable) you reinstalled Windows, which removed all your Windows applications including Wubi, which was Ubuntu running as a Windows application.

If your biggest problem is know how big, I'll suggest that you consider creating a 50 gig partition for Ubuntu and 8 gigs for Linux Swap (optional to improve performance).

If you do it that way you won't run into a problem of having Ubuntu mess-up Windows.  Because it'll be on it's own partition.  Windows won't mess-up Ubuntu either, because Windows would be on a separate partition.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> I don't think you ever had Ubuntu installed on a partition.  You appear to have been running Wubi.  This is running Ubuntu under Windows as a Windows application.  You had a glitch.  Instead of fixing Windows (which may or may not have been fixable) you reinstalled Windows, which removed all your Windows applications including Wubi, which was Ubuntu running as a Windows application.

If your biggest problem is know how big, I'll suggest that you consider creating a 50 gig partition for Ubuntu and 8 gigs for Linux Swap (optional to improve performance).

If you do it that way you won't run into a problem of having Ubuntu mess-up Windows.  Because it'll be on it's own partition.  Windows won't mess-up Ubuntu either, because Windows would be on a separate partition.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
i am 100% sure i was **NOT **using wubi when i installed ubuntu the first time. on the install disk on the 3rd or 4th window when it asks what you want to do to install ubuntu it use to have an option that said "install along side windows and choose between them on boot." now that option is gone form the installer.

---

### Post by cllewis91592 on 2011-10-09
this is what it shows me when i run the installer
[ATTACH]203904[/ATTACH]

and this is what it should show
[ATTACH]203905[/ATTACH]


any reason why the third option wont show up?

---

### Post by mrjoeyman on 2011-10-09
All looks fine bro. Here is a link that if you follow, you will be on easy street. I did exactly this.


[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)

(Maybe someone will be able to tell you why you don't get the third option, but after you get it, follow this install guide)

Update: you can still follow the guide with what it offers you. It will probably give you that option after you get the first part of the tutorial completed. Of course all of this assumes that you are able to boot into your windows 7 installation still.

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> i am 100% sure i was **NOT **using wubi when i installed ubuntu the first time. on the install disk on the 3rd or 4th window when it asks what you want to do to install ubuntu it use to have an option that said "install along side windows and choose between them on boot." now that option is gone form the installer.

I just booted up a Windows machine and loaded the CD.  The autorun will take you to the screen you appear to be trying to find.  The wording is:


[LIST=1]
[*]Demo and full installation
[*]Install inside Windows
[*]Learn More
[/LIST]
By the wording of most of your messages and the title of your thread I'm almost certain as I mentioned from my first reply.  I didn't recall the exact wording, but mentioned I had never hear of an "install alongside windows".  But as you see there is an "install inside windows".  This is apparently what you had saw and did.  It appears that you installed "Inside Windows" and thought you were installing "Alongside Windows".

There is no such thing as "Alongside Windows".  There is a dual boot option that allows you to pick with OS to boot to.  But this involves installing Ubuntu on it's own partition as a separate OS.

You won't get that option (inside windows) if you boot directly to the CD.  You can only get that option if you run the CD while Windows is running.

Based on everything you say (except for the words that you didn't install Wubi) you installed and was running Wubi, not Ubuntu.

Please borrow your friends cd drive and verify what I'm saying.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> I just booted up a Windows machine and loaded the CD.  The autorun will take you to the screen you appear to be trying to find.  The wording is:


[LIST=1]
[*]Demo and full installation
[*]Install inside Windows
[*]Learn More
[/LIST]
By the wording of most of your messages and the title of your thread I'm almost certain as I mentioned from my first reply.  I didn't recall the exact wording, but mentioned I had never hear of an "install alongside windows".  But as you see there is an "install inside windows".  This is apparently what you had saw and did.  It appears that you installed "Inside Windows" and thought you were installing "Alongside Windows".

There is no such thing as "Alongside Windows".  There is a dual boot option that allows you to pick with OS to boot to.  But this involves installing Ubuntu on it's own partition as a separate OS.

You won't get that option (inside windows) if you boot directly to the CD.  You can only get that option if you run the CD while Windows is running.

Based on everything you say (except for the words that you didn't install Wubi) you installed and was running Wubi, not Ubuntu.

Please borrow your friends cd drive and verify what I'm saying.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
i just posted a picture of what i am talking about. i did not run the disk inside windows. i booted from the disk and was trying to install ubuntu on my drive. as im typing this i am in live mode of the cd. it is in my cd drive and running **OUTSIDE **windows. i am **NOT** using wubi.

---

### Post by apollothethird on 2011-10-09
> **cllewis91592 said:**
> this is what it shows me when i run the installer
[ATTACH]203904[/ATTACH]

and this is what it should show
[ATTACH]203905[/ATTACH]


any reason why the third option wont show up?

> **mrjoeyman said:**
> All looks fine bro. Here is a link that if you follow, you will be on easy street. I did exactly this.


[http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)

(Maybe someone will be able to tell you why you don't get the third option, but after you get it, follow this install guide)

Update: you can still follow the guide with what it offers you. It will  probably give you that option after you get the first part of the  tutorial completed. Of course all of this assumes that you are able to  boot into your windows 7 installation still.

Actually I hadn't went past the first screen (which maybe the OP didn't either).  I guess the "along side" option is what I was describing along... putting Ubuntu on it's own partition for a multiple choice boot.

So, I'll restate my suggestion for the OP to create a partition and perform a full install on that partition.  It'll therefore be along side all the other partitions which will be untouched (as I explained in all my messages).

Thanks for the clarifications of where the wording happens to be.  The user will have to go through the install process to get there.  When he gets there he'll be able to select the partition he has created for Ubuntu, or create one using Ubuntu's advanced features for installing the OS.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by mrjoeyman on 2011-10-09
Most likey Ubuntu detects that there is not an appropriate partition to list that option (install alongside). It quite likely is the result of what was done during the "uninstall" process that was chosen. All should be ok though if the link I submitted is followed to the letter. :P

---

### Post by westie457 on 2011-10-09
Hi, a change of tactics is in order here IMO. Follow these steps carefully and do not try to rush anything, otherwise things will break very catastrophically.

Boot into Windows and open up the computer MMC and go to 'storage' to see the partitions currently on your hard drive. If you have only the one partition right=click on it and select 'shrink this partition', make it as small as Windows will allow. Leave the newly created space as unformatted.

Reboot into a LiveCD in 'TRY' mode and start Gparted.
In the Gparted window select the Windows partition - right-click and select 'resize/move -  and shrink it some more (as much as you want or need to), click on the 'Resize/Move' box and click on 'Apply'. [COLOR="Red"]Wait patiently for this to finish[/COLOR]. Again leave this space unformatted. Now reboot again into Windows and allow the CHKDSK to run and confirm that Windows is okay.

Once again reboot using the LiveCD and select 'INSTALL' at the where do you want to install screen select 'Something else'. In the partitioning window select the unformatted space set to use all but about 2GIB.
In the next box choose EXT4 and in the small box underneath put a check to format the space. In the next box 'USE AS' select '/' root. Click okay.

For the small space that is left all you need to do is select the 'USE AS' box and choose 'Swap'. Agree to everything and the installation will go ahead. Follow any prompts that appear and in a while you should have a fully functioning dual-boot computer.


There are some other options that can be done to the partitions once you have got things running.

---

### Post by cllewis91592 on 2011-10-09
> **apollothethird said:**
> Actually I hadn't went past the first screen (which maybe the OP didn't either).  I guess the "along side" option is what I was describing along... putting Ubuntu on it's own partition for a multiple choice boot.

So, I'll restate my suggestion for the OP to create a partition and perform a full install on that partition.  It'll therefore be along side all the other partitions which will be untouched (as I explained in all my messages).

Thanks for the clarifications of where the wording happens to be.  The user will have to go through the install process to get there.  When he gets there he'll be able to select the partition he has created for Ubuntu, or create one using Ubuntu's advanced features for installing the OS.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")
ok let me try this again. i am fully aware that i need to create a new partition on my hard drive to install ubuntu. i know i need to do a full install of ubuntu on the drive to get the full effect of ubuntu. **I HAVE INSTALLED UBUNTU BEFORE, AND HAVE USED IT FOR SOME TIME NOW. **but what i am trying to say (and have been saying for the past 10 posts!) is that i do not feel comfortable using a partition manager such as gparted, because the last time i used it i lost everything on my hard drive. what i am trying to figure out is **WHY THE THIRD OPTION FROM THE PICTURE IS NOT SHOWING UP! **right now im not concerned with making a new partition or anything like that **AT THE MOMENT**. i will, however, worry about that matter later.

recap: [B]ALL I AM TRYING TO FIGURE OUT IS WHY THE THIRD OPTION IS NOT SHOWING UP ON THE INSTALLER, AND IF THERE IS A WAY OF GETTING IT BACK!
NOT WORRIED ABOUT CREATING A PARTITION AT THE MOMENT! 
[/B]

---

### Post by mrjoeyman on 2011-10-09
Well I don't want you to burst a vein or anything, but as stated before, Ubuntu may detect that you NEED to do what Westie just suggested, and create the partition that Ubuntu will recongnize to be able to GIVE you BACK that option my friend. 

Take a breath! :lolflag:

---

### Post by apollothethird on 2011-10-09
Please Delete... duplicated post.

---

### Post by mrjoeyman on 2011-10-09
Well I see that there have been no posts for the last hour or so. Sadly people may not try to help if you use "yell text".


You sound as if you may have tried searching this or any forums for this similar problem, but I found a few just in case you didn't have the chance.

[http://ubuntuforums.org/showthread.php?t=1646489&page=2](http://ubuntuforums.org/showthread.php?t=1646489&page=2)
[http://ubuntuforums.org/showthread.php?t=1674726](http://ubuntuforums.org/showthread.php?t=1674726)

Good luck.

---

### Post by cllewis91592 on 2011-10-09
well i decided to throw caution to the wind and used the windows partition manager. i just shrank it down and will install later(ive got other matters to attend to now) i will let you know if it worked later. for now i will mark this post as solved.

sorry for getting upset. :(

---

### Post by mrjoeyman on 2011-10-09
Hey all good ;)  If you successfully got the shrink done with windows then you should be able to follow the guide I sent. I mentioned it because of all the installs I have done of Linux distributions, this guide set me up with the most intuitive and fast installs (and fastest working systems) I have ever done. Again, good luck and keep us informed!

---

### Post by cllewis91592 on 2011-10-09
well i got it installed and tweaked to my liking. took 3 times to get the install to work though. not really sure why, anyway everything worked out so i guess they can erase this thread or move it somewhere. 
:KS

---

### Post by vasa1 on 2011-10-09
> **cllewis91592 said:**
> this is what it shows me when i run the installer
[ATTACH]203904[/ATTACH]

and this is what it should show
[ATTACH]203905[/ATTACH]


any reason why the third option wont show up?

Bit late but **possible** reasons why the "install alongside Windows" option doesn't occur is if there's no "unallocated space" or the disk already has 4 primary partitions. Experts please confirm!

---

### Post by mrjoeyman on 2011-10-10
> **cllewis91592 said:**
> well i got it installed and tweaked to my liking. took 3 times to get the install to work though. not really sure why, anyway everything worked out so i guess they can erase this thread or move it somewhere. 
:KS

Excellent. Enjoy my friend.

---

### Post by HDVH on 2011-11-23
> **westie457 said:**
> 

If you have only the one partition right=click on it and select 'shrink this partition', make it as small as Windows will allow. Leave the newly created space as unformatted.


Hi all, am a newbie in search of help dual-booting ubuntu (first time ever) with windows 7 - I've been reading up and this thread seems to be the most helpful, with the links and advice.  Problem is, I seem to have 4 partitions on my laptop at the mo - 

System, 
C, 
Recovery (D),
HP_Tools

And the advice I've seen so far (eg the quote above) mentions if you have one partition, or even three and some unused space... I don't seem to have any free space to work with??

Any help much appreciated, please don't hesitate to make it foolproof/mega simple as I'm new to ubuntu and also to anything to do with disk partitions!

Thanks in advance! 

H

---

### Post by mrjoeyman on 2011-11-23
Check this site: 

[http://windows7themes.net/how-to-shrink-a-partition-in-windows-7.html](http://windows7themes.net/how-to-shrink-a-partition-in-windows-7.html)

It will show you how to get to disk manager and shrink your partition. As for which partition to shrink, just choose the largest partition that is designated "NTFS". I recommend that you let windows decide how much to shrink it, since it will keep you from shrinking it to the point that will hinder your existing installation. It will give you a readout of how much it is going to shrink the partition before it actually does it. If you are going to have at least 15-20 gigs of space left over after the shrink, then all is good. You may have less or you may have much more. If you don't want to shrink it down to the size that windows recommends, THEN you can manually choose to shrink it to the size you would like. Its ok to manually set it smaller, but let windows handle the maximum. After that, you can look back up to a previous post for the link to how to proceed with the install of Linux. Cheers!

By the way, "Shrink it smaller" up above is referring to the space that will be unallocated after the shrink.

---

### Post by Quackers on 2011-11-23
If you already have 4 primary partitions on your disc you will need to delete one first. You can then shrink your Windows C: drive with Windows Disk Management (after defragmenting it first). This will create the space necessary for a new extended partition, which can hold as many LOGICAL partitions as you wish.
Other people in your position have deleted the HP TOOLS partition as these tools can be downloaded separately from the HP website, if needed - though you probably won't ever need them.

---

### Post by mrjoeyman on 2011-11-23
> **Quackers said:**
> If you already have 4 primary partitions on your disc you will need to delete one first. You can then shrink your Windows C: drive with Windows Disk Management (after defragmenting it first). This will create the space necessary for a new extended partition, which can hold as many LOGICAL partitions as you wish.
Other people in your position have deleted the HP TOOLS partition as these tools can be downloaded separately from the HP website, if needed - though you probably won't ever need them.

Yes this is true because you are only allowed 4 primary partitions on a disk. But I think you could work around this without deleting anything. Just make the leftover (unallocated) space after the shrink, an extended partition and then create, either one logical partition to install Linux on, or if you want to have a custom partition scheme, make them all logical. Except of course for the swap. :)

If it gives you errors, then you will have to delete a partition and start over. And yes good advice on the defrag. :)

---

### Post by Quackers on 2011-11-23
That won't work I'm afraid. If you shrink the C: drive and leave unallocated space you will still have 4 primary partitions, which as you have said, is the maximum possible on a MBR partitioned disc.
If you try to create an extended partition (which is a different type of Primary partition) you will be attempting to create a 5th partition. At best it will fail. At worst Windows will change its partition type to dynamic disks. This is not good news if you want to install a different operating system.

---

### Post by mrjoeyman on 2011-11-23
Thanks Quackers! Very good to know. There you go OP, let us know how it works out.

---

### Post by HDVH on 2011-11-26
OK so can I relistically just delete the HP tools bit then? Planning on using Ubuntu just don't wanna completely get rid of Windows... but HP Tools? I don't even know what it is!  Just checking it won't upset the day to day running of my comp if i judt click delete? Thanks guys!

---

### Post by mrjoeyman on 2011-11-26
Nope shouldn't be a problem, but it might not be large enough of a partition. How big is it?

---

### Post by Mark Phelps on 2011-11-26
> **HDVH said:**
> OK so can I relistically just delete the HP tools bit then?
NO -- that partition is way too small for installing Ubuntu.

Instead, you need to shrink the Win7 OS partition -- which you do ONLY from the Win7 Disk Management utility.  Do not use GParted or the Ubuntu installer to do this shrinkage.

If you're then left with a block of unallocated space -- that continues to the end of the drive -- you are OK to create an Extended partition in that space.

But, BEFORE you do that, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You will need this to restore Win7 boot capability if anything goes wrong during the subsequent dual-boot Ubuntu install.

---

### Post by HDVH on 2011-11-30
OK burning a system repair disc (presume that's what you meant!) as we speak.  

I'd already shrunk the 'C' partition before i realised (thanks to you guys) that I couldn't have more than 4.   Sooo, I currently have:

System:      199 MB
C:           124 GB
Unallocated: 91.35 GB
Recovery:    17.24 GB
HP tools:    99 MB

So does this look OK and could someone please walk me through 'creating an extended partition' in the space I've got unallocated!

Thanks everyone for your help so far!

H :)

---

