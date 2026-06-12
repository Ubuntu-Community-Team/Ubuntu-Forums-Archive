---
title: "leaving Lucid 10.04 64 bit 'cause it's unusable*"
date: 2010-07-29
forum: General Help
---

### Post by RabbitWho on 2010-07-29
Some problems I've had: 

[http://ubuntuforums.org/showthread.php?t=1534903](http://ubuntuforums.org/showthread.php?t=1534903)
[http://ubuntuforums.org/showthread.php?t=1540983](http://ubuntuforums.org/showthread.php?t=1540983)

There've been lots of others, but I've solved them, these I can't solve and it seems no one else has these problems and no one can help me. 

I'm sick of crashes and restarting my computer 10 times a day. 

[B]
So my questions: 
Where do I go? 

32 bit lucid? Jaunty? (I had a year of very happy problem-free use with Jaunty 32 bit) Reinstall 64 bit Jaunty?
[/B]
Specs: 
Dell Inspiron Laptop 1545
Pentium Dual-Core T4200 @2.00 Ghz 
4GB of RAM
Graphics is Intel Intergrated GMA 4500MHD

[B] How do I redo the ubuntu partition without hurting the Windows partition? Just delete it completely? From Windows?
How do I keep all the programs I've saved in Lucid now, can I just copy the "home" folder to an external HDD and then replace the Home folder in the new install with the old Home folder? 
[/B]
Is it possible to get 4GB of ram working in a 32bit OS? 


I have already:
- ran memtest
- ran badblocks
- have up to date grub
- have proper drivers for graphics card

Yes it's a 64 bit OS. 
Yes I know lucid 64bit works well for you :)  6 people have told me now.



[SIZE=1]*unusable for me in my computer right now




[/SIZE]

---

### Post by cbstryker on 2010-07-29
It's odd that you are having issues with 10.04. Personally I've found it to be very good, except for a bug that was in the Xorg server that did not allow any screen to be a negative integer (as in a screen left of screen 0, which would be -1). But that since was promptly fixed.

The flashing screen issue seems like it could be a video driver or compiz issue.

If you really want to reinstall a previous version simply select "Manual Partition" during install and select your Ubuntu partition, set it to "mount to /" and format it. That's all you should need to do to get a fresh install, and that won't affect your windows installs.

You can copy your /home folder but that wouldn't save any of your installed programs, but it would save all your preferences and settings.

---

### Post by RabbitWho on 2010-07-29
> **cbstryker said:**
> It's odd that you are having issues with 10.04. Personally I've found it to be very good, except for a bug that was in the Xorg server that did not allow any screen to be a negative integer (as in a screen left of screen 0, which would be -1). But that since was promptly fixed.

The flashing screen issue seems like it could be a video driver or compiz issue.



But those are just graphics things, right?  And this is an actual window that opens and closes, it drives the processor demented. 

> 
If you really want to reinstall a previous version simply select "Manual Partition" during install and select your Ubuntu partition, set it to "mount to /" and format it. That's all you should need to do to get a fresh install, and that won't affect your windows installs.

You can copy your /home folder but that wouldn't save any of your installed programs, but it would save all your preferences and settings.Thanks, there's no way to not loose all that stuff? ISP has a limit on how much we download. I can't get them again, and I loose internet access in a month.

---

### Post by Cavsfan on 2010-07-29
I have been running Lucid 64 bit since it was beta and it works great for me!
And I am dual booting with windows 7.
You have only been on Lucid for a week, at least that is the date of your first posted problem and your 2nd posted problem is less than a day old.

I hope you stick around a little longer to see if someone can solve your problems. Because once they are tweaked and fixed, they will remain fixed I am pretty sure.

Also, I urge you not to get impatient and bump threads after a short while as I think that causes people to ignore them. 
I would give them at least a day or so before bumping.
Just provide as much information as you can about your problem and the right person will come and help. I have never seen a more helpful forum than this one.

---

### Post by cbstryker on 2010-07-29
> **RabbitWho said:**
> But those are just graphics things, right?  And this is an actual window that opens and closes, it drives the processor demented.

Well, I've never experienced that. That's really odd. Does that only happen with a specific program? 

> **RabbitWho said:**
> Thanks, there's no way to not loose all that stuff? ISP has a limit on how much we download. I can't get them again, and I loose internet access in a month.

Technically you could scour through all the /bin /usr/bin etc etc etc and copy all the files, but in all honestly, that will literally guarantee a broken system because you are not pulling all the dependencies with a package manager. Your system will be far worse than it ever was.

I know the pain of download caps. When I needed to reinstall Lord of the Rings Online it was a 10GB download (which failed twice, so it added up to about 25GB) and then it needed to patch about another 4 or so GB. I was on a 60GB cap. I whole heartedly disagree in caps which is why I switched providers and went with unlimited. I personally think all service providers with download caps less than 100GB for their cheapest ($20/mo) plan should be boycotted.

---

### Post by dino99 on 2010-07-29
there are less isuues with pae kernel (32 bits) and you get the same advantages as 64 bits, so why choosing the wrong install ?

---

### Post by Cavsfan on 2010-07-29
> **RabbitWho said:**
> But those are just graphics things, right?  And this is an actual window that opens and closes, it drives the processor demented.

What graphics card do you have and are you using the recommended driver for it?
System > Administration > Hardware Drivers.

---

### Post by Cavsfan on 2010-07-29
> **dino99 said:**
> there are less isuues with pae kernel (32 bits) and you get the same advantages as 64 bits, so why choosing the wrong install ?

I am using the latest 64 bit kernel with no problem at all. 
I think **RabbitWho** needs to stick with 64 bit and let us iron out the problems he is having as they may end up being minor fixes.

---

### Post by Quackers on 2010-07-29
I'm sorry you're having problems RabbitWho. I had a couple of graphics problems until I installed the nvidia driver for my card (8600M GT) but since then it's been great.
I was very pleasantly surprised when I installed Lucid as everything (except graphics) worked right out of the box. I didn't expect that (after previous installations problems). I've even got wobbly windows when I maximise/minimise. 
I hope you can sort things out.
I've been so sick of Windows that I've even installed Snow Leopard too. I have to say that Lucid works better than Snow Leopard so far.
Good luck.

---

### Post by RabbitWho on 2010-07-29
> **cbstryker said:**
> Well, I've never experienced that. That's really odd. Does that only happen with a specific program? 


No it happens almost every time I boot up and it happens before I open anything.

>  


Technically you could scour through all the /bin /usr/bin etc etc etc and copy all the files, but in all honestly, that will literally guarantee a broken system because you are not pulling all the dependencies with a package manager. Your system will be far worse than it ever was.

I know the pain of download caps. When I needed to reinstall Lord of the Rings Online it was a 10GB download (which failed twice, so it added up to about 25GB) and then it needed to patch about another 4 or so GB. I was on a 60GB cap. I whole heartedly disagree in caps which is why I switched providers and went with unlimited. I personally think all service providers with download caps less than 100GB for their cheapest ($20/mo) plan should be boycotted.

60 GB? You don't know the pain! 
I know it's bad. I'm on a 15 GB cap. We don't have a choice about what ISP we use because the others are even worse for mobile broadband. 


[LIST]
[*]All O2 Broadband Plans have a data usage limit and a charge of 1.6c  per MB (ex VAT) applies for all usage in excess of the data usage limit  on your plan."
[/LIST]

There is no way to tell how many megabites you've downloaded, which means if we ever go over I'm going to fight them tooth and nail if I can. 

In Turkey it's even worse again, My parents have a 4 GB limit. They had to pay 100 euro for their dongle and if anything happens to it they have to buy it again.

---

### Post by RabbitWho on 2010-07-29
> **Cavsfan said:**
> What graphics card do you have and are you using the recommended driver for it?
System > Administration > Hardware Drivers.


Graphics is Intel Intergrated GMA 4500MHD

Don't know what the story is with drivers, only things mentioned in *Hardware Drivers* are some wireless ones.

Again I think the fact that the flashing window only happens on start up (never randomly while I'm doing something) and is processor intensive means it has nothing to do with graphics. 

I can live with the other graphics glitches, though I'd rather not! But fixing them isn't going to matter if we can't solve the flashing window because if we can't solve that I can't keep using lucid.

---

### Post by Cavsfan on 2010-07-29
I have an nvidia card, so I can't help, but I am sure someone with knowledge of your graphics card 
will come along and help. It can't be a show stopper as probably many people have an Integrated video card like yours.

---

### Post by RabbitWho on 2010-07-29
This is what I'm doing now: 

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

It'll take a while before I know if it's worked or not because likesay the problems happen at random, there's nothing i can do to bring them on.

---

### Post by Cavsfan on 2010-07-29
> **RabbitWho said:**
> This is what I'm doing now: 

[http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx](http://www.howtoforge.com/how-to-install-latest-intel-driver-2.12-on-ubuntu-10.04-lucid-lynx)

It'll take a while before I know if it's worked or not because likesay the problems happen at random, there's nothing i can do to bring them on.

That looks like a good link dated July 5th 2010, so I hope it helps you! It should! :D

---

### Post by cbstryker on 2010-07-29
> **RabbitWho said:**
> 60 GB? You don't know the pain! 
I know it's bad. I'm on a 15 GB cap. We don't have a choice about what ISP we use because the others are even worse for mobile broadband. 

In Turkey it's even worse again, My parents have a 4 GB limit. They had to pay 100 euro for their dongle and if anything happens to it they have to buy it again.

Well, I'm sorry but all I can say is... OUCH!! That really should be illegal!

---

### Post by Cavsfan on 2010-07-29
Don't let anyone talk you out of 64 bit! It is stable and I have been using it for about a year and a half with no problems!
The only thing is Adobe dropped 64 bit flash, but here is a link for **lovinglinux**'s FLASH-AID that he has developed as an add-on for Firefox.

_[https://addons.mozilla.org/en-US/firefox/search/?q=flash-aid](https://addons.mozilla.org/en-US/firefox/search/?q=flash-aid)_

He has a later version that is being reviewed by Mozilla and will be available in less than a week, but this one should work now.
This will install 32 bit flash as that is all that is available right now. But, it works great! 
And if the buttons on youtube do not work e.g. you cannot pause it or get any buttons to work there is an easy workaround for that.
Let me know if that happens to you.

---

### Post by cbstryker on 2010-07-29
> **Cavsfan said:**
> Don't let anyone talk you out of 64 bit! It is stable and I have been using it for about a year and a half with no problems!

Agreed. Linux 64bit was stable long before Windows 64bit ever was.

---

### Post by RabbitWho on 2010-07-30
Okay so today when I booted up the first time it froze on the background of the login screen after login.

The second time I got in but the panels wouldn't start and no programs would open and I couldn't even get at the terminal. 

The third time I had that gosh darned flashing window again.


To everyone who came here to tell me that Lucid work well for them.. That's great! I'm so happy for you! But as I said in my first post [B]it doesn't work at all for me. 

[/B]
So unless anyone knows how to fix it could I please get help with getting rid of it? 

I wonder will swapping to 32 bit help? Is there a way to get the 4GB of ram active in a 32 bit OS because the last time only 3.2 was working. 

 I'm so upset I'm going to loose all my programs, maybe I'll be able to find an unsecured wireless somewhere and download all the stuff again. Arrrrgh

---

### Post by Quackers on 2010-07-30
32 bit might be worth a go. In my (limited) experience things do seem to work better in 32 bit. 
BTW have you checked for disk/ram errors?

---

### Post by Cavsfan on 2010-07-30
> **RabbitWho said:**
> Okay so today when I booted up the first time it froze on the background of the login screen after login.

The second time I got in but the panels wouldn't start and no programs would open and I couldn't even get at the terminal. 

The third time I had that gosh darned flashing window again.


To everyone who came here to tell me that Lucid work well for them.. That's great! I'm so happy for you! But as I said in my first post [B]it doesn't work at all for me. 

[/B]
So unless anyone knows how to fix it could I please get help with getting rid of it? 

I wonder will swapping to 32 bit help? Is there a way to get the 4GB of ram active in a 32 bit OS because the last time only 3.2 was working. 

 I'm so upset I'm going to loose all my programs, maybe I'll be able to find an unsecured wireless somewhere and download all the stuff again. Arrrrgh

I don't know what the problem is, but I know _it is not_ the fact that it is 64 bit.

---

### Post by Quackers on 2010-07-30
Is there a 64 bit driver for his graphics card? That's what I was thinking.

---

### Post by coolman98 on 2010-07-30
don't leave !!:(

---

### Post by RabbitWho on 2010-07-30
> **Quackers said:**
> Is there a 64 bit driver for her graphics card? That's what I was thinking.


You mean downloadable? 

It came with 64bit Vista first day, so it's certainly meant to work with it. 

> 
BTW have you checked for disk/ram errors?     
How? Bare in mind as it stands I can't even boot into ubuntu, I'm posting from the Windows 7 part.

---

### Post by Quackers on 2010-07-30
Don't you get a memtest86 entry in the grub menu? That's the ram test. There must be a way to check the hard disk for errors. Maybe a first step would be from within Windows7. Maybe someone more knowledgable than me could give you an idea.

---

### Post by jmszr on 2010-07-30
RabbitWho,

In response to "Is it possible to get 4GB of ram working in a 32bit OS? "
From: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE) -

"Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD."

If you are continuing to have the same problen at start up, then the 32-bit version is certainly worth a try.
If you have a separate /home partition then when Manually installing designate /home as /home but do NOT format /home. If you don't have a separate /home then you will have to backup /home prior to reinstallation (of course,you should backup /home no matter what the circumstances). As far as the other Ubuntu-installed programs you might try UMarks: [https://addons.mozilla.org/en-US/firefox/addon/13153/](https://addons.mozilla.org/en-US/firefox/addon/13153/) .

If memtest isn't on the Lucid Live CD menu (as a choice when first booting the Live CD) then I know that it is on the 8.04 Live CD menu. 

Edit: You can also download memtest from here: [http://www.memtest.org/#downiso](http://www.memtest.org/#downiso) and burn it to CD.

Edit2: RabbitWho, I had several of your threads open at once so part of my post here refers to posts that aren't on this thread.

---

### Post by RabbitWho on 2010-07-30
Thanks guys. 
Did the memtest, "pass". 
Nothing strange. 

downloading 32bit lucid. cross your fingers.

---

### Post by RabbitWho on 2010-07-30
Gonna try installing 32 bit on a likkel partition and see if it works okay, then delete both and install it over all of it if it does work. 

I won't endanger windows7 fecking around like this? I don't want to have to install all this again AS WELL.

---

### Post by QIII on 2010-07-30
Maybe I missed it, but...

If you are going to attempt a reinstall, why not try reinstalling the 64 bit version first?  Before you do, run a disk "repair" tool to see if you have any bad sectors.  If you have a physical problem with the disk (which I generally solve by installing a new one), critical files may have been damaged.  If, for instance, one of the heads banged on a platter when you accidentally kicked the machine, you'd could end up with problems.

Your sample size of one machine not withstanding, the 64 bit version works well for many (most?) users.  

Just saying that if you are going to go through the effort, try again with 64 bit.

By the way, did you check the md5sum on the .iso and do the integrity check on your burned disks?

(Again, forgive me if I have missed something in the thread.)

So long as you use manual partitioning and don't touch your Windows partitions, you should be safe.

BUT:  DO BACKUPS!   DO BACKUPS!   DO BACKUPS!

---

### Post by RabbitWho on 2010-07-30
> **QIII said:**
> Maybe I missed it, but...

If you are going to attempt a reinstall, why not try reinstalling the 64 bit version first?  Before you do, run a disk "repair" tool to see if you have any bad sectors.  If you have a physical problem with the disk (which I generally solve by installing a new one), critical files may have been damaged.  If, for instance, one of the heads banged on a platter when you accidentally kicked the machine, you'd could end up with problems.

 

:( 
So a good disk repair tool is?

> 
Your sample size of one machine not withstanding, the 64 bit version works well for many (most?) users.  

Just saying that if you are going to go through the effort, try again with 64 bit.
You're the 4th person in one thread to tell me how it works well for everyone else. :D Like I said I'm really happy for you, and imma let you finish, but :P 
It would be much nicer for me if everyone had had the same problem, because then they'd know how to fix it. ;)

It worked okay for a few days, i don't want to start using it again and installing it and settling in only to find the same problems come back. When I've no idea what they are there's no way to prevent them. It's so disheartening. 

From the very first second I had little graphics glitches, i've seen them before on xfce and kde but this time i even had them on gnome and lxde. 

I don't have loads of time to keep trying out different stuff. I need something that's reliable. . I have 1000 things to do and I can't do anything with my computer like  this. 


> 
By the way, did you check the md5sum on the .iso and do the integrity check on your burned disks?
yup

> 
So long as you use manual partitioning and don't touch your Windows partitions, you should be safe.

BUT:  DO BACKUPS!   DO BACKUPS!   DO BACKUPS!There's nothing to back up on windows but a few installs, it's just an awful lot of hassle, you know yourself

---

### Post by wkulecz on 2010-07-30
> **RabbitWho said:**
> Some problems I've had: 


Specs: 
Dell Inspiron Laptop 1545
Pentium Dual-Core T4200 @2.00 Ghz 
4GB of RAM


No real point in installing 64-bit OS on a system with <= 4GB of RAM.  I'd suggest trying the 32-bit version -- drivers are more mature and better tested.

> I won't endanger windows7 fecking around like this?
This is one area I've had lots of issues with, the switch to grub2 since 9.10 makes it a lot harder to fix, but the how-tos and docs are catching up.  Keep this link handy:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)


I've found 64-bit 10.04 extremely stable on four different systems, my only issue has been somewhere along the way CD/DVD burning has broken so I have to dual boot into Windows or 8.04 to burn a disk (something that would have been a show-stopper a couple of years ago, but not such a big deal now as I rarely burn disks anymore).

But unless the upgrade brings new features you need, I'm a big believer in "if it ain't broke, don't fix it!"  In fact, I still do most of my Windows work on Windows 2000 as with the exception of video editing where Windows 7 is a big improvement, everything since has been a step backwards, IMHO.

I'm talking better than the power company reliable -- I only reboot when the power has been out longer than my UPS can keep it alive, or there is a kernel security update.  Windows 2000 will randomly crash if I forget to reboot it every 6 or 7 weeks, which reminds me, I need to reboot it this weekend.

I turn off the monitors when I'm not using them, but I hate waiting for boot up -- probably 10.04 biggest improvement, but largely negated by the hassles caused by grub2 and the "plymouth" splash screen dodad :(

My 10.04 systems do double duty as file servers so they don't just sit idle.

---

### Post by QIII on 2010-07-30
> **RabbitWho said:**
> You're the 4th person in one thread to tell me how it works well for everyone else. :D Like I said I'm really happy for you, and imma let you finish, but :P 
It would be much nicer for me if everyone had had the same problem, because then they'd know how to fix it. ;)

Yeap.  (I hope you didn't take that as "Neener neener!  It works for me!)  If everyone were having the same problem, it would be something several people had fixed and could tell you about.

Sometimes "one-off" problems are the hardest to solve.

A quick and dirty way to detect (generally) bad sectors would be to use badblocks from the LiveCD.  It's a first step.

---

### Post by RabbitWho on 2010-07-30
Everyone says something completely different. Even the Ubuntu website says different things about 32 bit vs. 64bit on different pages.
It goes from "not recommended" to "being absolutely the thing to do unless you have some specific reason for needing 32bit" 

Anyway I tried to back up my home folder on an external hard drive from ubuntu and surprise surprise it crashed. I don't want to do it again in case it damages the externall hdd and deletes my stuff. and it won't mount from the live cds so now what? how do i get into the ubuntu files from windows?

Why is nothing ever easy. :(

---

### Post by QIII on 2010-07-30
> **wkulecz said:**
> No real point in installing 64-bit OS on a system with <= 4GB of RAM.  I'd suggest trying the 32-bit version -- drivers are more mature and better tested.

Sorry.  Both inaccurate, old information and persistent FUD.

RAM is inconsequential to the discussion.  The 64 bit machine architecture is supplied with 64 bit and 32 bit instruction sets.  Using a 64 bit OS makes use of the more efficient 64 bit instruction sets, regardless of the amount of RAM.

Since the 32 bit instruction sets are available, *most  *(not all) 32 bit applications will work in a 64 bit OS.  That's not universal.

As for drivers and software?  This was true several years ago.  It is not true any more, except for a few cases in which developers are not keeping up with the rest of the industry.

Do you remember when people doggedly held on to 16 bit OSes when 32 bit hardware became the norm?

If you have 64 bit machine architecture, use a 64 bit OS.  The exception would be in a case where you absolutely MUST use a 32 bit application that WILL NOT work in a 64 bit environment.

---

### Post by CharlesA on 2010-07-30
If /home is on an EXT4 partition there isn't much you can do to access it from Windows.

What error is it saying when you try to mount it from a livecd?

---

### Post by QIII on 2010-07-30
> **RabbitWho said:**
> It goes from "not recommended" ...

That has been discussed and there is some semi-official word that this will be reviewed/corrected/mulled over/...

I think there may have been some "lingering 64 bit general issues in the industry" concerns, based on a response I saw on launchpad.  Obviously, I can't speak for Canonical.

---

### Post by QIII on 2010-07-30
> **RabbitWho said:**
> Why is nothing ever easy.

I have to be utterly honest with you and say that I don't think I've run  across anyone who has had nearly the fundamental issues you have had!   It's really hard to understand.  I'm at a loss.

Somehow, we just have to get you back to something that will work.

Did you try badblocks?  What you are describing seems to be shot through so many things that I really wonder if there is some disk damage and file corruption.

---

### Post by RabbitWho on 2010-07-30
Software to get into linux from windows: 


[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

Problem.. need administrator privileges. Have administrator privillages. Windows is an idiot. 

> **QIII said:**
> I have to be utterly honest with you and say that I  don't think I've run  across anyone who has had nearly the fundamental  issues you have had!   It's really hard to understand.  I'm at a loss.

Somehow, we just have to get you back to something that will work. 

Did you try badblocks?  What you are describing seems to be shot through  so many things that I really wonder if there is some disk damage and  file corruption.

Right, checking out badblocks now. Does that have to be run from inside ubuntu? If so i'll try it once I've reinstalled.. gotta figure out how to back stuff up now

> 
What error is it saying when you try to mount it from a livecd?      Oh it's so long! The jist is that it's broken, and there's instructions on how to fix it. But it's not broken because it works through windows. o.O 

I might try it again. 


I could always send it back to dell, i have about 2 weeks of original warranty left... it's just i've no idea how I'd explain what's wrong. I could just put a piece of paper linking to this thread inside.

---

### Post by soldier1st on 2010-07-30
boot from the livecd and copy your data from ubuntu to another spot and reinstall it. also for your problem is your system overheating? also what are your system specs?also did you install any unsupported/prereleased updates as once ubuntu is installed you should update it fully.

---

### Post by QIII on 2010-07-30
Run badblocks from the LiveCD so your hard drive is not mounted.

---

### Post by RabbitWho on 2010-07-30
Got the external HDD to mount from the live cd

new problem

it says i don't have permission to copy any of the files. I went to users and groups and ticked all the boxes, didn't help. 
There's no permission issue with the external HDD because it would copy earlier from the ubuntu install which is giving me all the problems and crashed before I could finish copying the stuff. 
Hopefully the HDD was fine because I can still get into the files from windows.

---

### Post by RabbitWho on 2010-07-30
and re: badlocks: 

```

ubuntu@ubuntu:~$ badblocks
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]
ubuntu@ubuntu:~$ badblocks -b
badblocks: option requires an argument -- 'b'
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]
ubuntu@ubuntu:~$ badblocks -i
badblocks: option requires an argument -- 'i'
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]
ubuntu@ubuntu:~$ badblocks /dev/hda1 > bad-blocks
badblocks: No such file or directory while trying to determine device size
ubuntu@ubuntu:~$ fsck -t ext3 -l bad-blocks /dev/hda1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext3: No such file or directory while trying to open /dev/hda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```no idea what I'm doing.


> **soldier1st said:**
> boot from the livecd and copy your data from  ubuntu to another spot and reinstall it.  That's what I'm trying to do, I'd appreciate your advice. 
> 
also for your problem is your  system overheating?

Nope. 
> 
 also what are your system specs? 
in very first post.
> 
also did you install  any unsupported/prereleased updates as once ubuntu is installed you  should update it fully.

I did everything in the update manager and some drivers to get wireless working and medibuntu repos and... well all the usual  stuff, yanno!

---

### Post by QIII on 2010-07-30
Try

```
badblocks -b 512 /dev/sda
```Replace "sda" with the device you are checking.

I'm going from memory on the syntax here.  If that doesn't work, I'll take a look at the man pages when I get home.

---

### Post by RabbitWho on 2010-07-30
```
ubuntu@ubuntu:~$ badblocks -b 512
Usage: badblocks [-b block_size] [-i input_file] [-o output_file] [-svwnf]
       [-c blocks_at_once] [-d delay_factor_between_reads] [-e max_bad_blocks]
       [-p num_passes] [-t test_pattern [-t test_pattern [...]]]
       device [last_block [first_block]]

```

Does it know what it's supposed to be looking at? I mean could the problem be specifically that it doesn't know what it's supposed to check for blocks?

---

### Post by RabbitWho on 2010-07-30
> **QIII said:**
> Try

```
badblocks -b 512 /dev/sda
```Replace "sda" with the device you are checking.

I'm going from memory on the syntax here.  If that doesn't work, I'll take a look at the man pages when I get home.

How do I know what letters are going to represent it? It's just called "278gb filesystem"

When I right clicked and went to properties it said it's name was... *deep breath* 244d8db9-d569-43fc-a01c-4ea2f0498194

So I tried that... predictably.. 
```

ubuntu@ubuntu:~$ badblocks -b 512 /dev/244d8db9-d569-43fc-a01c-4ea2f0498194
badblocks: No such file or directory while trying to determine device size

```

---

### Post by QIII on 2010-07-30
Fat fingers.

---

### Post by QIII on 2010-07-30
The alphabet is the UUID.

Would you type

```
sudo fdisk -l
``` in the terminal.  That's a small "ell", not a "one".

Post the results inside code tags.

---

### Post by borth92 on 2010-07-30
Rabbitwho I'm glad to see you made a new thread that wasn't nearly as insulting to the community. Idk why you have had so many problems, maybe your machine isn't made to run 64-bit? I have a Dell XPS M1330 with 4gb RAM that is made to run 32-bit, I can only imagine the horrors I would have with a 64-bit version. Try running a 32-bit version of 10.04, and I think most of your problems will be gone.

---

### Post by QIII on 2010-07-30
He has a 64 bit processor.

---

### Post by CharlesA on 2010-07-30
> **RabbitWho said:**
> 

it says i don't have permission to copy any of the files. I went to users and groups and ticked all the boxes, didn't help. 
There's no permission issue with the external HDD because it would copy earlier from the ubuntu install which is giving me all the problems and crashed before I could finish copying the stuff. 
Hopefully the HDD was fine because I can still get into the files from windows.

Did you still have the same problem after running *sudo nautilus*?

> **QIII said:**
> The alphabet is the UUID.

Would you type

```
sudo fdisk -l
``` in the terminal.  That's a small "ell", not a "one".

Post the results inside code tags.

If it's the primary drive, it's probably going to be /dev/sda1 but it is always best to double check. :)

---

### Post by RJARRRPCGP on 2010-07-30
> **RabbitWho said:**
> 

I'm sick of crashes and restarting my computer 10 times a day. 



For at least 98 percent, sounds like your hardware is garbage, because of bad components. Sorry. :( A possible cause is  crapacitors. => [http://badcaps.net](http://badcaps.net)

---

### Post by RabbitWho on 2010-07-31
ran badblocks on "sda" last night. no readouts so i've no idea if anything happened, got in without problems on third attempt today. 

```

rabbit@penguincounter:~$ sudo fdisk -l
[sudo] password for rabbit: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9b17c2d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3658    29376770    7  HPFS/NTFS
/dev/sda2            3658       38914   283192321    5  Extended
/dev/sda5            3658       37480   271679488   83  Linux
/dev/sda6           37481       38914    11511808   82  Linux swap / Solaris

Disk /dev/sdb: 1017 MB, 1017643008 bytes
29 heads, 60 sectors/track, 1142 cylinders
Units = cylinders of 1740 * 512 = 890880 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


```
> **borth92 said:**
> Rabbitwho I'm glad to see you made a new thread that wasn't nearly as insulting to the community. Idk why you have had so many problems, maybe your machine isn't made to run 64-bit? I have a Dell XPS M1330 with 4gb RAM that is made to run 32-bit, I can only imagine the horrors I would have with a 64-bit version. Try running a 32-bit version of 10.04, and I think most of your problems will be gone.


I have never ever insulted the community.

---

### Post by RabbitWho on 2010-08-01
```
ubuntu@ubuntu:~$ badblocks -b 512 /dev/sda1
badblocks: Permission denied while trying to determine device size
ubuntu@ubuntu:~$ sudo badblocks -b 512 /dev/sda1



```What can I expect from this? 

Is it going to fix problems? Just tell me I have problems? Both? Neither?

Neither? Or something with no info given. 

Now trying: 

```
ubuntu@ubuntu:~$ sudo badblocks -nvs /dev/sda1
Checking for bad blocks in non-destructive read-write mode
From block 0 to 29376769
Checking for bad blocks (non-destructive read-write test)
Testing with random pattern: done                                
Pass completed, 0 bad blocks found.


```
Doing sda5 now

---

### Post by RabbitWho on 2010-08-02
Finished, took 15 hours. No blocks found. Does that mean the hard drive is okay? or does it mean absolutely nothing?

---

### Post by regeya on 2010-08-02
> **RabbitWho said:**
> Some problems I've had: 

[http://ubuntuforums.org/showthread.php?t=1534903](http://ubuntuforums.org/showthread.php?t=1534903)
[http://ubuntuforums.org/showthread.php?t=1540983](http://ubuntuforums.org/showthread.php?t=1540983)

There've been lots of others, but I've solved them, these I can't solve and it seems no one else has these problems and no one can help me. 

I'm sick of crashes and restarting my computer 10 times a day. 

[B]
So my questions: 
Where do I go? 

32 bit lucid? Jaunty? (I had a year of very happy problem-free use with Jaunty 32 bit) Reinstall 64 bit Jaunty?
[/B]
Specs: 
Dell Inspiron Laptop 1545
Pentium Dual-Core T4200 @2.00 Ghz 
4GB of RAM
[B] 
How do I redo the ubuntu partition without hurting the Windows partition? Just delete it completely? From Windows?
How do I keep all the programs I've saved in Lucid now, can I just copy the "home" folder to an external HDD and then replace the Home folder in the new install with the old Home folder? 
[/B]
Is it possible to get 4GB of ram working in a 32bit OS? 

[SIZE=1]*unusable for me in my computer right now



[/SIZE]

****

OK, I'm going to be harsh about this.

How about, instead of starting with being a drama queen, start with memtest?  That'd be far more constructive.

I mean, it sounds like a hardware issue to me.  10.04 has been for me, personally, the most stable, trouble-free release I've used to date.

---

### Post by RabbitWho on 2010-08-02
> **regeya said:**
> 

OK, I'm going to be harsh about this.

How about, instead of starting with being a drama queen, start with memtest?  That'd be far more constructive.

I mean, it sounds like a hardware issue to me.  10.04 has been for me, personally, the most stable, trouble-free release I've used to date.

Been there, done that. 
How about, instead of being nasty for no reason, reading the thread? Thanks.

---

### Post by RabbitWho on 2010-08-02
Installed 32 bit. 

Not a single problem yet. And everything even mounts immediately every time. :D Not even the flickers I was getting on the 64bit live CD.

---

### Post by Quackers on 2010-08-02
Nice one :-)

---

### Post by RabbitWho on 2010-08-02
:D

Right! all this time and not a problem yet. 

Marking this thread as solved, even though it's a bit of an unsolved mystery as to why it wasn't working before. Maybe my processor is borderline or maybe the  64bit cd was scratched or maybe i deleted something important without realizing it. Just keeping my fingers crossed :) 

Thanks so much everyone who helped!

---

### Post by CharlesA on 2010-08-02
Glad you got it working!

---

