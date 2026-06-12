---
title: "What's the best way to install Ubuntu?"
date: 2011-04-20
forum: General Help
---

### Post by malldoes on 2011-04-20
I just bought a new computer and it's running Windows 7, 64 bit.  My old HP printer won't work with Windows 7, 64 bit, but it does work with Ubuntu.  I've tried running Ubuntu off of a CD and the printer works fine.  It's just that running Ubuntu off of a CD is slow, so I figured I'd just install it on my hard drive.

The thing is, I have never had a computer with two operating systems on it, so I'm not sure how to proceed.  Do I just install Ubuntu under the Windows OS, or do I partition the hard drive and install Ubuntu there?  I only want to use Ubuntu to operate my printer, other than that, I will never use Ubuntu.  What's the best course of action for what I want to do?

Thanks for your time.

---

### Post by cottfcfan on 2011-04-20
Surely if all you want to use Ubuntu for is printing, wouldn't it make more sense to buy a new printer that works with windows 7, there cheap enough now.

---

### Post by ububeginner on 2011-04-20
I'm guessing that rebooting to switch to Ubuntu just to be able to use a printer will become a hassle. You should look into Virtual box. I will let you run Ubuntu from within Windows.

---

### Post by dragonfly41 on 2011-04-20
Since your printer works on ubuntu (but using different drivers in ubuntu) I would first try uninstalling your windows drivers and reinstalling by "add printer".

Explore these links ..

[http://www.bradkovach.com/printflush/](http://www.bradkovach.com/printflush/)

[http://www.fixyourownprinter.com/forums](http://www.fixyourownprinter.com/forums)

---

### Post by Dasti on 2011-04-20
Installing Ubuntu in the windows OS would work fine for you...if you've got time to switch to ubuntu every time you want to use the printer..

---

### Post by dcstar on 2011-04-20
> **malldoes said:**
> I just bought a new computer and it's running Windows 7, 64 bit.  My old HP printer won't work with Windows 7, 64 bit, but it does work with Ubuntu.  I've tried running Ubuntu off of a CD and the printer works fine.  It's just that running Ubuntu off of a CD is slow, so I figured I'd just install it on my hard drive.

The thing is, I have never had a computer with two operating systems on it, so I'm not sure how to proceed.  Do I just install Ubuntu under the Windows OS, or do I partition the hard drive and install Ubuntu there?  I only want to use Ubuntu to operate my printer, other than that, I will never use Ubuntu.  What's the best course of action for what I want to do?

Thanks for your time.

You could go to the Virtualization forum, read how to install the free VMware Player and install Ubuntu inside that.

Then you can have both Ubuntu and Windows operating simultaneously and print from Windows using a shared printer inside Ubuntu.

---

### Post by daxbau on 2011-04-20
> **cottfcfan said:**
> Surely if all you want to use Ubuntu for is printing, wouldn't it make more sense to buy a new printer that works with windows 7, there cheap enough now.
the printers are now cheap enough, thats true, but what about our environment:confused:
Theres a russian programmer who creates progs to reset the "death"-counter on printers.

f**** predicted obsoleszence.

whits theese russion tools, all the printers work fine, even if i got hardware errormessages.

hope this helps

(sorry that i cant give you the website, a russias friend of mine managed for me to get theese progs, cause i don't know kyrillic)

---

### Post by El Zoido on 2011-04-20
If you are anyway interested in using Linux/Ubuntu, simply install Ubuntu alongside Win7, it works fine in dual boot.
You should find enough info on how to do this on the net (it's easy).

But before doing so you can anyway try using a virtualization solution.
E.g. download Virtualbox and set up a virtual machine to run Ubuntu. 
If set up right, it might be able to access the printer.
Then create a shared folder where you move the files you want to print and open them from within your virtual machine.

---

### Post by malldoes on 2011-04-20
I tried uninstalling the printer and re-installing it, but still no luck.  I have Microsoft VirtualPC, but I'm guessing that works differently than VMware. (I'm checking out the VMWare website now.)

I really hate to buy another printer, since this printer still has a lot of life in it, plus, I have a lot of supplies for it.  If I was forced to buy a new printer, I'd have to go with the Epson 3000 to get something decent, and I don't want to spend $850 for a printer, when I probably won't be making a lot of prints anymore, now that I am retired.

It just bugs me that HP doesn't offer drivers for this printer to use in Windows 7 Ultimate, 64 bit.  This printer was their flagship printer when it came out, and now they act like they don't want anything to do with it.  

I have three printers, but each one serves it's own purpose.  My Epson Artisan 50 is used strictly for printing on CDs and DVDs.  My Kodak 1400 Pro is used for thermal dye prints, and my HP PhotoSmart 7550 was used for photo quality inkjet prints, and for everyday printing needs.  Losing the use of the HP printer leaves a big hole in my printing needs.

If anyone needs this computer's specs, it's an Intel i7-990X six core processor running at 3.46Ghz, 24GB of triple channel 1333Mhz RAM and two, 2TB hard drives.  I doubt anyone would need to know the other specs, but if so, it also has two DVD burners, an ATi Radeon 5870 video card, a SoundBlaster X-Fi Titanium sound card, and 10 USB ports (2 are USB 3.0).  So, I have several ways to connect UBUNTU besides running it off of a CD, but I'm sure it would be faster to just install it on the computer, only I've never had two OS's on a computer before and I wondered about the hassle of switching between the two.  It sounds like VMWare might cut down on the hassle.

Anyway, thanks for the replies.  I'll look into VMWare to see if that will make running Ubuntu a bit easier for me.  I just feel like without the 64 bit drivers to allow the printer to run in Windows 7, I'll never get the full use out of the printer anymore.:(

---

### Post by Ad@m on 2011-04-20
[http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=72892&lang=en&cc=us&prodTypeId=18972&prodSeriesId=72890&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=72892&lang=en&cc=us&prodTypeId=18972&prodSeriesId=72890&taskId=135)

Did you try drivers from ^

---

### Post by Spyderkid on 2011-04-20
install alongside windows 7 use a USB or CD

---

### Post by El3mentGamer on 2011-04-20
Download the .iso from Ubuntu.com
Burn the .iso onto a blank Cd/Dvd with a fair amount of file capacity (over 2GB)
Reboot your computer and when it's booting up press the 'Function' key to boot from another device (i.e. the CD)

---

### Post by malldoes on 2011-04-20
> **Ad@m said:**
> [http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=72892&lang=en&cc=us&prodTypeId=18972&prodSeriesId=72890&taskId=135](http://h20000.www2.hp.com/bizsupport/TechSupport/DriverDownload.jsp?prodNameId=72892&lang=en&cc=us&prodTypeId=18972&prodSeriesId=72890&taskId=135)

Did you try drivers from ^

Yes, they suggest that I install drivers for another printer, their Deskjet 5550, which I did, only to find out that since it's not a PhotoSmart printer, it doesn't have the options I need to print out photos.  It only prints out text.  I also tried installing their WinXP drivers in Windows 7, virtual PC emulation mode.  I can run WinXP inside Windows 7, but when I tried to print a picture, it would only print the top left corner of the picture, and it would print that small section on the bottom right side of the page.

Thanks for the suggestion though. :)

---

### Post by malldoes on 2011-04-20
> **El3mentGamer said:**
> Download the .iso from Ubuntu.com
Burn the .iso onto a blank Cd/Dvd with a fair amount of file capacity (over 2GB)
Reboot your computer and when it's booting up press the 'Function' key to boot from another device (i.e. the CD)

That's what I've been doing, but I was running Ubuntu off of the CD.  I wasn't sure of the best way to install it.....under Windows, on it's own partition, or in a Virtual environment like VMWare.

---

### Post by malldoes on 2011-04-20
Thanks for all of the help, I appreciate everyone taking the time to reply, but it looks like Ubuntu will have to stay on the CD.

I tried to install it under Windows, but I kept getting an error message, so I figured I'd just install it on it's own partition.  Big mistake.  Once it was installed, I had problems, so I uninstalled it.  That took awhile since I had to redo the boot sequence, then delete the partition.  Eventually I managed to get my computer back to the way it was, so I'm not going to touch anything....it's working. :)

---

