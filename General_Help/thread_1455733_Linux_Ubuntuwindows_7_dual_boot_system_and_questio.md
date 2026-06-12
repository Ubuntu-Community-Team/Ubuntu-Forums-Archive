---
title: "Linux Ubuntu/windows 7/ dual boot system and questions"
date: 2010-04-16
forum: General Help
---

### Post by Belgsken on 2010-04-16
Greetings everyone, 

I am new to the whole linux ubuntu system, but after another crash and data loss i decided to make the big step and go for it.
But i also have a few questions before i embark on this journey and i hope some of you are able to help me a little bit.

As the title says:

I have picked up this idea from someone that used to work with me on how he had a dual boot system on his pc. I would like to achieve the same with windows 7/ ubuntu. 
But here are a few questions:


1) I use a 64bit version of windows 7 is there a 64bit version of Ubuntu ?

2) Does anyone know a step by step guide for creating a dual boot system ? 

3) How do drivers respond in ubuntu (ex. i have a geforce 9800gx2) ?

4) Same as above but for gaming purposes ? (ex warcraft, fifa, gta etc)

I have been reading about unbuntu but just to be sure i would like to ask these questions and hope someone can answer them for me.

These are my system specs :

------------------
System Information
------------------
Time of this report: 4/16/2010, 14:23:38
    
   Operating System: Windows 7 Home Premium 64-bit (6.1, Build 7600) (7600.win7_gdr.100226-1909)
           Language: Dutch (Regional Setting: Dutch)
System Manufacturer: System manufacturer
       System Model: System Product Name
               BIOS: BIOS Date: 07/11/08 11:30:28 Ver: 08.00.12
          Processor: Intel(R) Core(TM)2 CPU          6600  @ 2.40GHz (2 CPUs), ~2.4GHz
             Memory: 8192MB RAM
Available OS Memory: 8192MB RAM
          Page File: 2165MB used, 14214MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: Using System DPI
 System DPI Setting: 96 DPI (100 percent)
    DWM DPI Scaling: Disabled
     DxDiag Version: 6.01.7600.16385 32bit Unicode


Thank you very much for reading :)

---

### Post by mikewhatever on 2010-04-16
> **Belgsken said:**
> 
1) I use a 64bit version of windows 7 is there a 64bit version of Ubuntu ?

Yes.

> 2) Does anyone know a step by step guide for creating a dual boot system ? 

There are lots of guides on the web, here is one:
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

> 3) How do drivers respond in ubuntu (ex. i have a geforce 9800gx2) ?

Nvidia has a driver for Linux. Once Ubuntu is installed, check under System->Administration->Hardware-Drivers

> 4) Same as above but for gaming purposes ? (ex warcraft, fifa, gta etc)

May games are only available for Windows. Some can be made work on wine, but I am no expert in this particular area.

---

### Post by Objekt on 2010-04-16
> **Belgsken said:**
> 
1) I use a 64bit version of windows 7 is there a 64bit version of Ubuntu ?

Yes, but don't feel as if you have to use the 64-bit version of Ubuntu.  As with Windows, there are still a few cases where software doesn't exist in a 64-bit version, or is not quite as easy to use as its 32-bit counterpart.  Unlike 32-bit Windows 7, the 32-bit version of Ubuntu can use all your 8 GB of RAM.

> **Belgsken said:**
> 2) Does anyone know a step by step guide for creating a dual boot system ?

Easier than you may think.  The Ubuntu install program will automatically detect your Windows 7 install, and you will get a choice of which OS to boot when you restart the machine. 

> **Belgsken said:**
> 3) How do drivers respond in ubuntu (ex. i have a geforce 9800gx2) ?

Nvidia has an Ubuntu-compatible drive package for all their cards, in both 32- and 64-bit versions.  

It is not possible to compare the performance of video cards under Ubuntu and Windows, because very few games are published in both Windows and Ubuntu versions.  So it is unknown whether the Nvidia drivers for Ubuntu are as good as the ones for Windows.

I can tell you that I have no trouble watching videos under both Ubuntu and Windows XP with my hardware.  Games are a different matter - more on that below.

eta: Wanted to add that installing the Nvidia drivers in Ubuntu is VERY easy.  Once you get Ubuntu installed and log in for the first time, you will see a little circuit board symbol in the upper right pop up and a message asking you if you want to install hardware drivers.  You just approve it (button says "OK" or "Proceed" or something of that nature).  The drivers are downloaded & installed automagically.  You reboot, and then you have an Nvidia control panel applet, just as in Windows.
 
> **Belgsken said:**
> 4) Same as above but for gaming purposes ? (ex warcraft, fifa, gta etc)

Some Windows games can be made to work in Ubuntu, but they usually either run more slowly, or have various bugs & glitches.  That is if you can get them to work at all.  At least for games released in the last few years.  It's not really worth the effort, to me, if you have a perfectly good Windows 7 install to use.

Hope this helps.

---

### Post by QIII on 2010-04-16
> **Objekt said:**
>  Unlike 32-bit Windows 7, the 32-bit version of Ubuntu can use all your 8 GB of RAM.

No.  It can address only 2^32 bytes, or 4GB of RAM, just like any other 32 bit OS.  With a PAE enabled kernel, you can address 32GB, but you take a performance hit.

Let's take the non-PAE kernel:  4GB.

In practice, you are not likely to be able to address much more than ~3.25GB - 3.5GB.

A 64 bit system can address 2^64 bytes, or 16 exbibytes(binary)/18 exabytes(decimal).   That's a monstrously big number.

---

### Post by 2hot6ft2 on 2010-04-16
The guide I wish I would have read before I installed 9.10
[http://www.ultimateeditionoz.com/forum/viewtopic.php?f=67&t=341](http://www.ultimateeditionoz.com/forum/viewtopic.php?f=67&t=341)

---

