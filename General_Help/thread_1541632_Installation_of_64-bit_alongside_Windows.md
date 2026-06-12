---
title: "Installation of 64-bit alongside Windows"
date: 2010-07-29
forum: General Help
---

### Post by Veren on 2010-07-29
Hello, 
first of all I am a casual PC user so I apologise if this is a stupid question.
Ok, here it goes..
I was using Ubuntu 10.04 32-bit alongside Windows, choosing between them each startup. It was easy to install and all, but I´ve recently found out I was using 32bit version, unlike my 64-bit Windows. Therefore, I guess I didn´t get all the performance I could. So I downloaded the 64bit one, butned it to a CD and rebooted PC (I formatted all before so now I have only Win).
However, when trying to install Ubuntu64 there was no option to install it side by side and choose on startup. So I went to advanced and there was the partitioning thing. Now I have C and D, each by 120GB for windows and I had left 240GB for Ubuntu. It is disk E, however when I chose to install it there it says there is no root file. So please, help me at this point.
I want the whole E disc to be used for Ubuntu and I don´t know what mount point and the root thing to choose. Thanks

---

### Post by dino99 on 2010-07-29
prepare your hdd first:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

*** 64 bits brinks you more issues than 32 bits, better to install pae kernel on 32 bits, same advantages, less bugs)

---

### Post by zvacet on 2010-07-29
Before installing you will see window named create partition.There you have choice for

**location for new partition**: put on beginning

**use as **: ext4 journaling file system

**mount point **:  /

If you want to you can make separate home partition.In that case for root in enough 10 GB of space.Rest of free space (except ~2GB for swap) can be your home partition.On home will be your settings and files/data...so if you want to reinstall,fresh install home partition will be intact.

EDIT: Now I see answer from dino99 and I agree with him.It is easier to install pae kernel.

---

### Post by Cavsfan on 2010-07-29
> **Veren said:**
> Hello, 
first of all I am a casual PC user so I apologise if this is a stupid question.
Ok, here it goes..
I was using Ubuntu 10.04 32-bit alongside Windows, choosing between them each startup. It was easy to install and all, but I´ve recently found out I was using 32bit version, unlike my 64-bit Windows. Therefore, I guess I didn´t get all the performance I could. So I downloaded the 64bit one, butned it to a CD and rebooted PC (I formatted all before so now I have only Win).
However, when trying to install Ubuntu64 there was no option to install it side by side and choose on startup. So I went to advanced and there was the partitioning thing. Now I have C and D, each by 120GB for windows and I had left 240GB for Ubuntu. It is disk E, however when I chose to install it there it says there is no root file. So please, help me at this point.
I want the whole E disc to be used for Ubuntu and I don´t know what mount point and the root thing to choose. Thanks

I am dual booting Lucid and windows 7 64 and everything runs **great** on 64 bit. [B]64 bit is very stable!
[/B]When you go to install there should be an option towards the middle bottom that says Custom Install. You want to choose that. 
I was told to double my ram for my swap (I have 4GB and so I set swap to 8072MB) and left the rest to Ubuntu ext4 with a "/".

---

### Post by Veren on 2010-07-29
> **Cavsfan said:**
> I am dual booting Lucid and windows 7 64 and everything runs **great** on 64 bit. [B]64 bit is very stable!
[/B]When you go to install there should be an option towards the middle bottom that says Custom Install. You want to choose that. 
I was told to double my ram for my swap (I have 4GB and so I set swap to 8072MB) and left the rest to Ubuntu ext4 with a "/".

Thank you, I´m gonna do that right now.

Oh and thank you all too, I´m sure to check that link first
Bye

---

### Post by Cavsfan on 2010-07-29
> **Veren said:**
> Thank you, I´m gonna do that right now.

Oh and thank you all too, I´m sure to check that link first
Bye

Yes this is the LTS and I am glad you are sticking with it.
64 bit rocks baby! :guitar:

---

### Post by Veren on 2010-07-29
Ok please I ran to another problem...maybe as plain as the first one, but tough for me. I created the swap particle from my disk "E" as you have said with the size of 8GB, my ram is 4GB. The process took about an hour. The disk is 230GB big and I wanted to make the rest the root and home combined. However, I after the swap was created it made the rest of that disk unusable and I wasn´t able to do anything with it. My question is, whan talking about the ext4 particle, should I create it from what I now have as "C" ? I am also a bit scared of using the partedmagic, I don´t want to screw something up and format my windows disks. Thanks

---

### Post by Cavsfan on 2010-07-29
In windows 7 I was able to use disk manager to shrink my windows disk and free up about 100GB. That is how I did mine. I have not used gparted either.
I didn't partition it in windows just made it available.
Then when I did the custom install in Ubuntu. I created a logical partition of 8072GB (1024 x 8) for swap.
Then the rest of the 100GB I did make a partition of and I believe it is sda3.

See this screen shot of what it looks like in gparted now.

[[IMG]http://omploader.org/tNTJ6Mw[/IMG]]("http://omploader.org/vNTJ6Mw")

Windows 7 is on sda1 and I apparently have 1 MB unused.
The bottom 2 would be swap and ext4 "/"
I hope this helps

---

### Post by Cavsfan on 2010-07-29
> **Veren said:**
> Ok please I ran to another problem...maybe as plain as the first one, but tough for me. I created the swap particle from my disk "E" as you have said with the size of 8GB, my ram is 4GB. The process took about an hour. The disk is 230GB big and I wanted to make the rest the root and home combined. However, I after the swap was created it made the rest of that disk unusable and I wasn´t able to do anything with it. My question is, whan talking about the ext4 particle, should I create it from what I now have as "C" ? I am also a bit scared of using the partedmagic, I don´t want to screw something up and format my windows disks. Thanks

I'll get on windows 7 and see if I can figure out how you can do it as I did.

---

### Post by Cavsfan on 2010-07-29
In windows 7 64 bit home premium, if you type in the little search box just above the start button, enter "disk man" and you should see this appear:
**Create and format hard disk partitions** - click on that.

When you see your windows partition which will probably say **C:**
Right click on that and go down to **Shrink Volume** and it will take a while then show you how much room you can free up by doing this.

Here is what mine looks like in windows:

[[IMG]http://omploader.org/tNTJ6Zw[/IMG]]("http://omploader.org/vNTJ6Zw")
The 91.43FB is my ext4 / and the 7.63 is my swap file. Not quite sure why it shows that way, but it's windows.
I hope it lets you obtain enough disk space to install Ubuntu. :)

I had to defragment mine and that took forever to be able to get 100GB out of my 500GB drive.

I hope you don't need this, but here is a good free windows defragmenter that will defrag at bootup which is what you'll need.
And since this is windows, I suggest that after downloading, you right click on it and scan it for viruses. If you do need to download it.
You know how windows is!

[U][http://download.cnet.com/Puran-Defrag-Free-Edition/3000-2094_4-75115626.html](http://download.cnet.com/Puran-Defrag-Free-Edition/3000-2094_4-75115626.html)

[/U]Then once you have enough room to install Ubuntu you can go do that and choose **Custom Install**. 
You should be able to put both swap and ext4 / on the same drive.
I know nothing about using external drives... or even using separate drives either...

I do hope you can shrink your C: drive down w/o having to defragmenting it first!
But, you do what you gotta do! At least you know now what that is hopefully.

---

### Post by Veren on 2010-07-29
Thank you very much Cavstan, though with a little honour I must say I just managed to do it some other way, I simply changed my C particle to ext4 and changed mount point to /, I&#7743; not really sure how it worked but now I'm writing from my 64bit Ubuntu :p  So I thank you again for your response, it was very helpful.
Oh and there's one more thing that has always bugged me,though it's  more of a cosmetc one.
On the grub menu, I have about 5 choices. 4 of them have to deal with ubuntu starting in various modes and the last one is the Windows loader. Is there any way how I could get rid of the ones between normal Ubuntu boot and Win ? Thank you, see you in the morning.

---

### Post by Cavsfan on 2010-07-29
> **Veren said:**
> Thank you very much Cavstan, though with a little honour I must say I just managed to do it some other way, I simply changed my C particle to ext4 and changed mount point to /, I&#7743; not really sure how it worked but now I'm writing from my 64bit Ubuntu :p  So I thank you again for your response, it was very helpful.
Oh and there's one more thing that has always bugged me,though it's  more of a cosmetc one.
On the grub menu, I have about 5 choices. 4 of them have to deal with ubuntu starting in various modes and the last one is the Windows loader. Is there any way how I could get rid of the ones between normal Ubuntu boot and Win ? Thank you, see you in the morning.

Glad you got it going! I hope you do not have trouble getting into windows now. I think I did the last time I did a clean install.
Either I could get into windows and not ubuntu or the other way around.
Anyway, I hope this is not the case for you.

And about the bootup screen (GRUB2), funny you should mention that because I have made a tutorial for making a maintenance 
free GRUB2 screen along with how to add your own custom picture. I could never have figured this out on my own, a very 
knowledgeable guy on here **Ranch Hand** helped me do it. I just thought it was about time I shared that with everyone.
It will work if you just use Ubuntu or if you dual boot Ubuntu and windows like we do.
It won't work if you are also booting other OSs like Debian, etc.
I will submit it tomorrow if I get a chance and I have been told it may take a few more days for someone to look at it.

But, if you are willing to wait a few, this should be right what you and hopefully a lot of people need.

I was complaining about having to update the default line of my grub menu every time we got a new kernel.
This will solve that problem!   :D

---

### Post by Cavsfan on 2010-07-29
So, what I am talking about is if you want to and this is up to each person, but if you are 
dual booting Ubuntu and windows 7 or whatever you can have just 3 entries:

[COLOR=RoyalBlue]Ubuntu Lucid Lynx 10.04
Ubuntu Lucid Lynx 10.04 (Recovery Mode)
Windows 7[/COLOR]

Or if you just use Ubuntu, you would have 2 lines and they will never need changing.
The top line will always load the newest kernel.
You can still have Memtest listed if you want, but I do not. That will be up to each person.

And if you only have Ubuntu you could only have 2 lines:

[COLOR=RoyalBlue]Ubuntu Lucid Lynx 10.04
Ubuntu Lucid Lynx 10.04 (Recovery Mode)
[COLOR=Black]
And each time a new kernel is installed, it will automagically be taken care of.
[/COLOR][/COLOR]

---

### Post by Veren on 2010-07-30
Hello,
thank you for your advices, and yes you were right, my Windows stopped working yesterday :D But I found a way around it, and it was probably the simpliest solution ever :D I reinstalled Windows, but this time, I only made 2 particles, 120 GB one and 350. I don´t know why is this, but when there are only 2 particles, the Ubuntu installer offers you the option of installing Ubuntu and Win side by side, taking care of the partitioning part. So it split my 350 GB particle into 2, left a half of it for Windows games like I wanted and kept a half for itself. 
I really don´t know why it doesn´t offer the side by side thing when you have 3+ Win particles though.
Oh and to the Grub, I´m gonna try that right away. Now I have a Ubuntu startup, Ubuntu safemode, 2 memory test entries and Win loader, I´m gonna try to get rid the the ones in the middle. Thanks

---

### Post by Cavsfan on 2010-08-02
My tutorial on how to make a maintenance free GRUB2 menu is up now if anyone is interested.

See my post 2 posts up on this thread for details.

_[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)_

---

