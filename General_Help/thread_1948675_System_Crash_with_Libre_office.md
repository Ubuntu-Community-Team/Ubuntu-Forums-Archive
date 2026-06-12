---
title: "System Crash with Libre office"
date: 2012-03-28
forum: General Help
---

### Post by Scottty on 2012-03-28
Hello

Everytime I keep Libre calc or libre writer open for about 5-10 minutes everything stops working. The only thing I can do is move the mouse around but I can't select anything

I have a Toshiba C650D-007 Laptop
O/S is a dual boot between Windows 7 and Ubuntu 11.10

The issue I am having is when I am in the Ubuntu OS

I have uninstalled libre office. Then I reinstall Libre Calc and the problem happened again.

I would like to use Open Office however I tried installing from the command line. It said I was successfull however it didn't create an Icon to run the Open Office programs. I couldn't find it with the Dash either. 

I installed Synaptic Package Manager and if I look for open office it does say it is installed. How can I run the program. Do I have to do it through the command line.

---

### Post by ajgreeny on 2012-03-28
Try renaming the configuration folder for libreoffice then restarting LO again.

Where that folder is depends on your DE and version of LO, so in the 5 - 10 mins you have before it crashes, open the Tools ->Options ->Paths from the menu to find the configuration folder pathway, probably **/home/user/.config/.libreoffice**, though it has changed recently, eg, in version 3.5.1.2, to be **/home/user/.config/libreoffice **(note, no  **.** in the libreoffice folder name any more)

---

### Post by claracc on 2012-03-29
> I would like to use Open Office however I tried installing from the command line. It said I was successfull however it didn't create an Icon to run the Open Office programs. I couldn't find it with the Dash either.


I think you cannot have installed at the same time openoffice and libreoffice. You have to select one of them to install.

For installing openoffice from deb packages in openoffice.org you can follow this guide:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by Scottty on 2012-03-29
Hello again

It seems as though it is not Libre Office or OpenOffice that is the problem. Now the Ubuntu 11.10 is freezing without running those applications. Perhaps Ubuntu doesn't do well on Laptop computers.

I am going to reinstall Windows 7 and run Ubuntu in Virtualbox. 
I'm a little disappointed but hopefully Ubuntu 11.10 will run ok in Virtualbox.

I will let you know how it turns out.

Scott

---

### Post by Scottty on 2012-03-31
Hello again

Well I tried installing Ubuntu 11.10 as a guest OS with virtualbox and found it was very slow

So I thought about installing Ubuntu 11.10 again as a dual boot with Windows7 only this time I would use the 32 bit version instead of the 64 bit version. 

It seems like it is working well. I have had Libre calc open for 3 hours now and my system has not crashed

I am very pleased, I get to keep my Ubuntu.

Scott

---

### Post by CosmicFlux on 2012-06-09
Hey,

I've recently set up a dual-boot system between Linux Mint 13 & Ubuntu 12.04 on both my laptops. I've experienced this same issue when running LIbreOffice.

The system locks up, with only the mouse remaining operational.

It happened on both distro's so I initially thought it was my Acer laptop that was the problem, but it's happening on both distro's on my Packard Bell EasyNote too. 

The only common denominator was that I was running LibreOffice Base when these system crashes occured.

Anyone have any ideas? Are there any known issues in LibreOffice which could cause a system-wide crash of this sort?

Regards,

Daz

---

### Post by dasankir on 2012-08-08
I came across this and solved the same problem:
[http://forums.linuxmint.com/viewtopic.php?f=47&t=77851&start=0](http://forums.linuxmint.com/viewtopic.php?f=47&t=77851&start=0)

[INDENT]> Superfish wrote:
The fix: under the Tools->Options->LibreOffice->View menu, turn off "Use Anti-Aliasing"
(If that doesn't work, try also turning off "Use hardware acceleration")[/INDENT]

My system: Ubuntu 10.04 64bits, backported kernel 3.0.0

---

