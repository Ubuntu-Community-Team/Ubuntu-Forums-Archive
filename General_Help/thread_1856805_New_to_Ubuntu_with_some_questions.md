---
title: "New to Ubuntu with some questions"
date: 2011-10-08
forum: General Help
---

### Post by gbelov on 2011-10-08
Hello everyone! Decided not to create a new thread, so would appreciate it if someone helped me here.

I'm very new to Linux and Ubuntu. Had to reinstall Windows for the 100th time today (disk format and all, so a clean installation) and somehow realized it might be a great opportunity to try something new, so here I am. I downloaded Wubi and the installation process went perfect, no glitches at all, and now I am writing this from Ubuntu. Very excited and am enjoying every minute of it. Also thought Linux might be better for my pretty old laptop in terms of performance.

What surprised me the most, however, was the fact that Ubuntu seemed to have had all the necessary drivers for my configuration. Every bit of hardware just worked from the start. Amazing! 

**So my question is: **does Ubuntu really have all these drivers and stuff, or did this happen because I had already installed everything (all the drivers) on Windows? This is important because that's what's been keeping me away from Linux: having to assemble everything together, network card drivers, USB drivers, touchpad drivers, making everything work. If Ubuntu is shipped with all this stuff right out of the box, then nothing's stopping me from deleting my new Windows installation altogether and reinstalling Ubuntu properly, on a freshly formatted clean drive. 

Please help me. I'm sure the "sound" of another Windows user calling it quits and seeing the light is more than music to your ears :) 

TLDR: Does Ubuntu have all the necessary drivers, or did everything work because I had installed them on Windows? 

Thanks!

---

### Post by huggs on 2011-10-08
> **gbelov said:**
> Hello everyone! Decided not to create a new thread, so would appreciate it if someone helped me here.

I'm very new to Linux and Ubuntu. Had to reinstall Windows for the 100th time today (disk format and all, so a clean installation) and somehow realized it might be a great opportunity to try something new, so here I am. I downloaded Wubi and the installation process went perfect, no glitches at all, and now I am writing this from Ubuntu. Very excited and am enjoying every minute of it. Also thought Linux might be better for my pretty old laptop in terms of performance.

What surprised me the most, however, was the fact that Ubuntu seemed to have had all the necessary drivers for my configuration. Every bit of hardware just worked from the start. Amazing! 

**So my question is: **does Ubuntu really have all these drivers and stuff, or did this happen because I had already installed everything (all the drivers) on Windows? This is important because that's what's been keeping me away from Linux: having to assemble everything together, network card drivers, USB drivers, touchpad drivers, making everything work. If Ubuntu is shipped with all this stuff right out of the box, then nothing's stopping me from deleting my new Windows installation altogether and reinstalling Ubuntu properly, on a freshly formatted clean drive. 

Please help me. I'm sure the "sound" of another Windows user calling it quits and seeing the light is more than music to your ears :) 

TLDR: Does Ubuntu have all the necessary drivers, or did everything work because I had installed them on Windows? 

Thanks!

Has nothing to do with Windows, Ubuntu just works :P
Well, 99% of the time, the other 1% of the time, you google your problem, and 99% of the time you find the solution because somebody else had the same problem already.
The other 1% of he time, you come here, and ask for help, and some really nice folks will help you sort your problem. Welcome to Ubuntu :P

---

### Post by bcbc on 2011-10-08
+1 ubuntu installed through wubi is totally separate from windows. Installing windows without drivers is like pulling teeth, but Ubuntu just works (and the fact that it fits on one CD is pretty amazing).

---

### Post by gbelov on 2011-10-08
> **bcbc said:**
> +1 ubuntu installed through wubi is totally separate from windows. Installing windows without drivers is like pulling teeth, but Ubuntu just works (and the fact that it fits on one CD is pretty amazing).

Thanks guys! Already had the GRUB problem, though, but should have known better. Other than that, everything's smooth. Got me thinking, though, are there any other pitfalls like the GRUB one that I should be aware of? I'm a pretty advanced user on Windows and am a hobbyist programmer, but Linux is totally uncharted territory for me. I'm planning on reading a proper book on that, but for the time being is there like a starter manual or something, on how to deal with Linux? I've browsed through all the settings already, so that's fine, but the file system, for instance, is totally new to me. Where do all the programs and stuff I download actually go to? Sorry for piling everything up in here...

---

### Post by bcbc on 2011-10-08
> **gbelov said:**
> Thanks guys! Already had the GRUB problem, though, but should have known better. Other than that, everything's smooth. Got me thinking, though, are there any other pitfalls like the GRUB one that I should be aware of? I'm a pretty advanced user on Windows and am a hobbyist programmer, but Linux is totally uncharted territory for me. I'm planning on reading a proper book on that, but for the time being is there like a starter manual or something, on how to deal with Linux? I've browsed through all the settings already, so that's fine, but the file system, for instance, is totally new to me. Where do all the programs and stuff I download actually go to? Sorry for piling everything up in here...

**_The_** grub problem? 

For where programs and other things are stored: [http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard#Directory_structure)

For everything else you download: cd ~/Downloads (~/ = your home directory)

Programming: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by Rubi1200 on 2011-10-09
Hi and welcome to the forums gbelov :)

I have moved your post and those that followed into a new thread.

The Wubi Megathread is a place to post for users who have specific problems with their Wubi installs not for general comments and questions.

In future, please start your own thread for support requests, comments etc.

Thanks for understanding.

---

### Post by fixerdave on 2011-10-09
If you're used to XP then Ubuntu will amaze you, but then it's a much more modern operating system.  Gone are the days of the great XP driver hunt; you just don't have to do that any more.  If you compare Ubuntu to something like Win7, then it's much more fair... both are modern and both have advantages, but XP is a historical artefact.

Personally, I'm paid to install Win7 but I run Ubuntu at home, and on any system anyone asks me to install. It's just better - especially from an install point of view.  This is because it's 'free'.  I mean 'free' as in free speech, not necessarily free beer.  Basically, you don't have to click through endless EULAs to install anything and that makes the whole install process go so, so much faster.  With both Ubuntu and Win7, it takes about the same amount of time from start to fully patched system.  But, what you get with Ubuntu is an OS AND all the generally used apps.  Those apps will kill you in Win7 (or XP) because you have to hit "OK" over, and, over, and over again.  If you have a standard install suite in Ubuntu, it would be a trivial matter to script a bunch of 'sudo apt-get install... ' lines to install everything unattended.  That's what 'free' give you, no EULAs.  It is so much less effort to install.

I'm not quite as rave about compatibility... I've run into more than a few Linux HW issues.  But, if it works with a liveCD, it will likely work.  If it won't, then maybe there's a quick solution.  If not, honestly, I'm not going to fight to the death to get a particular OS going.  It sounds like you have the right HW to make life easy.  I'd go for it.

If you are an expert in Windows, the switch can be frustrating.  I can't say how many times I've known how to do something in Windows but struggled for hours in Linux until I figured it out.  These days, I'm over the steepest part of the learning curve and, well, I'd never go back.  I mean, I'm glad Windows exists as it's a great career opportunity, but I'll never go back at home.

   David...

---

### Post by claracc on 2011-10-09
Well, you can get familiar to ubuntu with the wubi installation, although it is only a temporary solution.

But if you want to be sure your hardware is ubuntu compatible it's better you burn a live CD with the current ubuntu release, boot your computer from it and play with the OS without installing it.

In this way, you can see if ubuntu driver's work well in your hardware.

Then, you can decide to install it along side your win os (dual boot) or wipe the entire HD and install only ubuntu (if it is enough for you).

---

### Post by drofart on 2011-10-09
> **gbelov said:**
> Hello everyone! Decided not to create a new thread, so would appreciate it if someone helped me here.

I'm very new to Linux and Ubuntu. Had to reinstall Windows for the 100th time today (disk format and all, so a clean installation) and somehow realized it might be a great opportunity to try something new, so here I am. I downloaded Wubi and the installation process went perfect, no glitches at all, and now I am writing this from Ubuntu. Very excited and am enjoying every minute of it. Also thought Linux might be better for my pretty old laptop in terms of performance.

What surprised me the most, however, was the fact that Ubuntu seemed to have had all the necessary drivers for my configuration. Every bit of hardware just worked from the start. Amazing! 

**So my question is: **does Ubuntu really have all these drivers and stuff, or did this happen because I had already installed everything (all the drivers) on Windows? This is important because that's what's been keeping me away from Linux: having to assemble everything together, network card drivers, USB drivers, touchpad drivers, making everything work. If Ubuntu is shipped with all this stuff right out of the box, then nothing's stopping me from deleting my new Windows installation altogether and reinstalling Ubuntu properly, on a freshly formatted clean drive. 

Please help me. I'm sure the "sound" of another Windows user calling it quits and seeing the light is more than music to your ears :) 

TLDR: Does Ubuntu have all the necessary drivers, or did everything work because I had installed them on Windows? 

Thanks!
For easy understanding just think of windows 7 ,dose u install any extra driver? Every thing pre loaded, you don't have to worry about driver wit linux except unsupported device like nvidia video card  etc.
[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)

---

### Post by robert shearer on 2011-10-09
Ubuntu guides...
[https://wiki.ubuntu.com/ubuntu-manual](https://wiki.ubuntu.com/ubuntu-manual)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://ubuntuguide.org/wiki/Ubuntu:Natty](http://ubuntuguide.org/wiki/Ubuntu:Natty)
[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

---

### Post by coldraven on 2011-10-09
Greetings :)
My advice is to download a Live Desktop CD from here [http://releases.ubuntu.com/](http://releases.ubuntu.com/)
I have found that the torrents are best for speed, also you can download over several days if your connection is intermittent.
Install Ubuntu on the entire disc 

Then download VirtualBox from here [URL="https://www.virtualbox.org/"]https://www.virtualbox.org/
[/URL]Create a virtual machine with your Windows disc. Then you can make a backup of it by using the "Export" function, it does not take as long as it will first report. It may say 2hrs but actually takes about 15mins.
You can create "snapshots" of your Virtual machine before installing software which may break it.
For experimenting with other OSs you can make more virtual machines. Some ready made ones can be found here [URL="http://virtualboxes.org/images/"]http://virtualboxes.org/images/
[/URL]Have fun!

---

### Post by fixerdave on 2011-10-09
> **gbelov said:**
> ...What surprised me the most, however, was the fact that Ubuntu seemed to have had all the necessary drivers for my configuration. Every bit of hardware just worked from the start. Amazing! 

**So my question is: **does Ubuntu really have all these drivers and stuff, or did this happen because I had already installed everything (all the drivers) on Windows?...

TLDR: Does Ubuntu have all the necessary drivers, or did everything work because I had installed them on Windows? ...

To specifically answer your question, according to Wikipedia:
"The advantage of this setup (Wubi) is that users can test the operating system and install the drivers before they install it to a dedicated partition."

In other words, Wubi is virualising the drive and not much else.  So, if the HW is working, then it's working under Ubuntu.

Oh, and don't forget that there's Ubuntu, Kubuntu (KDE desktop), Xubuntu (lighter version), and even Lubuntu (lighter still, but unofficial).  There are others.  It's all about choice...

---

