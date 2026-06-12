---
title: "Low battery life and very hot Laptop with Ubuntu 10.10"
date: 2011-02-12
forum: General Help
---

### Post by cletus8 on 2011-02-12
Hi People!

I have a Lenovo G555 Notebook:
AMD Athlon II Dual Core M320 2.2 GHz 3072 MB 320 GB

I have been using this with Ubuntu 10.10, but the problem is that the battery life time is VERY lower than with Windows 7, and also, the Laptop Itself gets **very very hot**!

Could you recommend me a more "laptop" friendly Distribution ?

I read that **OpenSUSE** is the best for this, but those topics where from 2008, so, things should be changed.

Thanks in advance!

---

### Post by cptrohn on 2011-02-12
Give Kubuntu a try, KDE has more advanced battery saving options than gnome does.

---

### Post by Habeouscorpus on 2011-02-12
Xubuntu/XFCE is great at power saving. On my netbook, I can stretch my battrey to ~9, and GNOME knocks it down to ~5-6.

---

### Post by cletus8 on 2011-02-12
> **Habeouscorpus said:**
> Xubuntu/XFCE is great at power saving. On my netbook, I can stretch my battrey to ~9, and GNOME knocks it down to ~5-6.

Hi again!

Well, i have this Laptop from less than 6 months, and i use it very few times a week.
The battery is 6-cell, 5200MaH, and when full charged, it can keep alive 1hr and 20 minutes with all the luck.

---

### Post by bobcollard on 2011-02-12
> **cletus8 said:**
> Hi again!

Well, i have this Laptop from less than 6 months, and i use it very few times a week.
The battery is 6-cell, 5200MaH, and when full charged, it can keep alive 1hr and 20 minutes with all the luck.
Your problem is not Ubuntu 10.10, it is the Kernel used by it.   Try Liquorix.  Installation instructions below.
For 32 bit, go here:  [http://forums.anandtech.com/showthread.php?p=31113394](http://forums.anandtech.com/showthread.php?p=31113394)
For 64 bit, go here:  [http://ubuntuforums.org/showthread.php?t=1588760&page=2](http://ubuntuforums.org/showthread.php?t=1588760&page=2)

---

### Post by cletus8 on 2011-02-13
Hi again!

i have installed the Liquorix Kernel, and not only the battery life improved. Also the overall performance improved a lot.

However, the max battery life i can reach is ~2 Hours. isnt this VERY low?
Remember its a 6-cell 5200mAH battery.

I dont understand how **Habeouscorpus** manages to get it alive for 5 / 6 hours....


any recommendation ?

---

### Post by bobcollard on 2011-02-13
> **cletus8 said:**
> Hi again!

i have installed the Liquorix Kernel, and not only the battery life improved. Also the overall performance improved a lot.

However, the max battery life i can reach is ~2 Hours. isnt this VERY low?
Remember its a 6-cell 5200mAH battery.

I dont understand how **Habeouscorpus** manages to get it alive for 5 / 6 hours....


any recommendation ?
First check out the specs at the company who made the computer.  Most will tell you to run the battery all the way down to get a full charge.  If you are using it mostly like a desktop, run the battery down to half charge and remove it running on AC.  This will prolong the battery life.  There are tricks to make your battery last longer, here is a URL up to date with information:
[http://www.wikihow.com/Extend-Laptop-Battery-Life](http://www.wikihow.com/Extend-Laptop-Battery-Life)

I use my computer as a desktop, the battery is stored and I am on AC with an external monitor and keyboard.  Use Google and search the forums for more information.  Glad the Kernel worked for you.
Bob

---

### Post by Habeouscorpus on 2011-02-13
> **cletus8 said:**
> Hi again!
I dont understand how **Habeouscorpus** manages to get it alive for 5 / 6 hours....


any recommendation ?


My battery powers a netbook... and it's rated for 8hrs 45 min. Sorry, I didn't mention that.

---

### Post by cletus8 on 2011-02-13
Hi again!

Well, finally i have installed XUBUNTU. I got a little lower cpu temp on stock and better performance (or at least gtkperf says that)

[B]
Things I have done after a fresh install of xubuntu:[/B]

[LIST=1]
[*]Installed Liquorix kernel (temp decreased 3ºc)
[*]installed manually latest FGLRX Ati Drivers
[*]Updated everything
[/LIST]
**The facts:**

CPU Temp (according to acpi): ~51ºc **vs** ~48ºc in Windows 7
battery life: ~2Hrs vs 2.5 Hrs Windows


About the Temperature, i dont think there is anything else can be done... or im wrong?

About the battery Life, i still think that 2hrs in Linux and 2.5hrs on windows is pretty low... Am i wrong? because im such a newbie with notebooks. All my life worked with desktops..


Thanks in advance!

---

### Post by Habeouscorpus on 2011-02-13
Well, it depends on what the battery was made for. Some batteries are kinda weak, and don't last long. My other computer has about a 4 hour life, and that's what it was made for. It could also be faulty, dying, possessed, stupid, and/or just plain bad quality. It may not be the operating system.

If you're feeling very adventurous, you can go into the computer's BIOS and throttle the CPU. This will make your computer slower, but it saves lots of power! You can also switch off the wireless card (another power suck) when you're not using it. 

There's also a neato little program called Powertop. You can install it from the repositories and tweak things that way. (Be sure to run it as root!)

---

