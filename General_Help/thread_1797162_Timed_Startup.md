---
title: "Timed Startup"
date: 2011-07-04
forum: General Help
---

### Post by IlbiStarz on 2011-07-04
Hey everyone,

So I'm pretty new to Ubuntu. What I want to do is a timed startup.

Right now, I'm using a program called Auto Power on and Shut down on Windows. It let's me set times for the computer to shutdown, power on, hibernate, sleep, and etc. 

Is there any program or any script you can write for Ubuntu that lets you do this? I need something like:

Tell computer to turn off at 10am. 

*run programs*

Tell computer to (does Linux have hibernate?) something that isn't shutdown but looks like it's shutdown at 5pm. I use hibernate in Windows.

Thanks guys!

---

### Post by searchfgold6789 on 2011-09-08
Yes, there is such an application. It is called "gshutdown".
Yes, I know for a fact that Ubuntu has a hibernation and a sleep feature, but I have always had problems with those. I think it usually only works if you have a newer computer.

---

### Post by Bodsda on 2011-09-08
> **IlbiStarz said:**
> Hey everyone,
 
So I'm pretty new to Ubuntu. What I want to do is a timed startup.
 
Right now, I'm using a program called Auto Power on and Shut down on Windows. It let's me set times for the computer to shutdown, power on, hibernate, sleep, and etc. 
 
Is there any program or any script you can write for Ubuntu that lets you do this? I need something like:
 
Tell computer to turn off at 10am. 
 
*run programs*
 
Tell computer to (does Linux have hibernate?) something that isn't shutdown but looks like it's shutdown at 5pm. I use hibernate in Windows.
 
Thanks guys!
 
Auto on times can be configured from the bios. Off times can use a shutdown command scheduled with cron
 
Bodsda

---

### Post by ofnuts on 2011-09-08
> **IlbiStarz said:**
> Hey everyone,

So I'm pretty new to Ubuntu. What I want to do is a timed startup.

Right now, I'm using a program called Auto Power on and Shut down on Windows. It let's me set times for the computer to shutdown, power on, hibernate, sleep, and etc. 

Is there any program or any script you can write for Ubuntu that lets you do this? I need something like:

Tell computer to turn off at 10am. 

*run programs*

Tell computer to (does Linux have hibernate?) something that isn't shutdown but looks like it's shutdown at 5pm. I use hibernate in Windows.

Thanks guys!
For startup, see some indications here: [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

For shutdown there are plenty of apps (even the comand line "shutdown...").   

From a hardware point of view shutdown and hibernate are the same (machine is completely powered off). On my laptop, re-boot is much faster (and somewhat more reliable) than wake-up from hibernation, so I don't bother with hibernation.

"Sleep" is a different animal, the machine isn't completely powered off, but I don't know if a timed wakeup is possible.

---

