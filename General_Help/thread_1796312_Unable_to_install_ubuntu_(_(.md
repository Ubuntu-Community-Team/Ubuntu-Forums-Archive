---
title: "Unable to install ubuntu :( :("
date: 2011-07-03
forum: General Help
---

### Post by sravan008 on 2011-07-03
HI i'm newbie in ubuntu world :).i'm unable to install ubuntu :( , the problem is, when i got the partation window in the time installtion i choosed the custom partation , but i couldn't get my drive**(i formated one drive in my windows esply for ubuntu)**there , it shows me some other drives instead of that :( :( 
thats why i couldnot able to install the ubuntu:(

can any one solve this problem pleaseeeeeeee... 

NOTE:I got single partation drive with my laptop thats why i converted my whole hard disk drive to dynamic.:(

---

### Post by sravan008 on 2011-07-03
Guys if you want more info abt this problem please reply me i will try to replay in more detail , but final thing is i wanted to shift from old windows to nEw Linux world :)

---

### Post by grahammechanical on 2011-07-03
When you tried to install did the partition manager load? Did you see any partitions? In Windows hard discs are assigned a drive letter (such as C :. A partition would also be assigned a drive letter (such as d : But in Linux/Ubuntu disc drives and partitions are called partitions.

So, a hard drive would be called sda (sata drive a). The first partition on that drive would be called sda1 (sata drive a partition 1). The second partition would be listed as sda2 and so one. If you install a second hard disc, then it would show up as sdb.

You need to work out what partitions match up with your Windows Drive letters and which partition is the one you want to install Ubuntu in. Be careful not to install Ubuntu in one of the Windows partitions as you will loose your Windows operating system.

If you can load a Ubuntu Live CD/USB then do so and use Disk Utility to show you the partitions on your hard disc. Note the sizes and the labels and the type of format.

I hope that this helps. 

Regards.

---

### Post by apollothethird on 2011-07-03
> **sravan008 said:**
> HI i'm newbie in ubuntu world :).i'm unable to install ubuntu :( , the problem is, when i got the partation window in the time installtion i choosed the custom partation , but i couldn't get my drive**(i formated one drive in my windows esply for ubuntu)**there , it shows me some other drives instead of that :( :( 
thats why i couldnot able to install the ubuntu:(

can any one solve this problem pleaseeeeeeee... 

NOTE:I got single partation drive with my laptop thats why i converted my whole hard disk drive to dynamic.:(


Boot to the Ubuntu Live CD.  Click on Try Ubuntu.  Run GParted (found under the System menu).

Use GParted to resize your large partition (if you only have one).  Or manipulate the drive anyway you want.  Create a partition for Ubuntu.  My recommendation is to select type ext4 for that partition.  You can also name it Ubuntu (or something similar) to remind you where it is during the install.

For convenience and performance efficiency you migh also create a linux-swap partition (at least equal to the size of the amount of ram you have installed).

Now close Gparted and run the “Install Ubuntu” icon on the desktop.  Select the manual option for the installation.  Select the ext4 partition for the install and “/” as the install point.

Follow the prompts and you shouldn't have any problems.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by sravan008 on 2011-07-04
@abv all :

guys thanks for the reply :) , there i can see some partations like sd1 and sd2 but all those partations contains some data :( i deleted one partation in windows for linux OS but i couldnt get that unallocated space :( , can you tell how to install ubuntu in that unallocated space 


NOTE: I converted my hard disk into dynamic partation

---

### Post by e79 on 2011-07-04
> **sravan008 said:**
> Guys if you want more info abt this problem please reply me i will try to replay in more detail , _**but final thing is i wanted to shift from old windows to nEw Linux world**_ :)

Carefully backup all your data on your Windows installation, then boot the Ubuntu CD and select 'Use and Erase the whole drive'.

Simple ;)

---

### Post by blackbird34 on 2011-07-04
if you use gparted on the cd you should be able to convert the unallocated space into an extra partition UNLESS you have four partitions already. Then things get complicated.

---

### Post by apollothethird on 2011-07-04
> **sravan008 said:**
> @abv all :

guys thanks for the reply :) , there i can see some partations like sd1 and sd2 but all those partations contains some data :( i deleted one partation in windows for linux OS but i couldnt get that unallocated space :( , can you tell how to install ubuntu in that unallocated space 


NOTE: I converted my hard disk into dynamic partation

There are a number of ways of dealing with the unallocated space.  You can select it from GParted and partition it to ext4.  Then exit GParted.  Then run the Install to Drive option and select that partition for your installation drive.

Others will give you other methods.  Again, there are lots of methods.  The one I described appears to be about the simplest from my perspective.  But a different way might be easier for the next person to describe.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by sravan008 on 2011-07-04
@e79 thanks for the suggestion but it will not help me :)


James im going through the first method , i will get bak to u in very soon. and thanks for the qucik replies

---

### Post by sravan008 on 2011-07-04
@james :


I tried alot but its not working dude.I got some partations in the time of installtion like /dev/sd1 sd2 etc,and also get  **unusable** space but i could able to use that. :(and another problem is i deleted a drive in windows wich contains 40gb but here it shows 200gb unusable space:).Didnt understand what i have to do now:(. Again i'm mentioning i converted whole drive into dynamic drive in windows for partioning my dive


help me to get in this new world guys

---

### Post by wildmanne39 on 2011-07-04
> **sravan008 said:**
> @james :


I tried alot but its not working dude.I got some partations in the time of installtion like /dev/sd1 sd2 etc,and also get  **unusable** space but i could able to use that. :(and another problem is i deleted a drive in windows wich contains 40gb but here it shows 200gb unusable space:).Didnt understand what i have to do now:(. Again i'm mentioning i converted whole drive into dynamic drive in windows for partioning my dive


help me to get in this new world guys
Hi, that is a problem, dynamic drives cause issues. Do search on the forums and you may find some information on dynamic drives, I know there is instructions for converting dynamic to regular drive but I am not sure where and I remember reading that it is a risky operation.

---

### Post by apollothethird on 2011-07-05
> **sravan008 said:**
> @james :


I tried alot but its not working dude.I got some partations in the time of installtion like /dev/sd1 sd2 etc,and also get  **unusable** space but i could able to use that. :(and another problem is i deleted a drive in windows wich contains 40gb but here it shows 200gb unusable space:).Didnt understand what i have to do now:(. Again i'm mentioning i converted whole drive into dynamic drive in windows for partioning my dive


help me to get in this new world guys

The easiest thing you can do if you don't have anything significant on the disk is to backup whatever you want, then use GParted to remove all those partitions, then repartition it with GParted.

If you have data on the drive and want to try to keep it I'll have another suggestion a bit more complex.

-- L. James

-- 
L. D. James
[EMAIL="ljames@apollo3.com"]ljames@apollo3.com[/EMAIL]
[www.apollo3.com/~ljames]("http://www.apollo3.com/%7Eljames")

---

### Post by wildmanne39 on 2011-07-05
Hi, have a look at this thread scroll down the page to where oldfred is talking about dynamic disks and it gives links and information for converting them to regular disks. Please if you can make a back  up before you start.
[http://ubuntuforums.org/showthread.php?t=1779529&highlight=convert+dynamic+disk](http://ubuntuforums.org/showthread.php?t=1779529&highlight=convert+dynamic+disk)

---

### Post by sravan008 on 2011-07-05
i will take the backup but i think windows OS will gone if i do like that , thats why i'm searching for other options guys :o

---

### Post by wildmanne39 on 2011-07-05
> **sravan008 said:**
> i will take the backup but i think windows OS will gone if i do like that , thats why i'm searching for other options guys :o
Hi according to the information on the link I gave you you are suppose to be able to do it without getting rid of windows backing up your drive is always suggested though.

---

### Post by sravan008 on 2011-07-05
sure i will go through tat and i will cum bak here with update:)

---

### Post by sravan008 on 2011-07-11
thank you wildmanne39 :)


its working fine now :)

---

