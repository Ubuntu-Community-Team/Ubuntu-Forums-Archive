---
title: "Dissappointed - HP Printer"
date: 2010-11-25
forum: General Help
---

### Post by Quarkrad on 2010-11-25
Just bought HP Photosmart Premium printer because I read that HP is one of the better manufacturers that supports Linux. I'm running 10.10 sw.  Ideally I would like to hardwire the printer to a Ubuntu 10.10 PC via USB and in the same room, connect another Ubuntu 10.10 PC to the printer using wireless.  Initially I set up the printer on my WinXP side using the CD disk with the printer - to my surprise I was able to make a connection with the printer using wireless straight away. I rebooted to Ubuntu and connected the printer via USB.  A window popped up saying the driver for a HP Photosmart C310 printer was missing (encouraging as this printer is known as a C310).  Then another search window popped up looking for the driver. Eventually a New Printer window popped up with the option to select the driver from a database.  There are three Photosmart Premium printers listed but all the drivers appear to be for a c309 printer.  Selecting one of these drivers does allow me to print a text doc but scanning is a no goer.  I installed the HP Toolbox from the reps but this doesn't even see the printer no matter what I try (USB or wireless).  So far disappointing &#8211; on WinXP (that I do not want to use) I have fully feature rich Photosmart Premium (c310) but so far on Ubuntu 10.10 all I have is a basic USB printer.  Is this the best I can achieve?

---

### Post by mastablasta on 2010-11-25
You need to get propper drivers.
 
Try here:
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=115&prodSeriesId=4023238&prodTypeId=18972&objectID=bpu00658#A2](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=115&prodSeriesId=4023238&prodTypeId=18972&objectID=bpu00658#A2)
 
and here:
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by WorMzy on 2010-11-25
I've never had one of these newfangled all purpose swiss army-knife printers, but I expect that you need to set up the features separately on Linux. The printer drivers will be for the printer aspect of the.. uh.. printer.

I suggest installing hplip, if the driver downloader didn't already; it's a bunch of tools specifically for HP printers and apparently supports both single function and multifunction printers. You may also want to install sane-utils, for back-end scanner support.

After that, you're on your own. I've got no idea whether you'll need to configure things or what command-line/GUI tools you need to use to access the various functions, but hopefully I've given you something to work with. Use google to see if anyone else has the same printer and has tips on how to access the various functions.

---

### Post by colin.p on 2010-11-25
> **Quarkrad said:**
> Just bought HP Photosmart Premium printer because I read that HP is one of the better manufacturers that supports Linux. I'm running 10.10 sw.  Ideally I would like to hardwire the printer to a Ubuntu 10.10 PC via USB and in the same room, connect another Ubuntu 10.10 PC to the printer using wireless.  Initially I set up the printer on my WinXP side using the CD disk with the printer - to my surprise I was able to make a connection with the printer using wireless straight away. I rebooted to Ubuntu and connected the printer via USB.  A window popped up saying the driver for a HP Photosmart C310 printer was missing (encouraging as this printer is known as a C310).  Then another search window popped up looking for the driver. Eventually a New Printer window popped up with the option to select the driver from a database.  There are three Photosmart Premium printers listed but all the drivers appear to be for a c309 printer.  Selecting one of these drivers does allow me to print a text doc but scanning is a no goer.  I installed the HP Toolbox from the reps but this doesn't even see the printer no matter what I try (USB or wireless).  So far disappointing &#8211; on WinXP (that I do not want to use) I have fully feature rich Photosmart Premium (c310) but so far on Ubuntu 10.10 all I have is a basic USB printer.  Is this the best I can achieve?

There is no way, that I know of, to connect a printer via USB AND by wireless. It's either one or the other. You obviously have a wireless router or AP, otherwise, the second wireless computer would not see the printer (the printer does not have router capability built in). So, have the printer connect to your router via wireless, so the second computer can see it, and then the first computer should see it through your home network. I am assuming the first computer can connect, or see the second computer?

I have the HP 6500 wireless printer and have 5 computers wireless or wired, and all can use all functions of the printer, through the router.


ps: if HPLIP doesn't see your printer (may be a new model?) you need to go to [http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html) to download the newest HPLIP, as the printer may be newer than the release of the repos version of HPLIP. I had the same problem with my printer in jaunty (had to download a new HPLIP), then when karmic came out the printer was listed fine.

---

### Post by Quarkrad on 2010-11-25
Quite a way forward now - downloaded the 'correct' c310 driver from the HP site and I have a HP Toolbox icon in the top panel. The current problem is that there is a Red exclamation mark over the printer icon in Admin/Printers.   It appears the problem is a missing filter, specifically **cups-missing-filter-warning**.  The popular solution to this on Google is sudo aa-complain cupsd but unfortunately it is not working for me.  I will carry on and try and fix this - I believe I have CUPS on my machine so this message/missing filter is intriguing. I'm a newbie so this is a bit like walking in the dark.  However....

---

### Post by Quarkrad on 2010-11-25
OK running hp-check -t in terminal shows any issues.  I've downloaded a couple of things but stuck on one last problem.  I need to install a package called foomatic-rip-hplip - it is missing on my system.  So far not having any luck on how to install this.

---

### Post by WorMzy on 2010-11-25
That's provided by the hpijs-ppds package.
EDIT: Actually, no, it's not. It was in Karmic and Lucid, but it's not in Maverick for some reason..

---

### Post by Quarkrad on 2010-11-25
Its down to this - debugging the printer via the HPToolBox I'm told **The printer's state message is: 'Filter"/usr/lib/cups/filter/foomatic-rip-hplip" for printer ..... not available**.  But when I look in usr/lib/cups/filer these is file called **foomatic-rip**.  Should I also have this other file foomatc-rip-hplip?  Are they different or the same thing and there is confusion?

---

### Post by WorMzy on 2010-11-25
It's a different file.
/usr/lib/cups/filter/foomatic-rip is provided by the foomatic-filters package.
/usr/lib/cups/filter/foomatic-rip-hplip was provided by the hpijs-ppds package (v. 3.10.2), the current version (v. 3.10.6) doesn't come with it. You could try installing v. 3.10.2 from the Lucid repos [here]("http://packages.ubuntu.com/lucid-updates/all/hpijs-ppds/download"), though there's no guarantee that will work with the packages you've got installed.

---

### Post by Quarkrad on 2010-11-26
My Ububntu Software Centre does not appear to like this package/file.  When it try to install it says **Dependency is not satisfiable: hpijs (= 3.10.2-2ubuntu2.1) **.  So far Google does not like this also - no hits on this output.  An adventure this!

---

### Post by WorMzy on 2010-11-26
You could install that from the Lucid repos too, from [here]("http://packages.ubuntu.com/lucid-updates/hpijs") (at the bottom, pick the architecture you're using), but that depends on libhpmud0 v. 3.10.2-2ubuntu2.1, which is available [here]("http://packages.ubuntu.com/lucid-updates/libhpmud0"). I think that's all you'd need.

---

### Post by Quarkrad on 2010-11-26
Still a problem I'm afraid on my 10.10 system.  It said there was a later version already in stall so I un-installed it via synaptic and installed the version in your late post.  Then I try to install the 1st file and Sofdtware Centre is still saying **Dependency is not satisfiable: hpijs (= 3.10.2-2ubuntu2.1) **

---

### Post by WorMzy on 2010-11-26
Are you sure you installed both packages from my last post? The first link is that exact version of hpijs; if it's complaining that you don't have it even though you've installed it, then I don't know what else you can do. You may have to cut your losses and live without full functionality. Either that, or install 10.04 LTS and use that instead of 10.10.

---

### Post by Quarkrad on 2010-11-26
Yes - I'm losing the will to live on this one.  Pity - brand new os (10.10) and brand new 'linux friendly' manufacturer and yet the install process is a nightmare.  The windows install was seamless - I've spend two days on this and to be honest - it is a bit of a pig.  All I have is basic printing.  Oh well........  thanks for your help.

---

### Post by Quarkrad on 2010-11-26
OK - perhaps I was too quick to complain.  The driver package HP provides only goes up to 10.04.  I reinstalled 10.04 and it is much better - I have a printer/scanner!  Hopefully, soonish, HP will include a version that runs on 10.10.

---

### Post by WorMzy on 2010-11-26
I think you have some cause for complaint, but at least 10.04 will be supported until 2013, so if HP take a long time to support later version, you've still got something to use. In the meanwhile, it might be worth sending a polite email to HP support, asking them to keep creating Linux compatible-drivers.

---

### Post by richlyn9 on 2010-11-26
hey !!! good to hear that your printer works in 10.4.

I have a lucid too and just bought a HP deskjet AIO 1050 but it was not detected automatically. 
the hP site lists 3.10.6 as the version but am not sure as the hplip version finder asked me to get 3.10.9 ver
so i am a bit confused...
could you advise me.

---

### Post by Quarkrad on 2010-11-27
I have just followed the steps I made on the HP site with your printer details and yes - it only goes up to 10.04 and points you to 3.10.9. I would suggest you download/install this version - it obviously supports a wide range of printers.

---

### Post by fatpanda on 2010-12-04
I ran into the same issues but didn't want to go back to ubuntu 10.04, so here's a quick fix for the situation, 

1. First install the hplip-3.10.9 as advised above. The scanner will work properly.

2. Fetch the lucid lynx hpijs-ppds package:
[http://packages.ubuntu.com/lucid-updates/hpijs](http://packages.ubuntu.com/lucid-updates/hpijs), for instance in your Downloads folder

3. Extract the foomatic-rip-hplip filter from the package:
# cd Downloads
# ar x hpijs-ppds_3.10.2-2ubuntu2.1_all.deb
# (cd / && tar xvzpf ~/Downloads/data.tar.gz ./usr/lib/cups/filter)

4. Setup your printer, everything should work as expected.

---

### Post by Quarkrad on 2010-12-06
I eventually found a method of getting 3.10.9 to run on 10.10 - so I have my printer working - almost.  I can't getting duplex printing working but there seems to be method so hopefully just more digging.  This is what I did (I tested on a clean install of 10.10)

1. Ensure fully up to date and multiverse and universe repositories are enabled in source list.

2. Install aptitude    **sudo apt-get install aptitude**

3. Download hplip 3.10.9 from hp website  (assume download to Desktop)

4. In terminal change to Desktop  cd Desktop

5. Run this command in terminal **sh hplip-3.10.9.run**

this will create a folder on your desktop called **hplip-3.10.9**  Close down the terminal.  Work will now be done in the hplip-3.10.9 folder.

6.  Open this folder and then open the folder called **installer**

7.  In the installer folder open a file called **distros.dat**

8.  Select all the text in this file and deleted it.  Save the file - so it is empty.

9.  Open browser and navigate to URL **[http://jamesmcdonald.id.au/it-tips/hp-officejet-pro-8500a-a910a-on-ubuntu-10-10](http://jamesmcdonald.id.au/it-tips/hp-officejet-pro-8500a-a910a-on-ubuntu-10-10)**  At the bottom of this page there is link to a text file. Click on the link and **Copy** all the text

10.  Go back to Desktop/hplip-3.10.9/installer/ and open the empty **distros.dat** file

11.  **Paste** the text from the web site into the empty file - save the file and close

12. Close all windows - back to Desktop.  Open the **hplip-3.10.9** folder and double click on a file called **hplip-install** and choose Run in Terminal.

This will re-open the terminal and auto run the installation script - you should find that all dependencies are identified and installed.  Eventually you are asked to connect the usb printer cable and everything is installed.

---

### Post by pudland on 2010-12-25
fatpanda,
Excellent post for the foomatic-rip issue.  This did the trick along with this post from Joshimitsu:
[http://ubuntuforums.org/showthread.php?t=1645102](http://ubuntuforums.org/showthread.php?t=1645102)
Sys Info:
Ubuntu 10.10
HPLIP 3.10.9
HP Prem C310

Thanks again!

---

### Post by mastermechanic on 2011-01-09
I'm fairly new to ubuntu and too need a HP driver for my wireless deskjet 3050 print scan copy printer. I went to the link for the hp drivers and downloaded. After that clicking on the file doesn't do anything but looks for a language code. 

What is the right procedure for installing these drivers?

Thanks,
Tony

---

### Post by Quarkrad on 2011-01-10
I've just had a look at the hp site and got as far as the Lunix page but the page/site is down for maintenance. I'll get back once it is up - what version of Ubuntu are you using?

---

### Post by Quarkrad on 2011-01-12
You can download the latest driver from here - [http://sourceforge.net/projects/hplip/files/hplip/](http://sourceforge.net/projects/hplip/files/hplip/)   you need to try 3.10.9

---

