---
title: "Newcomer needs advice"
date: 2009-08-21
forum: General Help
---

### Post by smeet on 2009-08-21
Hi. 
I am a complete newcomer to the ubuntu forum and need some good, sound advice.
I am currently running Vista on my laptop and have been thinking of switching to ubuntu. I am not a computer geek so, before I make the switch, please help with the following questions:
1. Which version of ubuntu is recommended for laptops?
2. Can it be run alongside vista or must vista be removed once ubuntu has been installed?
3. How easy is it to install? Are there any tricks or pitfalls?
4. I have a number of windows based applications for video, photo editing, GPS etc plus the usual microsoft office applications. Will these run in ubuntu?
 
This is just a start. I am sure that I will have many more questions once I get started.
 
Thanks.

---

### Post by howefield on 2009-08-21
> **smeet said:**
> 
1. Which version of ubuntu is recommended for laptops?
2. Can it be run alongside vista or must vista be removed once ubuntu has been installed?
3. How easy is it to install? Are there any tricks or pitfalls?
4. I have a number of windows based applications for video, photo editing, GPS etc plus the usual microsoft office applications. Will these run in ubuntu?

1. Desktop verion, current is 9.04.

2. Yes it can be run alongside vista and this is probably the best thing to do until(if) you get to a position where you don't want vista.

3. Very easy assuming your hardware is compatible. There is more work once you have installed Ubuntu, configuring things like multimedia, flash, drivers, whatever.

4. Maybe, you can use wine to run certain windows programs, some will run better than others. Some not at all. You can also virtualise windows, basically allowing you to run both operating systems simultaneously.  

Another option is to consider installing with Wubi, this installs Ubuntu within windows and gives you the choice of operating system to boot at startup, the benefit being you can uninstall via add/remove programs.

---

### Post by gldearman on 2009-08-21
1) A full-power laptop (as opposed to a netbook) capable of running Vista should be able to run any version of Ubuntu without problem.  I'd go with Ubuntu 9.04 (the latest) unless you know in advance that you would prefer the KDE desktop.  If you're a newbie, though, just go with the latest version of the main release.

(Remember, you can run from the LiveCD to check it out before installing!)

2) You do not have to uninstall Vista.  Both can be installed at once, and you can pick one when booting.

3) I have heard many people say that the easiest way for a newbie to install is with [wubi]("http://wubi-installer.org/").  That should help with tricks and pitfalls.  Though, I won't lie, getting your wireless and video cards working properly may be tricky, too.  Come back and post specific questions if you have problems.

4) For office software, MS Office works on Ubuntu under WINE (a Windows Emulator), but Open Office comes with Ubuntu and is better than MS Office.  The Gimp is much like Photoshop, and comes preinstalled.  If you need the full power of Photoshop, it works under WINE as well (Adobe works very hard to make sure of that).  I can't tell you about GPS or video editing, but if you do a lot of media editing, maybe you should check out Ubuntu Media edition.

---

### Post by P4man on 2009-08-21
what everyone else said, except:

> 4. I have a number of windows based applications for video, photo editing, GPS etc plus the usual microsoft office applications. Will these run in ubuntu?

Photo editing, there is gimp, just like the previous poster said, but prepare for a bit of time to get used to it. Its every bit as powerful as photoshop, but if you're a photoshop user, you will feel quite lost for some time!

Video editing has been a sore point on linux for a long time. To some extend it still is. There are hugely expensive professional apps, but  for consumer grade (which in the linux world typically means free) apps, there is not nearly the wealth of options you have on windows. Kdenlive is probably your best best:
[http://www.kdenlive.org/](http://www.kdenlive.org/)

For office, use open office, installed by default. I wouldn't go as far as saying its superior to MS office, but its more than good enough for 99% of us.

In general, try finding native linux programs for the tasks you want to accomplish, and as a last resort, you can try running windows apps under wine or on a virtual machine. But that should be the exception, not the rule. Linux is not Windows, its not better at running windows apps, its a small miracle it can run some at all. Linux is far superior at running linux apps though :)

---

### Post by smeet on 2009-08-21
Thanks al lot, Howefield, gldearman and p4man. I will let you know how I get along in a day or two.
:?

---

### Post by gldearman on 2009-08-21
> **P4man said:**
> what everyone else said, except:

Photo editing, there is gimp ... Its every bit as powerful as photoshop ...

For office, use open office, installed by default. I wouldn't go as far as saying its superior to MS office, but its more than good enough for 99% of us...

Wow.  I would have said that in reverse.  I'd say Gimp is not as powerful as Photoshop, but good enough for 99% of us.  On the other hand, I'd say Open Office is superior to MS Office in almost every respect. :lol:

That's perspective for you!  Different users use programs different ways, so they see different strengths and weaknesses in them.

Good luck, smeet!

---

### Post by TrakerJon on 2009-08-21
> **smeet said:**
> Hi. 
I am a complete newcomer to the ubuntu forum and need some good, sound advice.
I am currently running Vista on my laptop and have been thinking of switching to ubuntu. I am not a computer geek so, before I make the switch, please help with the following questions:
1. Which version of ubuntu is recommended for laptops?
2. Can it be run alongside vista or must vista be removed once ubuntu has been installed?
3. How easy is it to install? Are there any tricks or pitfalls?
4. I have a number of windows based applications for video, photo editing, GPS etc plus the usual microsoft office applications. Will these run in ubuntu?
 
This is just a start. I am sure that I will have many more questions once I get started.
 
Thanks.
 
1. The current 9.04 is the best so far.
2. I strongly recommend that you partition your drive with something like partition manager [http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html ]("http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html") and install Ubuntu on a newly created drive. Then if you have problems it's much easier to remove Ubuntu. Note: If you remove Ubuntu refer to FixMbr or FixBoot as needed [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392") with your Vista disk handy...I can help as well.
3. The key is paying attention at each prompt/window, again I recommend creating a drive specifically for Ubuntu, 20Gb is plenty.
4. Visit my post once you get Ubuntu up and running, if you have questions feel free to ask...[http://ubuntuforums.org/showthread.php?t=1181327]("http://ubuntuforums.org/showthread.php?t=1181327")

---

### Post by decoherence on 2009-08-21
> 3. How easy is it to install? Are there any tricks or pitfalls?

As was previously said, it depends on how well your hardware it supported. Once you've downloaded and burned the Ubuntu CD, you can use it to boot your computer in to a live system. The main things to check for are whether video works (this should be easy to tell!) sound works (System > Preferences > Sound... then click one of the test buttons) and networking. wired networking is pretty solid but wireless can be hairy. It is controlled through the NetworkManager icon in the upper panel near the right side. It looks like two screens, one on top of the other. Or a wall socket with a cable, if you're plugged in to ethernet.

If all these things work for you, you're laughing. Otherwise, get some more information before you go with Ubuntu. Could be things will work properly with another distro or a Long Term Support version of Ubuntu.

---

### Post by linux_tech on 2009-08-21
This may be helpful to setup dual boot system.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by P4man on 2009-08-21
> **linux_tech said:**
> This may be helpful to setup dual boot system.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Hmm don't like that link much.They let you chose "install" in the ubuntu live cd menu. Makes a lot more sense to use the "try ubuntu" option so you can test stuff first, and then click install when you're ready (and surf the web or play a game while it installs).

Then it seems they suggest using "manual" as partitioning option, yet the screenshot shows a "use whole disk" scenerio and they dont explain how to manually set up partitions.

Lastly, you can just as well let the installer (or gparted actually) manage the whole partitioning and resizing stuff. It might be a bit slower than doing the preparation under vista, but its certainly not more complicated and its less prone to error.

My 2 cents..

---

### Post by steveneddy on 2009-08-21
My two cents:

I would not recommend Wubi unless you are just using it to just try out Ubuntu to see how it looked and feels.

What I recommend doing to really get a good feel for the OS and still be able to use all of the features is to use a vurtual machine, like VirtualBox.

VirtualBox is a free software that installs on your Windows machine and you install and run Ubuntu, or any other operating system for that matter, and you don't have to mess with dual booting or the crappy Wubi software.

I think you would be much happier with a VM and would still get the full benefit of installation without the hassles of dual booting for someone who may be slightly inexperienced.
[URL="http://www.virtualbox.org/wiki/Downloads"]
Use version 3.0 of VirtualBox.[/URL] Link only goes to the download page, not to the download directly.

Please read the instructions and the manual before installation and make sure you have a good grasp on what you are doing before you dive into this.

Good luck. Post back with your results.

---

### Post by smeet on 2009-08-22
Gosh, I never thought I would get so many useful replies. I'm not sure if I am better informed or more confused, but thanks to all.
I have down loaded Ubuntu 9.04 off the web and burned it to disk. I see that the file type is shown as MPlayer Video File. Is this correct?

---

### Post by DeMus on 2009-08-22
Look here for open source software which is equivalent to Windows software: [_Equivalent_Software_]("http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software")

---

### Post by XxionxX on 2009-08-22
I made this switch just recently, and although I occasionally wander back to windows I do so less and less often. I have the feeling that one day I won't return at all. There are the occasional snags that I have experienced but nothing that really bothered me because everyone on the forums has been so helpful. I think that all of the problems that I am having are a result of just getting used to the new "groove" of things. I feel more at home every time I find a new feature. I feel even more at home when I have a problem because everyone on the forums comes running with advice. I won't say that the transition is easy (I gave up twice on other distros before I finally just made the leap) but it is rewarding in some strange way. The Linux thing is not for everyone (yet) but for those who can handle the hiccups of the transition it is the best thing since sliced bread.

---

### Post by P4man on 2009-08-22
> **smeet said:**
> Gosh, I never thought I would get so many useful replies. I'm not sure if I am better informed or more confused, but thanks to all.
I have down loaded Ubuntu 9.04 off the web and burned it to disk. I see that the file type is shown as MPlayer Video File. Is this correct?

No. Its an ISO cd image. You have to burn it to cd. You need a program for that in windows. here is an extensive how to:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

As for all the contradicting replies. Heh. I can imagine you are confused. No one is right or wrong though, just opinions and choices. You'll find you have many of those in the linux world :D

---

