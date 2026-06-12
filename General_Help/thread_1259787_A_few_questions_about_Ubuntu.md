---
title: "A few questions about Ubuntu"
date: 2009-09-06
forum: General Help
---

### Post by Haxes on 2009-09-06
Hello, all

Recently, I have downloaded and installed Ubuntu using the Wubi installer to install Ubuntu within Windows Vista. While I do love Ubuntu very much, and I am considering the switch to Ubuntu, however, before I do, I have a few questions I would like to ask.

1) I am on the Ubuntu part of my computer as we speak. I noticed that Ubuntu automatically recognized all of my drivers for my laptop, and everything is workiing correctly. Is this because I already have Windows Vista installed to my HDD, or if I were to get rid of Vista and install Ubuntu fresh, would it pick up all of the drivers such as WLAN, Eternet, USB Ports, Sound Card, Video Card, etc?

2) So far, I have had absolutely no major problems with Ubuntu, and I love that I can say that, however, I have had a minor problem. Whenever I switch to a new task, it seems to load very slowly. The actual program will load right away, however, the picture seems to blink a few times before I can see everything. That's really the only way I can describe it. Basically, everything lags. However, I am thinking that the only reason it lags is because of the fact that I am running this while I have Vista on my computer. My laptop meets the requirements for Wubi and Ubuntu to be able to run. If anyone needs any specs of my computer, feel free to ask which you  need, and I will gladly supply them.

---

### Post by mike555 on 2009-09-06
I suggest you dual boot , read the instructions carefully , but that way if you ever need Windows it will still be there , but you can just boot into Ubuntu most of the time ...

---

### Post by chriskin on 2009-09-06
> **Haxes said:**
> 

1) I am on the Ubuntu part of my computer as we speak. I noticed that Ubuntu automatically recognized all of my drivers for my laptop, and everything is workiing correctly. Is this because I already have Windows Vista installed to my HDD, or if I were to get rid of Vista and install Ubuntu fresh, would it pick up all of the drivers such as WLAN, Eternet, USB Ports, Sound Card, Video Card, etc?


your windows installation has definitely **nothing** to do with it
ubuntu doesn't need you to install drivers for wireless, ethernet, usb , sound cards etc
you probably have to install just the graphics card through system/administration/hardware drivers.

---

### Post by ad_267 on 2009-09-06
Ubuntu doesn't need Windows for any drivers. If you removed Windows it would run just the same. If you've installed using Wubi and you removed Windows it would also remove Ubuntu. You would have to reinstall Ubuntu by installing it to its own partition.

The lag won't be because you're running Vista, and I don't think Wubi should affect performance much. Check if there's a graphics driver you can install from System - Administration - Hardware Drivers.

---

### Post by Haxes on 2009-09-06
I'll do that, ad_267. I am currently on the Vista part of my computer, because the lag got to me.

So, inorder to install the driver for my graphics card, I just need to go to "System," "Hardware, then "Hardware Drivers."

What if I don't see my graphics card there?

EDIT: On a side note, thanks for the quick replies. I'm not quite used to getting answers so fast, and I really appreciate it.

---

### Post by ad_267 on 2009-09-06
What graphics card do you have? If it's an Nvidia card then there should be a driver listed there. If it's an ATI or Intel card then it's possible you already have the best drivers installed, the drivers for some ATI and Intel graphics chips are open source so can be distributed with Ubuntu and installed automatically.

---

### Post by Haxes on 2009-09-06
I have an NVidia. I'll reboot now and see if its there. Again, thanks for your help :)

---

### Post by Haxes on 2009-09-06
So, I did what you said and in the "Hardware Drivers" window, it says "No proprietary drivers are in use on this system." Needless to say, the lag is still here.

---

### Post by ad_267 on 2009-09-06
> **Haxes said:**
> So, I did what you said and in the "Hardware Drivers" window, it says "No proprietary drivers are in use on this system." Needless to say, the lag is still here.

So there was no list of drivers available, do you know the exact model of the video card? Also what are the other specifications for your computer, like the processor and amount of RAM. If it runs Vista OK then it should run Ubuntu no problem, I've found Ubuntu is faster than XP on most computers. I guess you could have some hardware which Ubuntu doesn't like that's causing problems though.

---

### Post by mike555 on 2009-09-06
you might want to checkout these videos  ... [http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

---

### Post by Haxes on 2009-09-06
> **ad_267 said:**
> So there was no list of drivers available, do you know the exact model of the video card? Also what are the other specifications for your computer, like the processor and amount of RAM. If it runs Vista OK then it should run Ubuntu no problem, I've found Ubuntu is faster than XP on most computers. I guess you could have some hardware which Ubuntu doesn't like that's causing problems though.

RAM: 2 GB
Processor: AMD AthIon Dual-Core QL-60 1.90 GHz
Graphics Card: NVIDIA GeForce 8200M G

---

### Post by ad_267 on 2009-09-06
That should be able to run Ubuntu no problem, although there should definitely be some Nvidia drivers available.

I'd first check that you have all the repositories enabled that you need. Go to System - Administration - Synaptic Package Manager. Then go to Settings - Repositories and check that the universe, multiverse and restricted software sources are all enabled. Then close that window and click Reload.

After that you could check the Hardware Manager again, or instead install the drivers from the Synaptic Package Manager. Search for the nvidia-glx-180 package, mark it for installation then click Apply.

---

### Post by Haxes on 2009-09-06
Okay, I will do that ASAP. I am currently finishing up a project on the vista part of my hard drive.

I have another question. If, for some reason, after doing what you just said doesn't work, do you think installing Ubuntu 9.04 using a Live CD could work? I downloaded the file earlier today, and I can make the disk at any time.

---

### Post by Chronon on 2009-09-06
> **Haxes said:**
> Okay, I will do that ASAP. I am currently finishing up a project on the vista part of my hard drive.

I have another question. If, for some reason, after doing what you just said doesn't work, do you think installing Ubuntu 9.04 using a Live CD could work? I downloaded the file earlier today, and I can make the disk at any time.

You can certainly install Ubuntu 9.04 from a Live CD, but I don't understand what that has to do with whether you are able to load proprietary drivers or not.

---

### Post by ad_267 on 2009-09-06
I don't think using the Live CD will help much. From what I've heard installing using Wubi isn't too different from installing Ubuntu on its own partition. Its more difficult to remove Ubuntu that way too. If you can't get rid of the lagging it's a lot easier to remove Ubuntu with Wubi.

If installing the Nvidia drivers doesn't help the only other thing I can think of is to try the latest alpha release of Ubuntu 9.10, the final release is due in late October. It's still pretty unstable and not meant for every day use, but with each release there's always improved hardware support.

---

### Post by Haxes on 2009-09-06
Okay. I'm actually burning the Live CD right now.

Also, Chronon, I wasn't thinking that it would fix the drivers or not, I was more thinking along the lines of it fixing the lag.

---

### Post by Haxes on 2009-09-06
ad, I did as you suggested, and while I was in Repositories, Universe, Multiverse, and Restricted Software were all selected.

I scrolled through the list, and I saw the following drivers(?) were all installed, and at their latest version:

nvidia-175-modaliases
nvidia-180-modaliases
nvidia-71-modaliases
nvidia-96-modaliases
nvidia common

Does that mean anything?

---

### Post by ad_267 on 2009-09-07
I think those modealias packages are just for detecting the model of Nvidia cards. The nvidia-glx-180 package is the one you need. The 8200M G chip is supported by that driver.

---

### Post by Haxes on 2009-09-07
Well, I tried everything you said, and the nvidia-glx-180 package never showed up. Is there any other way I can get it?

---

### Post by ad_267 on 2009-09-07
> **Haxes said:**
> Well, I tried everything you said, and the nvidia-glx-180 package never showed up. Is there any other way I can get it?

It should definitely be there. It's in the restricted repository. If you made sure that one was ticked and clicked the reload button (which updates the package list from the repositories) then it should show up. Sometimes the Quick Search does funny stuff, try clicking on the search button and search for the package by name.

You could also check the server used under Settings - Repositories. Try changing it to the main server and click reload.

Other than that you can install the drivers by downloading them from the Nvidia website, but it's not a graphical step by step installer like for Windows and is a lot more hassle.

You can also download the package from this website: [http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180), but you'd need to install these two packages first: [http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source](http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source), [http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau](http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau)

---

### Post by Haxes on 2009-09-07
Okay, thanks a lot. I'll try that in just a little bit and let you know if it works.

---

### Post by Haxes on 2009-09-07
> **ad_267 said:**
> It should definitely be there. It's in the restricted repository. If you made sure that one was ticked and clicked the reload button (which updates the package list from the repositories) then it should show up. Sometimes the Quick Search does funny stuff, try clicking on the search button and search for the package by name.

You could also check the server used under Settings - Repositories. Try changing it to the main server and click reload.

Other than that you can install the drivers by downloading them from the Nvidia website, but it's not a graphical step by step installer like for Windows and is a lot more hassle.

You can also download the package from this website: [http://packages.ubuntu.com/jaunty/nvidia-glx-180](http://packages.ubuntu.com/jaunty/nvidia-glx-180), but you'd need to install these two packages first: [http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source](http://packages.ubuntu.com/jaunty/nvidia-180-kernel-source), [http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau](http://packages.ubuntu.com/jaunty/nvidia-180-libvdpau)

Thanks a lot.

After doing everything in this post, I was finally able to get rid of the lag by checking the Hardware Drivers. I'm glad that I can finally scroll down a page on this website without it taking 2 minutes. haha.

And yes, so far, Ubuntu is MUCH faster than XP has ever been for me.

Again, thanks a lot.

---

### Post by lisati on 2009-09-07
I'd go with the "try the Live CD" suggestion. Don't forget to backup important data and make sure you've made a suitable backup of any recovery partitions on your system. If you're in luck there will be software preinstalled on your system to help with the task.

---

### Post by Haxes on 2009-09-07
I've already got Ubuntu installed using Wubi. However, I would like to uninstall it in the Windows part of my hard drive, and reinstall it with a Live CD.

I was actually just trying to do that. I was going to select the "Install them side by side, choosing between them each start up." option, however, it was not available.

According to my CD, Vista took up all 12 GB of my HDD, however, when I am on Vista, it says there are 70 GB free.

EDIT: Anyone know why the CD would say there is no space, and vista says there is 70 GB free?

---

### Post by ad_267 on 2009-09-07
> **Haxes said:**
> According to my CD, Vista took up all 12 GB of my HDD, however, when I am on Vista, it says there are 70 GB free.

You could try defragmenting your partition from Vista first and see if that helps. Also check what Gparted says from the LiveCD, which is under System - Administration - Partition Editor.

---

### Post by Haxes on 2009-09-07
> **ad_267 said:**
> You could try defragmenting your partition from Vista first and see if that helps. Also check what Gparted says from the LiveCD, which is under System - Administration - Partition Editor.

I'll defragment it tonight, and check Gparted tomorrow morning. I'm pretty tired, and will probably pass out once the defrag finishes.

---

### Post by The Cog on 2009-09-07
> **Haxes said:**
> I'll defragment it tonight, and check Gparted tomorrow morning. I'm pretty tired, and will probably pass out once the defrag finishes.

Don't confuse free space with free space.

Vista will be reporting the amount of free space within the partiton that Vista uses (probably referred to as drive C). 

However, that partition probably occupies nearly the whole disk if not all of it. The partition editor in the Ubuntu installer will be reporting free space referring to the amount of the disk that is not allocated to a partition at all. It's like looking at the wall in your house. If the whole wall is given over to bookshelf, then there is very little free wall even if the bookshelf is half empty.

The Ubuntu installation will probably involve reducing the size of the Vista partition in order to make space for the Ubuntu partitions (it normally uses two partitions for itself - system disk and a smallish swap partition). Make sure you have backups before doing this, just in case. And uninstall wubi first, to make more space for shrinking the partition.

---

### Post by Haxes on 2009-09-07
> **The Cog said:**
> Don't confuse free space with free space.

Vista will be reporting the amount of free space within the partiton that Vista uses (probably referred to as drive C). 

However, that partition probably occupies nearly the whole disk if not all of it. The partition editor in the Ubuntu installer will be reporting free space referring to the amount of the disk that is not allocated to a partition at all. It's like looking at the wall in your house. If the whole wall is given over to bookshelf, then there is very little free wall even if the bookshelf is half empty.

The Ubuntu installation will probably involve reducing the size of the Vista partition in order to make space for the Ubuntu partitions (it normally uses two partitions for itself - system disk and a smallish swap partition). Make sure you have backups before doing this, just in case. And uninstall wubi first, to make more space for shrinking the partition.

Well, earlier when I looked, the installication from the Live CD wanted me to delete the whole Vista partition. The option to install it on the same HDD as Vista wasn't even there.

Can I use Gparted to take roughly 22.5 GB from the Vista partition, and use 20GB for the System Disk, and 2.5GB for the Swap Partition?

---

### Post by davidryderuk on 2009-09-07
> 
The Ubuntu installation will probably involve reducing the size of the Vista partition in order to make space for the Ubuntu partitions

Hi,
I just wanted to add that the easiest way of resizing the vista partition is from within vista, as described in the link below.

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

Ubuntu can then install in the free space generated from shrinking your vista partition.

---

### Post by davidryderuk on 2009-09-07
You might also want to look at the following link if vista doesn't want to shrink your partition or offers to shrink it by a tiny amount.

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

If you do follow those instructions I would recommend just using the Power Defragmenter and Perfect Disk software. Don't bother with deleting all those files it suggests at the beginning of the tutorial.

---

### Post by The Cog on 2009-09-07
> **davidryderuk said:**
> Hi,
I just wanted to add that the easiest way of resizing the vista partition is from within vista, as described in the link below.


+1. This is indeed the easiest way. I had forgotten about that. 

As I said though, remove wubi first because it occupies a lot of Vistas filesytem space with its virtual disk file.

I don't think the Ubuntu installer will even offer to shrink the Vista partition if it thinks there is not enough free sapce within it to make a useful difference.

---

### Post by Bartender on 2009-09-07
> **Haxes said:**
> Well, earlier when I looked, the installication from the Live CD wanted me to delete the whole Vista partition. The option to install it on the same HDD as Vista wasn't even there.

I'm wondering if you've already got four partitions.  A lot of manufacturers have gotten into an annoying habit of sending out their products with four partitions (often all primary) already in place. This forces the user to get rid of at least one of the partitions.  If the Ubuntu install CD doesn't give you the usual options it's likely that the installer sees four partitions and doesn't know what to do.  

Go back in with the LiveCD and fire up the Partition Editor.  Count up the partitions and identify them, or post a screenshot.

---

### Post by Haxes on 2009-09-07
> **Bartender said:**
> I'm wondering if you've already got four partitions.  A lot of manufacturers have gotten into an annoying habit of sending out their products with four partitions (often all primary) already in place. This forces the user to get rid of at least one of the partitions.  If the Ubuntu install CD doesn't give you the usual options it's likely that the installer sees four partitions and doesn't know what to do.  

Go back in with the LiveCD and fire up the Partition Editor.  Count up the partitions and identify them, or post a screenshot.

I'm running the Winodws Vista Partition Shrinker thingy right now. Once I finish, if it doesn't work, I will do what you just said.

---

