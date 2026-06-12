---
title: "Serious Problems that appear unfixable"
date: 2011-04-22
forum: General Help
---

### Post by mike60014 on 2011-04-22
I am completely new to the Linux and Ubuntu environment so at this first post I will only be able to describe the nature of my problems but not provide any information as I do not know the commands to do so.

Basically I started experiencing a whole bunch of weird events after attempting to expand my partitions. My /home and /var were on separate partitions and I needed room. These partitions were not re-sizable so I simply created 2 new ones and copied the data from them to the new ones. All my partitions mount correctly and everything worked perfectly fine, initially. Then simply because I am OCD I had two pieces of unallocated space that were not combined. It annoyed me so i resized my swap partition to fit 1 smaller piece of unallocated space out of the 2. Restart, and can't run startx, couldn't run gdm either. Somehow got it to a point where I could run as root and now that I can actually see the error I still can't seem to fix it. 

The "report a problem button" also does not work in Ubuntu for no apparent reason. The process doesn't even seem to load when I do ps -A. 

When my system starts up it is set to start up in runlevel 2 with no gui and just CLI. I read somewhere that I may have to change this. Well low and behold the command inittab 2 or any number, does not work. I changed the file that I originally changed to edit the runlevel and boot in CLI and it does nothing. The file i edited was /etc/init/rc-sysinit.conf. 

Also, randomly my wireless stopped working as well, I have to plug in with an ethernet cable. 

My indicator applet session widget on my top panel randomly stopped working too. And every time my computer boots it displays 13 updates and 14 security updates of which when I go to update manager none of these display. I've attempted to reinstall pretty much everything except the OS itself and nothing has worked.

One thing I noticed is that gnome-desktop or just gnome is not installed. I cannot install it due to the dependency 'gnome'... When I run all the commands possible such as sudo apt-get upgrade, update, autoclean, check, aptitude upgrade, update; it finds nothing, and installs or updates nothing at all. And if I try to install from CLI with sudo apt-get install gnome it simply replies I have broken dependencies, which as I mentioned I did sudo apt-get check and everything else and it finds nothing. Please help, this is becoming very frustrating and I DO NOT want to reinstall. I really like Linux but I'm close to scrapping it and never using it again. I always have so many problems that seem unfixable. So i'm going to attempt to talk to the community about this one and let you guys do your thing because this is no longer working for me. Just let me know any commands I need to type or whatever and I will post the output and results, I need this fixed and refuse to accept that things just stop working for me for no apparent reason.

---

### Post by Zill on 2011-04-22
> **mike60014 said:**
> I am completely new to the Linux and Ubuntu environment so at this first post I will only be able to describe the nature of my problems but not provide any information as I do not know the commands to do so...
... Please help, this is becoming very frustrating and I DO NOT want to reinstall. I really like Linux but I'm close to scrapping it and never using it again. I always have so many problems that seem unfixable...
It is unfortunate that you have had so many problems with your installation.  However, I am puzzled as you say you are new to Linux but have discussed and implemented many "advanced" concepts that newbies do not normally even know about.  For example, a separate /var partition is generally only used for busy servers, not desktop systems.  In any event, unmounted partitions *should* be resizable!

It is possible that your numerous problems relate to using a server install, rather than a desktop install, as this would have automatically installed the Gnome desktop and avoided many configuration problems.

While you have stated you do not wish to reinstall, this is, IMHO, the best option.  Presumably you have little or no data on your existing Ubuntu installation.  Just backup what data you have and then reinstall using your preferred release of Desktop Ubuntu.  Allow the installation disk to re-partition the HDD with the required Linux "/", "/home" and "/swap" partitions (keep your Windows partition(s) if you wish to retain a dual-boot capability).  Re-installing should be a fast process and should leave a working Ubuntu desktop system.

I suggest you do this installation with an ethernet cable connected to your router.  This should automatically connect to the internet and allow all the updates to be installed.  Wireless is best configured *after* the installation is up and running. ;-)

---

