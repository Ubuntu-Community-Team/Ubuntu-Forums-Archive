---
title: "General questions about Linux"
date: 2009-08-22
forum: General Help
---

### Post by dcs.79c on 2009-08-22
Does Linux have an equivalent to Windows BSOD? If what happens in Windows that causes a BSOD should happen in Linux, what happens?
 
Why does Linux require a separate partition for the swap file? Is it required or is it optional? I know that Windows has the option of putting a swap file on a separate partition.
 
Vista has a neat feature called dynamic disk. I know that Linux doesn't use drive letters. Does Linux have "dynamic disk"? Can one combine 2 or more physical disks in Linux to equal 1 dynamic disk?
 
I want to build a PC & I'm intrigued by VMware's workstation. I have 2 choices for the host OS, Windows or Linux. I have Vista on my laptop & it has BSOD'd more than once. If I'm going to have both Linux & Vista on my PC, I want a stable OS that doesn't lock up & BSOD.
 
How do I add more than 1 GUI? I'd like to be able to switch between Gnome, KDE & XFCE.
 
Thank you.
David

---

### Post by ibutho on 2009-08-22
Swap is a space for virtual memory. Whether or not you need it depends on the amount of ram you have and how you use your computer. For combining multiple disks or partitions to appear as one, look into Logical Volume Management (LVM). To add another DE on ubuntu just install the metapackage you need e.g. ubuntu-desktop for Ubuntu's GNOME based desktop, xubuntu-desktop for Ubuntus XFCE based desktop and kubuntu-desktop for Ubuntus KDE based desktop.

---

### Post by sasho_zl on 2009-08-22
First of all Linux has NOTHING  in common with windows. The so called BSOD in windows appears because the system is not well build and if one thing crashes it takes everything down with it! In Linux the situation is different. In Linux even if the graphical user interface encounters a serious problem he can stop working but the Linux system will be fully operational in the background and you can restore the interface with a few commands. This is one of the reason why the Gnu/Linux based servers run most of the mission critical online operations in the world! 
I would recommend to you to read some books about Linux so you can clear your head from the windows things and hopefully in time you will look back and laugh at your self that you have wasted so much time dealing with a system like windows (that is my case).

---

### Post by RJ12 on 2009-08-22
Actually Linux does have a BSOD but most of the time its at startup its called a Kernel Panic its not Blue though and usually the keyboard lights flash and I have never encountered one except when trying to install OSX86 in Vmware.
About the Host it depends what you will need to use Vista for. What do you need vista for? I Love Linux and try to get everyone I know to atleast try the Live CD and Hopefully Linux will never be like Windows the only thing like windows on linux is Linux XP (I hate that they tried to sell Linux they even made the Linux Genuine Advantage!)

---

### Post by Nburnes on 2009-08-22
> **dcs.79c said:**
> Does Linux have an equivalent to Windows BSOD? If what happens in Windows that causes a BSOD should happen in Linux, what happens? **Kernel Panic, but very rarely.**
 
Why does Linux require a separate partition for the swap file? Is it required or is it optional? I know that Windows has the option of putting a swap file on a separate partition.** When you install Ubuntu it will give itself a swap partition based on the amount of RAM you have.**
 
Vista has a neat feature called dynamic disk. I know that Linux doesn't use drive letters. Does Linux have "dynamic disk"? Can one combine 2 or more physical disks in Linux to equal 1 dynamic disk? **Look up Logical Volume Management.**
 
I want to build a PC & I'm intrigued by VMware's workstation. I have 2 choices for the host OS, Windows or Linux. I have Vista on my laptop & it has BSOD'd more than once. If I'm going to have both Linux & Vista on my PC, I want a stable OS that doesn't lock up & BSOD. **Ubuntu is a stable OS, and if you looking for Superb Stability look into one of the LTS versions.**
 
How do I add more than 1 GUI? I'd like to be able to switch between Gnome, KDE & XFCE. **Yes you can add more than one desktop. Quite easily actually.**
Thank you.
David

Reply in Bold.

---

### Post by dcs.79c on 2009-08-22
**About the Host it depends what you will need to use Vista for. What do you need Vista for?**
 
I know that there are a lot of programs for Linux, but there are some programs that I have that only run on Windows.
 
**The so called BSOD in windows appears because the system is not well build and if one thing crashes it takes everything down with it! In Linux the situation is different. In Linux even if the graphical user interface encounters a serious problem he can stop working but the Linux system will be fully operational in the background and you can restore the interface with a few commands.**
 
I assume that you mean DOS commands?
 
**To add another DE on ubuntu just install the metapackage you need e.g. ubuntu-desktop for Ubuntu's GNOME based desktop, xubuntu-desktop for Ubuntus XFCE based desktop and kubuntu-desktop for Ubuntus KDE based desktop.**
 
From where do I download the DE's?

---

### Post by RJ12 on 2009-08-22
> **dcs.79c said:**
> **About the Host it depends what you will need to use Vista for. What do you need Vista for?**
 
I know that there are a lot of programs for Linux, but there are some programs that I have that only run on Windows.
 
**The so called BSOD in windows appears because the system is not well build and if one thing crashes it takes everything down with it! In Linux the situation is different. In Linux even if the graphical user interface encounters a serious problem he can stop working but the Linux system will be fully operational in the background and you can restore the interface with a few commands.**
 
I assume that you mean DOS commands?
 
**To add another DE on ubuntu just install the metapackage you need e.g. ubuntu-desktop for Ubuntu's GNOME based desktop, xubuntu-desktop for Ubuntus XFCE based desktop and kubuntu-desktop for Ubuntus KDE based desktop.**
 
From where do I download the DE's?
DE are Downloaded from The Add/Remove or Synaptic or go into terminal and type I think sudo apt-get install whatever de-desktop
And when I said what do you need vista for what program do you need to use

---

### Post by P4man on 2009-08-22
> **dcs.79c said:**
> 
I know that there are a lot of programs for Linux, but there are some programs that I have that only run on Windows.

Those programs, if they don't have a functional equivalent linux alternative, may or may not run using WINE "windows emulation". You can look them up in winehq database:

[http://www.winehq.org/](http://www.winehq.org/)

> I assume that you mean DOS commands?

Its definitely not DOS, but to a layman, it looks a lot like dos, because its a command line. Its.. well, very much more powerful than dos though.

That said, I'd like to disagree somewhat with some of the above posters about BSOD and linux stability. Linux is extremely stable if your hardware is properly supported. **But** if you're unlucky and you have for instance, a crappy ACPI Bios which only works properly with windows, then you may have more freezes than you ever had under windows 3.1. Its not Linux fault, but thats a moot point when you face it, and in those circumstances, i sometimes wished linux had a "BSOD" rather than blinking keyboard leds which dont help at all solving the issue.

> From where do I download the DE's?

Like most things you'll download/install on ubuntu, its in the so called repositories. You can download it through a graphical program called synaptic package manager, or through "DOS commands" *cough* which is the preferred way to post here, as its much easier to type "sudo apt-get install kubuntu-desktop" (which btw, will install KDE) then guiding you through synaptic. But both work.

---

### Post by Shazaam on 2009-08-22
/swap is actually a PARTITION not a file. But you can make a swap file and do away with the /swap partition. I haven't tried it yet so I can't recommend it.
[http://linux.com/news/software/applications/8208-all-about-linux-swap-space](http://linux.com/news/software/applications/8208-all-about-linux-swap-space)

---

### Post by P4man on 2009-08-22
> **Shazaam said:**
> /swap is actually a PARTITION not a file. But you can make a swap file and do away with the /swap partition. I haven't tried it yet so I can't recommend it.
[http://linux.com/news/software/applications/8208-all-about-linux-swap-space](http://linux.com/news/software/applications/8208-all-about-linux-swap-space)

I did try it, and it works equally well :)
a small advantage of a swap partition is that you can easily share it among different linux installs.

That said, if you have 2GB ram or more, you probably wont ever need a swap. Unless you want to use suspend to disk, but tbh, that is so shamefully slow on ubuntu I wonder if anyone ever bothers.

---

### Post by earthpigg on 2009-08-22
> **P4man said:**
> I did try it, and it works equally well :)
a small advantage of a swap partition is that you can easily share it among different linux installs.

That said, if you have 2GB ram or more, you probably wont ever need a swap. Unless you want to use suspend to disk, but tbh, that is so shamefully slow on ubuntu I wonder if anyone ever bothers.

he said he would be using virtual machines... in your case, OP, i suggest creating a swap partition to be safe unless you are really short on hard drive space.

keep in mind that, swap or no, linux will never let you fill a linux partition past about 95% full. that is the price we pay for never needing to defrag.

if you are looking at VM software, i submit VirtualBox for your consideration. there is a handicapped 'open source edition' in the ubuntu software repositories, or you can download the functionally superior closed source edition from [http://www.virtualbox.org/](http://www.virtualbox.org/). its made by Sun Microsystems. use VMware if you like, but be aware that -- since most people on this forum use VBox -- that is what you will get the best ubuntuforums.org support for.

if absolute stability is very important to you, i will put a few options available to you below - in order from *least stable*, to *most stable*:

1. current release of Ubuntu. right now, this is 9.04.
2. current *long term release* of Ubuntu that is at least a year old. as of the 4th month of 2009, this is 8.04. (8.04 was released the _4_th month of 200_8_.)
3. Debian Stable. Ubuntu is based on Debian, but they only release about 3 times a decade (compared to Ubuntu's twice a year). older stuff in the software repositories, but generally the ultimate in 'tried and true'. from purely a *_stability_* point of  view, and to use a horrible horrible comparison that will make many others in this forum cringe, this is like XP sp3. it will never have the flashiest or newest features, but it _*works*_.


keep in mind that google and wikipedia have some fairly mission critical linux boxes: most of google's stuff, and all of wikipedia are completely reliant on Ubuntu. *they* consider options 1 and 2 above to be stable enough for those mission critical tasks. but maybe your needs for stability are greater than theirs (for example, if you cannot back up your data), i do not know.

---

### Post by dcs.79c on 2009-08-23
Please be patient with me. As you can tell, I'm a Linux newbie. I have more questions.

Is there a Linux equivalent to Windows Device Manager?

What about motherboard chipset drivers? Do Linux drivers come on the CD that comes with the motherboard?

I'm sure that popular hardware would have Linux drivers. Like, I'm sure that ATI & Nvidia have Linux drivers.

There are so many virtual software programs. Do you know anything about Win4Lin or VirtualBox? I want a simple to understand program. How do Win4Lin, VirtualBox & VMWare Workstation compare?

I'm going to save all of this in a text file.

I read in Wikipedia that if Windows detects that it is running in Wine, it won't allow Updates, so Wine wouldn't be my first choice for a dual-boot system.
Thank you.
David

---

### Post by michy99 on 2009-08-23
> **dcs.79c said:**
> I read in Wikipedia that if Windows detects that it is running in Wine, it won't allow Updates, so Wine wouldn't be my first choice for a dual-boot system.
Thank you.
David

You don't run Windows in Wine, you run Windows programs in Wine.

---

### Post by P4man on 2009-08-23
> **dcs.79c said:**
> Please be patient with me. As you can tell, I'm a Linux newbie. I have more questions.

Is there a Linux equivalent to Windows Device Manager?

not something directly comparable.. A few things that resemble it though. Depending what you want to do. If you want to see what hardware you're running,  lspci and lsusb will show you in great detail.  Or if you want that in a gui there is "sysinfo".
> 
What about motherboard chipset drivers? Do Linux drivers come on the CD that comes with the motherboard?

Typically linux drivers are already in the kernel. Not only for popular hardware, even for a lot of exotic stuff. With the exception of videocards, there is good chance you'll never need a driver. Which is good, because if the driver is not in the kernel, things can quickly become difficult for a new user.

> 
I'm sure that popular hardware would have Linux drivers. Like, I'm sure that ATI & Nvidia have Linux drivers.


They need to. videocards is a special case, because ATI and nVidia refuse to give documentation how their chips work. (AMD did disclose this, but only for older videocards). So the linux community can't build good drivers (except for older ATI hardware). Luckily both nvidia and ATI (as well as intel) have pretty decent linux drivers now. But they are "closed source", and therefore, not supported by anyone except the vendors.

> There are so many virtual software programs. Do you know anything about Win4Lin or VirtualBox? I want a simple to understand program. How do Win4Lin, VirtualBox & VMWare Workstation compare?

VirtualBox is an excellent choice. Its powerful, very easy to use, good support. Should be your first choice on ubuntu, unless you'd have particular needs warranting something else.

> I read in Wikipedia that if Windows detects that it is running in Wine, it won't allow Updates, so Wine wouldn't be my first choice for a dual-boot system.


Dont believe everything you read on wikipedia :p. But you are confusing a few things. Dual boot is when you have one parition (or harddisk) dedicated to windows, and another to Linux. They won't interfere with each other, you can boot one or the other. This will not impact windows or its ability to update in any way.

Then there is the virtual machines. A VM is a program that emulates an entire computer. on that virtual computer, which runs as an application, you can install an operating system, like for instance windows. If you do that, you can have windows boot in a window on ubuntu (or vice versa). This has some limitations, most notably performance, and 3D video acceleration, but works very well otherwise. Windows will also do updates, assuming you have a legal copy of windows that you install on the VM.

Then there is wine. Wine is a windows emulator for linux. It will let you run many windows applications under linux, including a fair amount of (3D) games. It doesnt emulate an entire computer, it just creates an environment for windows applications. Updating windows is a moot point here, as there is no windows. You also dont need a windows licence for this.

Hope this clarifies a bit.

---

### Post by P4man on 2009-08-23
afterthought about "windows updating". perhaps what you read, is if you have a normal windows licence, and you also install that in a VM, you will need to activate windows again.As far as windows is concenred, the VM is another computer. AFAIK, you are not allowed to install the same windows licence on your harddisk and in a VM. You'd need second licence for that. When you run an unlicenced copy, updating becomes a problem, unless you apply a "crack" to it, which isnt legal, but does work.

So basically for running windows on a VM you have the choice between giving up dual boot (no more native windows), or an illegal crack, or buying another copy or licence.

Im no expert in windows licensing though, so perhaps Im wrong, if so someone will hopefully correct me :)

---

### Post by scorp123 on 2009-08-23
> **dcs.79c said:**
> Does Linux have an equivalent to Windows BSOD? Only as screensaver :)

```
sudo apt-get install xscreensaver-data-extra
```

Then go into your settings and select "BSOD" as screensaver. There are several "screens of death" from various OS in there, not just from Windows. So you'd also get to see AMIGA bombs, ATARI guru meditations, IBM AIX crashes, HP-UX crashes, Solaris and Linux kernel panics ... It's fun to watch ... and deeply satisfying to know that you can make that horrible crash message go away by just moving your mouse a little :D

---

### Post by dcs.79c on 2009-08-23
A previous post mentioned that the drivers are in the kernel. Can you be more specific? What kinds of drivers? How is the kernel updated? Can it be updated from within Linux or must one use DOS mode?

I know that a lot of programs are available for Linux, but, unfortunately, I can't walk into a store & walk out with Linux software. Or can I? I suppose that the only source for Linux software is the internet. What are good websites for obtaining Linux software?

Thank you.
David

---

### Post by sasho_zl on 2009-08-23
Almost all of the linux software you will ever need is uploaded in the online repositories. Just use synaptic package manager.

---

### Post by P4man on 2009-08-23
> **dcs.79c said:**
> A previous post mentioned that the drivers are in the kernel. Can you be more specific? What kinds of drivers? 

You dont want to know. You dont have to know :)
All you need to know is that without having to hunt for drivers, the vast majority of motherboards, mice, monitors, printers, scanners, webcams, network cards, wifi cards, soundcards, etc.. will just work.
> 
How is the kernel updated? Can it be updated from within Linux or must one use DOS mode?

Its updated the same way everything else is updated in ubuntu: repositories. Its a bit like windows update if you like, except it doesn't only update your OS, but also all installed applications.  And there is no DOS mode, but if you're wondering if all this works with graphical interface, then the answer is yes.

> I know that a lot of programs are available for Linux, but, unfortunately, I can't walk into a store & walk out with Linux software. Or can I? I suppose that the only source for Linux software is the internet. What are good websites for obtaining Linux software?

Best "website" is the ubuntu repository. You install apps, just by going in the main menu > applications > add/remove. There you can browse a huge library of (free!) applications, all of which will install (or uninstall) just by checking a box and clicking "ok".

Here, you may want to read this:

[https://help.ubuntu.com/9.04/add-applications/C/index.html](https://help.ubuntu.com/9.04/add-applications/C/index.html)

There is commercial software for linux too, which you can buy, but its not likely you'll ever need anything commercial. In most cases, the commercial packages are pretty similar to the free ones, but with added support. Star Office comes to mind, which is basically the same as Open Office.

---

### Post by dcs.79c on 2009-08-23
Well, needless to say, I'm intrigued by Linux, but I have a lot more to learn. I'll have to get more books on Linux.

Thank you.
David

---

### Post by sasho_zl on 2009-08-23
The Ubuntu beginners guide is a good choice for starters. You can download it for free through here - [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

Also good books are the "Ubuntu linux bible" and How to do everything Ubuntu".

---

### Post by dcs.79c on 2009-08-23
I downloaded the PDF version of the beginners guide. I have some Barnes & Noble gift cards. I can spend them on Linux books. I really would like to "wean" myself from Windows & use Linux exclusively.

Thank you.
David

---

### Post by P4man on 2009-08-23
well.. rather than spending a lot of time reading and researching, the best way to learn linux is play with it. Just download the ubuntu cd, and you can run it straight from the cd without even installing it (or better, run it from a USB stick).

That way, you get a feel for it, you can test things, and you'll face lots of questions anyway, and* then* you can start reading and doing research and trying to solve your problems to test stuff and learn that way.

It really isnt a good idea to get to the point where you have decided to switch 100% to linux without ever having tried it. FWIW, I dual booted for 2 years or so before I was able and willing to give up my windows. I learned a TON in those 2 years, but if I had deleted my windows partition and thrown away my cd on day 1, I would have ran back to the shop for a copy of windows  :)

---

### Post by oldos2er on 2009-08-23
Get a copy of the LiveCD ([http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)), and run it. You can check out Ubuntu without having to install it. Dead-tree books become outdated very quickly.

 You might also want to read [http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

### Post by scorp123 on 2009-08-24
> **dcs.79c said:**
> A previous post mentioned that the drivers are in the kernel. "drivers" is Windows slang. Here they're called "kernel modules" which describes exactly what and where they are. But to use your slang: Yes, (almost) all drivers are already in the kernel. No need to hunt for anything. With the exception of a few proprietary pieces of hardware (NVidia cards, ATI cards, a few WLAN chipsets ...) more or less any hardware should instantly work with Linux if there is support for it in the Kernel. Means: pop in your Linux CD, boot up, start working. Done.

> **dcs.79c said:**
>  Can you be more specific?
[http://en.wikipedia.org/wiki/Modprobe](http://en.wikipedia.org/wiki/Modprobe)


> **dcs.79c said:**
>  How is the kernel updated?  Update manager. Just like the rest of the OS. Or you do it manually with the appropriate shell commands (useful when you're logged in remotely or don't have a GUI on the system).

> **dcs.79c said:**
>  or must one use DOS mode? What's a DOS mode??? :D

> **dcs.79c said:**
>  I can't walk into a store & walk out with Linux software. Or can I?  Why would you need to do that? You just tell the package manager what you want, and voila, it goes and downloads the stuff for you. Done. No need to walk into any store.

BTW, commercial software for Linux _IS_ available if you go and look in the right places, but I would not expect to find that in your average smalltown computer shop.

> **dcs.79c said:**
>  What are good websites for obtaining Linux software? This is again Windows thinking. "Go to a web site and hunt for software, download X, click next, next, next, ... "

There are a few web sites that are like that (getdeb comes to mind ...) but here on Ubuntu it's all about the repositories. Which means: you don't go to web sites to hunt for software ... You go to web sites to learn where their software repository is, and then you let the package manager figure it all out and you let it hunt for software for you. That's its job, not your's. You just lean back and watch the applications install themselves :D

---

### Post by scorp123 on 2009-08-24
> **dcs.79c said:**
>  I really would like to "wean" myself from Windows & use Linux exclusively. Then do it. :D

---

### Post by URPradhan on 2009-08-24
> **sasho_zl said:**
> First of all Linux has NOTHING  in common with windows. The so called BSOD in windows appears because the system is not well build and if one thing crashes it takes everything down with it! In Linux the situation is different. In Linux even if the graphical user interface encounters a serious problem he can stop working but the Linux system will be fully operational in the background and you can restore the interface with a few commands...
Brother,
I do not agree with you on this. Even Ubuntu/Linux crashes like BSOD in XP !!! Surprised ? Yes, Unlike XP, Ubuntu does not show the blue screen with what causes the error. But the system hangs hard, and nothing works including keyboard, mouse, hot keys, etc .... ONLY POWER-OFF is the only solution !

Lets come to the scenario. I have GeForce FX 5200 nVidia video APG card mounted on y ASUS K8N MB. Even though I have the latest drivers for XP/Linux, in both cases my system hangs. In XP its BSOD and in ubuntu its permanent hang. 

Now you tell me how Ubuntu/Linux does not have similar things like BSOD of XP ?

Note that, I have configured the proper BIOS options including Disable fast write, etc, but still it hangs :(

---

### Post by theozzlives on 2009-08-24
> **dcs.79c said:**
> Does Linux have an equivalent to Windows BSOD? If what happens in Windows that causes a BSOD should happen in Linux, what happens?
 
Why does Linux require a separate partition for the swap file? Is it required or is it optional? I know that Windows has the option of putting a swap file on a separate partition.
 
Vista has a neat feature called dynamic disk. I know that Linux doesn't use drive letters. Does Linux have "dynamic disk"? Can one combine 2 or more physical disks in Linux to equal 1 dynamic disk?
 
I want to build a PC & I'm intrigued by VMware's workstation. I have 2 choices for the host OS, Windows or Linux. I have Vista on my laptop & it has BSOD'd more than once. If I'm going to have both Linux & Vista on my PC, I want a stable OS that doesn't lock up & BSOD.
 
How do I add more than 1 GUI? I'd like to be able to switch between Gnome, KDE & XFCE.
 
Thank you.
David

1. As said before, it's called Kernel Panic. I've never had one.

2. You can make a swap file, but it's better for a swap partition. A temp swap file is handy if you need a lot of swap for something like making your own custom Live CD.

3. Linux is kinda like a dynamic disk, in that you create a Mount Point that looks like a folder to mount a separate disk.

4. I'm not familiar with VMWare, I use [Virtual Box]("http://www.virtualbox.org"). It supports anything but Direct X. BTW: This computer had Vista once, when I bought it, I turned it into a Linux box straight away! VB runs XP, and 7 RC just fine. Vista is junk and it won't touch my machines.

5. that has been stated, you can do:```
sudo apt-get install kubuntu-desktop
```to get KDE, I've tried different WMs and I like GNOME.

---

### Post by P4man on 2009-08-24
> **URPradhan said:**
> Brother,
I do not agree with you on this. Even Ubuntu/Linux crashes like BSOD in XP !!! Surprised ? Yes, Unlike XP, Ubuntu does not show the blue screen with what causes the error. But the system hangs hard, and nothing works including keyboard, mouse, hot keys, etc .... ONLY POWER-OFF is the only solution !

Lets come to the scenario. I have GeForce FX 5200 nVidia video APG card mounted on y ASUS K8N MB. Even though I have the latest drivers for XP/Linux, in both cases my system hangs. In XP its BSOD and in ubuntu its permanent hang. 

Now you tell me how Ubuntu/Linux does not have similar things like BSOD of XP ?

Note that, I have configured the proper BIOS options including Disable fast write, etc, but still it hangs :(

You are right, linux kernel can freeze up pretty badly, but its usually related to bios problems, more specifically non compliant ACPI implementations. 

Many bios's, especially on cheaper boards, implement acpi code that is specifically  designed to work with windows, and windows only. They even test if its windows Xp or Vista, load routine A for Xp and B for vista. But if its neither xp or vista, they dont have default path and some things dont get initialized. 

On such boards, also windows 2000 may fail to run at all, or bluescreen.  Linux tries to work around that with a ton of blacklists and quirks and workarounds, but its not always successful. In such case, you can try some kernel parameters to cure the problem.  If you post the output of 

```
dmesg
```

I may be able to give you some advice. You can already try if the machine boots (and is stable) by booting with acpi=off. If that fails, try napic nolapic. You can also check if there is a newer BIOS available for your board, it might have been patched.

But I agree, on some hardware, linux can be less stable than windows 3.1 until you figured out the cause and a solution. And in those cases, a bluescreen would be a good thing.

---

### Post by URPradhan on 2009-08-24
> **P4man said:**
> You are right, linux kernel can freeze up pretty badly, but its usually related to bios problems, more specifically non compliant ACPI implementations. 

Many bios's, especially on cheaper boards, implement acpi code that is specifically  designed to work with windows, and windows only. They even test if its windows Xp or Vista, load routine A for Xp and B for vista. But if its neither xp or vista, they dont have default path and some things dont get initialized. 

On such boards, also windows 2000 may fail to run at all, or bluescreen.  Linux tries to work around that with a ton of blacklists and quirks and workarounds, but its not always successful. In such case, you can try some kernel parameters to cure the problem.  If you post the output of 

```
dmesg
```

I may be able to give you some advice. You can already try if the machine boots (and is stable) by booting with acpi=off. If that fails, try napic nolapic. You can also check if there is a newer BIOS available for your board, it might have been patched.

But I agree, on some hardware, linux can be less stable than windows 3.1 until you figured out the cause and a solution. And in those cases, a bluescreen would be a good thing.

Thank you dear...I'll try your suggestions today and will update here. I'm totally fade-off with this mother board and graphics card.

---

### Post by scorp123 on 2009-08-24
> **URPradhan said:**
>  Even Ubuntu/Linux crashes like BSOD in XP !!! It's called a "kernel panic" and it does not exactly "look like XP", e.g. there won't be a blue screen with idiotic hexadecimal stuff written on it. It will be a black screen with almost idiotic and highly cryptig hexadecimal stuff written on it ... :D

A Linux kernel panic is easy identifiable as such because the system will tell you that it did panic.

[IMG]http://orionida.files.wordpress.com/2008/02/kernel-panic.jpg[/IMG]

[IMG]http://khour.ir/digital/wp-content/uploads/2007/11/linux-kernel-panic-under-qemu.jpg[/IMG]

The last kernel panic I've seen for real was back in 2001 when a harddrive suddenly died. 

Hard freezes however are a different thing. Those usually have to do with either flaky CPU, flaky RAM or most likely a flaky ACPI implementation in your BIOS.

---

### Post by P4man on 2009-08-24
> **scorp123 said:**
> 
Hard freezes however are a different thing. Those usually have to do with either flaky CPU, flaky RAM or most likely a flaky ACPI implementation in your BIOS.

once X has loaded and you get a kernel panic, you dont get to see the tty output, but its still a kernel panic. Only clues are (usually) flashing keyboard leds.

edit: btw, I hope those screenshots aren't actually yours. Harddrives in PIO mode ? Thats gonna be slllooooowww lol.

---

### Post by scorp123 on 2009-08-24
> **P4man said:**
> once X has loaded and you get a kernel panic, you dont get to see the tty output Not true. It depends on the graphics card and what exactly went wrong. If the GPU is hanging then yes, you won't see it anymore. If however the kernel is still able to kill X or able to switch to another tty you might still see it. But yes: blinking keyboard leds and a frozen screen are strong indications that your kernel did something it should not have done ... :)

But that's not a "hard freeze". A hard freeze may occur both in text mode and in graphics mode. You usually have to use really flaky and/or broken hardware or a really experimental kernel with even more experimental tweaks. I remember getting hard freezes with hand-compiled kernels where I tried to tweak ACPI and kernel scheduler settings ... my system didn't like those tweaks it seems :D


> **P4man said:**
> 
edit: btw, I hope those screenshots aren't actually yours.  Google. Just type "Linux kernel panic" into the image search. As I said: The last real kernel panic I've seen for real was in 2001 ...

---

### Post by P4man on 2009-08-24
> **scorp123 said:**
> Not true. It depends on the graphics card and what exactly went wrong. If the GPU is hanging then yes, you won't see it anymore. If however the kernel is still able to kill X or able to switch to another tty you might still see it. But yes: blinking keyboard leds and a frozen screen are strong indications that your kernel did something it should not have done ... :)


Ive never seen that. Kernel panics I've had (due to an ACPI problem), always blinking leds and frozen (X) screen. No way to switch tty and I never saw it switch to a tty by itself, but I'll take your word for it that it  does that in some cases :)

---

### Post by 3rdalbum on 2009-08-24
I've had kernel panics recently when a partly-experimental wireless driver left the kernel's wireless subsystem in a weird state, and then I plugged in a different wireless card.

On one occasion I just immediately got blinking keyboard LEDs, and on another occasion it worked for a while; everything started freezing and I switched to a virtual terminal and saw kernel "Oops" messages being printed. The kernel was trying to recover from the damage done to its memory, and then it finally panic'ed.

I'd just like to correct some of your terminology:

"DOS mode" is a piece of Windows terminology, where it loads up the command-line-based operating system (MS-DOS) that came out before Windows. On Linux, the command-line is part of the system, and it has nothing to do with the old MS-DOS operating system.

Virtualbox is definitely the best virtualisation software for you. It really is excellent, and unlike some competitors it's free for personal use.

Linux is so incredibly different to Windows, that merely reading about it will not prepare you. You have to install it in order to know what's going on. And, I've found that books don't seem to be very helpful for real-world Linux skills; they tend to focus on server administration or "how to create documents in Openoffice.org". Not on "how to install a kernel module" or "how to troubleshoot problems". If you need to install kernel modules or troubleshoot problems (not everyone does, your milage may vary), then this is something you have to learn on the fly. Hopefully if you do need to do those things you will already have a bit of Linux experience under your belt by then, and you can quickly pick up what to do.

---

### Post by scorp123 on 2009-08-24
> **P4man said:**
> Ive never seen that. Kernel panics I've had (due to an ACPI problem), always blinking leds and frozen (X) screen. I forgot to mention what the difference to a "hard freeze" is:

- You work in X ... and all of a sudden your mouse stops moving.
- Keyboard seems to have stopped responding too
- no answer on ping, it's as if your host was not even powered up
- no blinking LED's or anything: no matter what key you hit there simply isn't any reaction

On some boxes I have had not even pushing the power-button for 10 secs and more will do anything ... it's as if the system had been instantly frozen. Hence the name "hard freeze".

Only way around this: cut the power. Not even the "magic SysRq" key combo (Alt + SysRq + R+E+I+S+U+B) will work as the keyboard is "frozen" too.

When you power up again and check the logs you will notice that all of a sudden there is a time gap between what must have been the moment the system got frozen and the fresh reboot. But there is nothing in the logs whatsoever that would give you a hint what the heck went wrong ...

Kernel panics on the other hand usually leave log entries behind, either in the system log (/var/log/messages) or e.g. in the X.org logs and possibly other places too. And the "magic SysRq" key combo will usually still work so you at least get to cleanly reboot the system.

Another reason why a "hard freeze" really really sucks. Chances are good that your filesystem and/or whatever file you had open at that moment got badly corrupted, journal or no journal.

---

### Post by P4man on 2009-08-24
so what is it then when the mouse and keyboard freeze up in X but the keyboard leds blink ? I never tried that magic boring elephant key combo, as I didn't know about it then, but id guess it wouldn't have worked. But istnt blinking keyboard leds always a kernel panic?

---

### Post by scorp123 on 2009-08-24
> **P4man said:**
> But istnt blinking keyboard leds always a kernel panic? As I said before: Yes it is. Strongly so. It's a kernel config option as far as I remember ...

... Googling ...

[http://rhcelinuxguide.wordpress.com/category/linux-kernel/](http://rhcelinuxguide.wordpress.com/category/linux-kernel/)

And ages ago someone wrote a modification so that those LED's would emit Morse code (!!) when the kernel panics:
[http://kerneltrap.org/node/355](http://kerneltrap.org/node/355)

That's just geeky :D

---

### Post by URPradhan on 2009-08-26
Update:
I have tried with kernel parameters like.... "acpi=off" and "noapic nolapic", but still Ubuntu goes into hardfreeze, specially when I try to run any heavy application like, Opera browser, GIMP, VLC Player, etc ... 

And its a similar story for XP too. If m/c is sitting ideal its working but while opening any heavy application system hangs. What could be the problem ?

Also, How can I change the AGP rate from 8X to 4X in Ubuntu for GeForce FX 5200 AGP ?

NOTE: I have ASUS K8N MB, Geforce FX 5200 AGP, 320 GB ATA HDD, 512 MB RAM

---

### Post by P4man on 2009-08-26
> **URPradhan said:**
> Update:
I have tried with kernel parameters like.... "acpi=off" and "npapic nolapic", but still Ubuntu goes into hardfreeze, specially when I try to run any heavy application like, Opera browser, GIMP, VLC Player, etc ... 

And its a similar story for XP too. If m/c is sitting ideal its working but while opening any heavy application system hangs. What could be the problem ?

NOTE: I have ASUS K8N MB, Geforce FX 5200 AGP, 320 GB ATA HDD, 512 MB RAM

Sounds like a hardware problem then. Perhaps the CPU is overheating? Powersupply failing? Bad RAM modules (did you run memtest?)

---

### Post by URPradhan on 2009-08-26
> **P4man said:**
> Sounds like a hardware problem then. Perhaps the CPU is overheating? Powersupply failing? Bad RAM modules (did you run memtest?)

Yes, I have ran memtest86 with all phases/passes and it did not found any error. I have the screen shots that I'll share today later.

Is it due to AGP rate 8X ? How can I change the AGP rate from 8X to 4X in Ubuntu for my GeForce FX 5200 ?

---

### Post by The Cog on 2009-08-26
> **URPradhan said:**
> 
Vista has a neat feature called dynamic disk. I know that Linux doesn't use drive letters. Does Linux have "dynamic disk"? Can one combine 2 or more physical disks in Linux to equal 1 dynamic disk?

Google for "Linux LVM" (Logical Volume Manager). It's a standard offering in Ubuntu, and probably all distros. It's a two-stage configuration. Firstly you nominate a one or more disks/partitions to be members of a pool of disk storage. Secondly, you divide that pool into one or more logical disks that you can then format with filesystems. I did one a couple of weeks ago, joining a pair of pyhysical disks into one logical disk and using striping to improve disk throughput.

---

### Post by stalkingwolf on 2009-08-26
there is Gnome Device Manager   its in synaptic.

---

### Post by URPradhan on 2009-08-27
> **URPradhan said:**
> Yes, I have ran memtest86 with all phases/passes and it did not found any error. I have the screen shots that I'll share today later.

Is it due to AGP rate 8X ? How can I change the AGP rate from 8X to 4X in Ubuntu for my GeForce FX 5200 ?

Here are the screenshots of NVIDIA SYSTEM utility ...
Is anything wrong here for the hardfreeze issue of my PC with Asus K8N MB + GeForce FX 5200 + 320 ATA HDD + Ubuntu 9.04/WinXP ?
[IMG]http://i29.tinypic.com/2zog2mb.jpg[/IMG]
[IMG]http://i27.tinypic.com/24w9cvo.jpg[/IMG]

Thank you.

---

