---
title: "Whats the chance of failure"
date: 2010-01-23
forum: General Help
---

### Post by esosa233 on 2010-01-23
Im still deciding on installing a dual boot ubuntu, I have a windows vista with 2007 office, but Im still not sure...I want to keep my basic mmo features...Whats the chance of this installation failing?

---

### Post by thegreatpenguin on 2010-01-23
I have several dual boot machines and they all work great if you manualy set your partition yourself set aside at least 10 gigs for ubuntu  then let the installer do the rest install it side by side you should be fine. I use all my office products under wine and they work great you can mount your file system and run the exe from the windows side hope this helps.

---

### Post by fjf314 on 2010-01-23
I did a dual-boot setup a few years ago with Windows XP and Ubuntu 6.06. Even then Ubuntu made it extremely easy to dual-boot. It literally amounted to clicking a button that I wanted to dual-boot just before the Ubuntu installation and moving a slider to note how much space I wanted to give my partition for Ubuntu. I can only assume that 9.10 makes it just as easy, if not easier.

---

### Post by esosa233 on 2010-01-23
what if I have 362 GB?

---

### Post by fjf314 on 2010-01-23
You can partition it however you see fit. thegreatpenguin's suggestion of 10 GB was just a minimum.

---

### Post by rogue_0111 on 2010-01-23
Run it in [VirtualBox]("http://www.virtualbox.org/"). 

This gives you the option to bounce back and forth is any issues arise. As a newbie this will be indispensable.

With virtualbox you can allocate the amount of RAM, video, H/D space, and hardware resources.

If for some reason some hardware on your comp does not have a driver or some other issue pops up, virtualbox is the best place to find this out.

---

### Post by thegreatpenguin on 2010-01-23
Yes my suggestion was just a minimum so that everything runs smoothly use however much you want.

---

### Post by esosa233 on 2010-01-23
ok, can some one give me an ideal partitioning for my current memory including the swap memory, also How do I install Virtual Box if I want to get it, do I install for windows host or linux host and how to use it.

---

### Post by Ginsu543 on 2010-01-23
We need some more information to help you. First, what are the specs of your computer? Do you have one 362 GB hard drive, or is that the sum of the capacities of all the drives you have installed? Also, how much ram does your computer have? Do you want the ability to hibernate? All this impacts how much swap you will need.

Second, how do you intend to use your Windows/Ubuntu? Do you plan to use Windows primarily with the ability to "play around" with Ubuntu? Or, do you plan to make Ubuntu your primary OS but need to run some Windows software? Or, do you want to be able to use both in their full respective glory?

The most basic setup is to assign equal space to Windows and Ubuntu. Assuming you have one 362 GB hard drive and 4 GB of ram, and you want to be able to hibernate, you could partition it like this:

1) 180 GB for Windows (Windows likes to be first)
2) The rest for Ubuntu, like this:
    a) 40 GB for / partition
    b) 137 GB for /home partition
    c) 5 GB for swap

However, if you have data files that you would like both Windows and Ubuntu to be able to access, you can create a separate data partition and keep things like documents, music, pictures, and video (things that are not OS-specific) on it. In that case, you could partition it like this:

1) 80 GB for Windows
2) 197 GB for data partition in NTFS (this will show up and be accessible in both OSes)
3) 40 GB for / partition
4) 40 GB for /home partition
5) 5 GB for swap

One note about VirtualBox. On my computer, I dual-boot Windows and Ubuntu. Previously, I would boot into Windows to run Windows software (Microsoft Office, BibleWorks, and games), and boot into Ubuntu to play around with it. But in the last year or so, I have pretty much made a total switch to Ubuntu. So I find that I hardly ever boot into Windows anymore. I do almost everything completely within the Ubuntu environment. However, there are a few instances in which I want to run Microsoft Office (I normally use OpenOffice but for some reason it doesn't handle a particular Greek font I need) or BibleWorks. That is why I decided to install Windows XP as a virtual machine inside VirtualBox. Not only does Microsoft Office and BibleWorks work flawlessly within VirtualBox, VirtualBox allows me to go seemlessly from my Ubuntu environment into the Windows environment and back again, all without the need to reboot. I can even copy and paste text from Microsoft Office directly into OpenOffice with both programs open. The only programs that don't work on VirtualBox are games. So I still have my dual-boot set up for that purpose. If you're interested in installing VirtualBox, follow the link rogue_0111 gave you, download the appropriate .deb package and install it using GDebi package manager (you should be able to just double-click it and it will launch GDebi for you). You will then have to allocate some hard drive space for a virtual disk that can be used by VirtualBox to install Windows on it. If you run into trouble, there is an entire forum section on Virtualization you can go to for help.

Hope that helps.

---

### Post by rogue_0111 on 2010-01-23
> **esosa233 said:**
>  How do I install Virtual Box if I want to get it, do I install for windows host or linux host and how to use it.

check out this video:

[http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows](http://tek-botics.webs.com/apps/videos/videos/show/6760140-how-to-get-virtualbox-on-windows)

---

### Post by Mark Phelps on 2010-01-24
> **fjf314 said:**
> ... Even then Ubuntu made it extremely easy to dual-boot. It literally amounted to clicking a button that I wanted to dual-boot just before the Ubuntu installation and moving a slider to note how much space I wanted to give my partition for Ubuntu. I can only assume that 9.10 makes it just as easy, if not easier.

If you do that with a Vista machine, you will almost certainly end up corrupting the Vista OS partition and rendering it unbootable!

You would do better using the Vista Disk Management utility to do the shrinking.

---

### Post by blueshiftoverwatch on 2010-01-24
> **esosa233 said:**
> Whats the chance of this installation failing?
I'm triple booting Ubuntu, Windows XP, and Windows 7 with no issues.

---

### Post by steveneddy on 2010-01-24
> **esosa233 said:**
> Im still deciding on installing a dual boot ubuntu, I have a windows vista with 2007 office, but Im still not sure...I want to keep my basic mmo features...Whats the chance of this installation failing?

Use Ubuntu in a virtual machine like VirtualBox until you gain more knowledge.

This will be easier and you will enjoy it better than using Wubi.

---

### Post by fjf314 on 2010-01-24
> **Mark Phelps said:**
> If you do that with a Vista machine, you will almost certainly end up corrupting the Vista OS partition and rendering it unbootable!

You would do better using the Vista Disk Management utility to do the shrinking.

Good to know, I was unaware of this.

Why does this become a problem with Vista?

---

### Post by Saiko Berry on 2010-01-24
Try Wubi if youre scared.. Though if you are scared Linux probably isnt for you.

---

### Post by fjf314 on 2010-01-24
> **Saiko Berry said:**
> Try Wubi if youre scared.. Though if you are scared Linux probably isnt for you.

I don't know if I would go that far. I recall I was pretty nervous when I did my first Linux install. Anything that's different can be a little scary at first.

---

### Post by Saiko Berry on 2010-01-24
Wubi is basically just a program that boots Linux at startup. Its like a virtual machine for Linux that works as the OS instead of a virtual OS, and its the same as dual booting basically. :l You install it through the exe, create a partition and uninstall it through the exe..

---

### Post by Slim Odds on 2010-01-24
> **rogue_0111 said:**
> Run it in [VirtualBox]("http://www.virtualbox.org/"). 

This gives you the option to bounce back and forth is any issues arise. As a newbie this will be indispensable.

With virtualbox you can allocate the amount of RAM, video, H/D space, and hardware resources.

[COLOR=DarkRed]If for some reason some hardware on your comp does not have a driver or some other issue pops up, virtualbox is the best place to find this out.[/COLOR]

Actually, that's false. The whole point of a "virtual" machine is that it does NOT let you have direct access to the hardware. VirtualBox (and other virtual machines) isolate your guest OS from the hardware and the host OS by providing a "pretend" machine.

If you want to test the hardware driver compatibility, the LiveCD is a much better way to do that. The only things that you can't really test that way are things like the proprietary video drivers, etc.

---

### Post by Joey B. on 2010-01-24
I just put a dual Boot with Windows 7 yesterday and everything works fine, except I can't get on my C Drive because I installed Ubuntu on my D Drive. Just shrink your drive then install on the largest free space.

---

### Post by akhilbehl on 2010-01-24
i would suggest the same (from experience) as one user above..
try to use only the vista utility to resize the drive.. otherwise there is a probability that you may lose the vista partition.. i say probably because it happened with me but i am not sure how many people it happens with..

also when this happened i read somewhere that.. this is because vista checks the filesystem after a resizing job and that leads to a problem if the resizing has been done by a third party software..

other than that.. i am dual triple booting with arch and winxp and i can vouch for it that it will be quite easy and moreover you would love ubuntu.. especially after vista (forgive me the opinion but vista really sucks, i would never use it even if it was free [as in free beer] because it just kills your hardware's performance and ubuntu is zapping fast compared to it).

---

