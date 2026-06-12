---
title: "Overheating issues"
date: 2010-01-05
forum: General Help
---

### Post by Mars92 on 2010-01-05
Recently I built a new computer, making my old laptop redundant, so I thought i'd turn it into a portable studio computer with linux. I'm running Ubuntu 9.04 with the low latency kernal and the ubuntustudio audio packages. 

And while the system still has many other kinks I need to work out, my main issue is heat. Even when I'm running the official Ubuntu kernal rather than real-time one, I'll use the laptop for basic browsing and messanging, and suddenly Ubuntu crashes with a warning saying that my laptop is too hot and has to shut down.

The only way I've found around this is to run the laptop from cold with an external fan blow right onto the computer. I can still hear the fan working and airflow is totally unrestricted. If it helps, the laptop is 4 years old and is a Acer Ferrari 4000.

I never had these issues running XP on it for the past 3 1/2 years and I'm reletively new to running a Linux system. Any light that can be shed on my problem is MUCH appreciated.

---

### Post by zine92 on 2010-01-05
It could be a driver issue of sort. Not very sure but guess i might share with you. I have a hybrid graphics card and when i boot ubuntu, 2 drivers will be automatically on and therefore making my laptop hot and so i had to disable 1 graphics card in bios during boot up. And i think if you are only using it as browsing/messaging/youtubing etc, you wouldn't need to install ubuntu, instead use a lighter weight version o ubuntu or some other small distros. Hope that helps. If you plan to try other distro, you may first install as a dual boot leaving ubuntu intact first, in case the problem really lies with drivers or power options. Anyway i found this thread, you can take a look. [http://ubuntuforums.org/showthread.php?t=1366256]("http://ubuntuforums.org/showthread.php?t=1366256")

---

### Post by audiomick on 2010-01-05
Hi.
Don't know much about that myself, but here is some info to start with.
[http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/acpi.4.html)
[http://manpages.ubuntu.com/manpages/hardy/man8/powersaved.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/powersaved.8.html)
[http://manpages.ubuntu.com/manpages/hardy/man4/acpi_thermal.4.html](http://manpages.ubuntu.com/manpages/hardy/man4/acpi_thermal.4.html)
[http://manpages.ubuntu.com/manpages/hardy/man8/apmd.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/apmd.8.html)

---

### Post by TBABill on 2010-01-05
For what it's worth, I have tried several distros recently for different purposes than your own issues with heat. However, heat was a big concern on my laptop that I use primarily and OpenSUSE 11.2 runs much cooler than Ubuntu, Fedora 12 and Mint. It also picked up all the drivers for my Acer 5520. Last night I installed 64 bit Mint 8 (pretty much the same as Ubuntu 64) and I am dual booting it with OpenSUSE. The 64 bit runs a little cooler than Ubuntu (Karmic 32 bit) did for me as well, but not quite as cool as SUSE.
 
Good luck. I haven't had any heat related shutdowns since switching from 32 bit Karmic, but I still feel like a "Ubunter" since I run mint 64 :)

---

### Post by akakingess on 2010-01-05
I am troubleshooting a similar issue and just had a quick question for anyone here on this thread having the overheating issue. Have you looked to see at what capacity the CPUs are running, and also does anyone else (besides myself) have something like (or exactly) Beagle running? I was wondering if Beagle would keep the processes running at a higher percentage than without. Don't mean to hijack this thread, rather was just wondering if anyone had the same stuff running in the background. Thanks in advance for any assistance or responses that you could provide.

---

