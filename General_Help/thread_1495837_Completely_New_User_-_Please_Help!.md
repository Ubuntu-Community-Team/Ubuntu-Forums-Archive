---
title: "Completely New User - Please Help!"
date: 2010-05-28
forum: General Help
---

### Post by luke31 on 2010-05-28
Hi everyone. This is my first post! I'm completely new to the Linux platform, as I've been a windows/mac user all my life. When I discovered 10.04, I was genuinely excited about its potential. So, I decided to take the jump and install the new OS onto my self-built desktop computer. This computer can easily handle Vista and Windows 7, so technically speaking it is not inferior. When I installed 10.04, the OS was HORRENDOUSLY LAGGY! Everything seemed to be going slow. Even dragging an open window around the desktop was painful. Now, I am a complete Linux newb, but I really want to learn how to utilize its full potential. Before that, however, I need to repair this issue. Please help, I'm completely new to Linux! Some of my computer specs are: AMD 64 x2 Processor, 2 Gigs DDR2 RAM, ATI RADEON X1650 Pro 512 MB GPU, and a Western Digital 750 GB Hard Drive. Thanks, and I hope that I can have many pleasant experiences to come with Linux!

---

### Post by dougalkerr on 2010-05-28
Wow - the spec looks fast enough to drive all Linux versions really well.
I just downloaded and installed Ubuntu Ultimate Edition which is based upon 10.4 and it FLIES.
It might be worth doing this. As you are new to Linux it won't make any difference if you haven't used Linux before.
So far this version has been able to do the last couple of things that I have been having trouble with and now I am really happy.

Have a go - what have you got to lose.

If you want something else that is very, very easy on resources and minimalistic (no fancy graphics) try Crunchbang Linux.

It is very easy to use once you get used to it. Right-click on the empty desktop and you have instant access to a lot of useful programs and you can een play around with how the whole thing looks from certain menu entries as well.
Remember though that in Linux, to get a lot of stuff to install you have to type sudo then a space before any commands you might type into Terminal.
Have fun - delete everything off the hard drive and when the Partitioner opens upon Install select the manual option and then delete all partitions or whatever and then create a partition for SWAP that is twice the size of your RAM then create a partition that is abot half the size of what you have left and in the mount point textbox give a 'right-slash', you know the sort of thing... like this (/) without the brackets. Choose to format it as either ext3 or ext4, the SWAP partition will be taken care of automatically.
You can now apply the settings for the hard drive partition and carry on installing the system.
It doesn't matter that you have still half of your hard drive unformatted, this will be for the other system if you want to dual boot.
You can install what eer Linux system you want first out of say Crunchbang and Ubuntu Ultimate Edition but, the last one installed will take default position on the boot menu.
Go on have a go. Crunchbang is quite small and fast so once you have a cd burned you should have it installed within 15 minutes.
Ultimate Edition is a bit bigger at 2.2Gb (yes you will need a DVD) and takes a bit longer to install because of all the bells and whistles but, it's worth it.
Be patient when installing as sometimes it may look like nothing is happening when things are actually going on in the background. This is especially true if your monitor goes into sleep mode. the system will still be installing though so give it time. With Crunchbang you should only see one sleep occurence if things are set like mine. Again Ultimate Edition will have more.
Oh, and you can use rewriteable cds and dvs. No sense in wasting them.
Hope this helps alleviate some fears you might have been having.
Let us know how you are getting on.
Remember you can always run the cd or dvd in the 'Live' mode if things go **** up and get on line that way.

---

### Post by luke31 on 2010-05-28
> **dougalkerr said:**
> Wow - the spec looks fast enough to drive all Linux versions really well.
I just downloaded and installed Ubuntu Ultimate Edition which is based upon 10.4 and it FLIES.
It might be worth doing this. As you are new to Linux it won't make any difference if you haven't used Linux before.
So far this version has been able to do the last couple of things that I have been having trouble with and now I am really happy.

Have a go - what have you got to lose.

If you want something else that is very, very easy on resources and minimalistic (no fancy graphics) try Crunchbang Linux.

It is very easy to use once you get used to it. Right-click on the empty desktop and you have instant access to a lot of useful programs and you can een play around with how the whole thing looks from certain menu entries as well.
Remember though that in Linux, to get a lot of stuff to install you have to type sudo then a space before any commands you might type into Terminal.
Have fun - delete everything off the hard drive and when the Partitioner opens upon Install select the manual option and then delete all partitions or whatever and then create a partition for SWAP that is twice the size of your RAM then create a partition that is abot half the size of what you have left and in the mount point textbox give a 'right-slash', you know the sort of thing... like this (/) without the brackets. Choose to format it as either ext3 or ext4, the SWAP partition will be taken care of automatically.
You can now apply the settings for the hard drive partition and carry on installing the system.
It doesn't matter that you have still half of your hard drive unformatted, this will be for the other system if you want to dual boot.
You can install what eer Linux system you want first out of say Crunchbang and Ubuntu Ultimate Edition but, the last one installed will take default position on the boot menu.
Go on have a go. Crunchbang is quite small and fast so once you have a cd burned you should have it installed within 15 minutes.
Ultimate Edition is a bit bigger at 2.2Gb (yes you will need a DVD) and takes a bit longer to install because of all the bells and whistles but, it's worth it.
Be patient when installing as sometimes it may look like nothing is happening when things are actually going on in the background. This is especially true if your monitor goes into sleep mode. the system will still be installing though so give it time. With Crunchbang you should only see one sleep occurence if things are set like mine. Again Ultimate Edition will have more.
Oh, and you can use rewriteable cds and dvs. No sense in wasting them.
Hope this helps alleviate some fears you might have been having.
Let us know how you are getting on.
Remember you can always run the cd or dvd in the 'Live' mode if things go **** up and get on line that way.

Wow thanks so much! You have no idea how much this info helped, and I'll make sure to try out the things you mentioned. Ubuntu Ultimate Edition sounds enticing, I think I'll go for that first! Thanks again, one great thing about Linux is the community, as everyone is so helpful.

---

### Post by luke31 on 2010-05-28
hmmm it seems that I can't install the proprietary drivers for my ATI Radeon x1650 Pro... I think this could be part of the issue?

---

### Post by geet89 on 2010-05-28
What is this ubuntu ultimate edition?? is it supported by canonical?

---

### Post by amite on 2010-05-28
Try these links,i hope it will help u:
[http://ubuntuclips.org/index.html](http://ubuntuclips.org/index.html)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[http://blog.taragana.com/index.php/archive/top-10-ubuntu-ebooks/](http://blog.taragana.com/index.php/archive/top-10-ubuntu-ebooks/)

---

### Post by Spr0k3t on 2010-05-28
The UbuntuUltimate edition is the same thing as Ubuntu, only with added repos and extra software.  There are a few minor tweaks.  Other than that it's exactly the same.

The problem looks to be an issue with the ATI drivers.  I'm not well versed with ATI software in Linux otherwise I'm sure I could hammer this one out.  Check the sticky to see if there might be some issues related to the ATI drivers.

---

### Post by arvevans on 2010-05-28
I have a similar system (AMD 64 X2, 1 GB RAM, ATI Video, 750 GB SATA HD).
Initial install (back in the 8.04 days) was slow, but trial-and-error tweaking has it running quite fast now with Ubuntu 10.04 release.

First off...nvidia is not your friend, although you may need parts of it for some programs.  There are drivers in the repositories for ATI Radeon.
Use the Synaptic package manager and search for "ATI" to find and install what you need.   Conflicts between various video drivers seem to me to be the culprit, but I am not expert enough to prove that.

This computer is configured for 3 GB of swap.  That is probably more than needed, but it works for me.

I am presently running 32-bit Ubuntu on this 64-bit machine, but when I was running 64-bit it was almost the same speed.  The selection of 32-bit was driven by some wine issues, not by any speed situation.

Unfortunately I did not keep notes regarding what I tweaked to get the speed up to "fast", but it is possible to make your AMD 64X2 run very fast with Ubuntu 10.04 software.

---

### Post by Gerard08 on 2010-05-28
Luke,Your post could be a bit more informative. Did you install from a live CD that was created from a download, or purchased from a reliable online source? Did you try a standard install on the entire drive allowing the install program to determine the number and sizes of partitions? If you made a dual-boot over windows you should describe what option you chose. If you can run ubuntu from the disk without installation, the installation should proceed fine. Try [https://help.ubuntu.com/community](https://help.ubuntu.com/community) for installation tips. I installed ubuntu on a home-built.  It takes time to learn about a new program, and getting everything working. The initial install should go smoothly.  If something is very wrong, then focus on just this aspect of the problem rather than a broader question about the OS. 

I attached a Driver file from [http://cgit.freedesktop.org/](http://cgit.freedesktop.org/) It might help.

---

### Post by luke31 on 2010-05-28
> **Gerard08 said:**
> Luke,Your post could be a bit more informative. Did you install from a live CD that was created from a download, or purchased from a reliable online source? Did you try a standard install on the entire drive allowing the install program to determine the number and sizes of partitions? If you made a dual-boot over windows you should describe what option you chose. If you can run ubuntu from the disk without installation, the installation should proceed fine. Try [https://help.ubuntu.com/community](https://help.ubuntu.com/community) for installation tips. I installed ubuntu on a home-built.  It takes time to learn about a new program, and getting everything working. The initial install should go smoothly.  If something is very wrong, then focus on just this aspect of the problem rather than a broader question about the OS. 

I attached a Driver file from [http://cgit.freedesktop.org/](http://cgit.freedesktop.org/) It might help.

Let me clarify these points. I downloaded Ubuntu through ubuntu.com, specifically the desktop addition. I booted from the CD, proceeded with the on-screen prompts, and selected the option to wipe the entire Hard Drive and install onto the newly formatted drive. That pretty much entails the entire installation process. No dual boots, just a fresh install. I never tried running live from the cd, just went straight to the installation. I hope this helps!

EDIT: I burned the ISO onto a cd-rw disk via disk utility on my macbook.

---

### Post by choochoousmc on 2010-05-28
new user here too. Got a two month old Acer aspire 5532 notebook. Runs quite well on it so far.
You might want to go back to square one.
Are you dual booting?   windows and ubuntu?
If so, you may want to first defrag the whole hard drive with windows or standalone software.
Then reinstall. I had install problems at first with a corrupt live cd. So you may want to make sure it is a good cd.
But now installed it boots and shuts down way faster than windows vista or 7 (I skipped xp).
My windows move around fine and it recognized all my hard ware including wireless network, and wireless Epson Printer.
good luck, hopefully soem one more knowledgeable can provide better assistance!

---

### Post by dougalkerr on 2010-05-29
Luke

It does sound like a problem with the ATI drivers. Leave them uninstalled, you probably won't need them unless you intend to go for games or something graphical does not work.
A reinstall of the system should get you up and running again then do some more work with the system before bothering with the graphics drivers.
Get familiar with things and how to recover from graphics problems when you do finally go for the graphics drivers install.
There are instructions on how to recover the 'X' video system if it goes **** up and usually you can repair graphics problems at boot by selecting system recovery/repair mode the choosing the option for repairing the graphics (I think it usually restores the graphics system to what it was before the ATI or other drivers took over).

If you followed all my instructions the other night then you will have some spare space on your hard drive.
Download and burn Crunchbang Linux.
Run the LiveCD and once the system has finished right-click and choose Install.
It goes the same as Ultimate Edition and when you get to the Partition manager choose the space left from before and opt for either ext3 or 4 as before and the mount label as a right-slash '/' again.

Crunchbang works very well without needing the graphics drivers installed and it is a simple but, powerful system. Easy to get used to and will get you some practice with typing into the Terminal to install things.
Good Luck again...

---

### Post by Gerard08 on 2010-05-31
Hi,

I think choochoousmc has a good point. The file is large, and there can be problems down loading and burning a new cd. Perhaps just try a second burn? The live version of the unbuntu download allows you to run the OS from the disk-something unique to Linux distros. If it runs smoothly on your hardware from disk, it should install OK. I'll defer to Dougalkerr about ATI drivers. There are many linux distributions, some that are lighter than Ubuntu. Keep in mind that as a linux user it is common to find that a configuration for your machine needs adjustment, and you have to read posts to understand how something works, then try your own fix. In your case, as a new user, try to get up and running quickly. You can then make smaller tweeks to optimize your system. By all means try other distros. I like ondisk.com for their distributions. Sometimes spending a few bucks can save aggravation.

---

