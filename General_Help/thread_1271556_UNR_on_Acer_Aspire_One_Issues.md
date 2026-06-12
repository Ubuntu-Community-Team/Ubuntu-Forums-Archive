---
title: "UNR on Acer Aspire One Issues"
date: 2009-09-21
forum: General Help
---

### Post by thefuturism on 2009-09-21
so, i finally bought my sd card to install unr to. i have been playing around with this tonight and here's what i've done, and what i have had problems with. i hope some of your expertise will help me.

okay, here's a _step-by-step_ of what i've accomplished so far:

-used an imagewriter to put the unr .img onto my usb flash drive.
-booted to the usb drive at startup and ran the "live session".
-plugged in my 8gb sd card.
-used the ubuntu drive partitioner to split my sd card into two partitions (one named 'UNR', and one named 'filestore').
-then i restarted the computer and booted from the usb drive again.
-i chose the "install ubuntu netbook remix" option.
-i went through the install procedure and repartitioned my sd card to allow room for "swap space" (about 460 MB).

[I][B]my partitioned sd card looked like this:
| 'filestore',NTFS,3.0GB | SWAP-AREA,460MB | 'UNR',ext2,4.0GB |.
[/B][/I]
-i chose to install ubuntu on the ext2 partition of about 4.0GB.
-the install went along smoothly and everything seemed to work fine.

**This is where my problems start**.
**1**-Once i restart after the initial install, i lose my menu bar from the top of the screen on all subsequent startups of ubuntu.
**2**-the GRUB loader also stops working: it still presents the option for me to boot into windows, but selecting that option just produces errors and tells me to restart. so the only way i can get back into windows is to remove the sd card altogether.
**3**-also, when in ubuntu it will not detect the wireless connection in my house and i cannot connect to the internet. 

(in case you were wondering why i partitioned my sd card, i did it that way so i can save my office and pdf files to the NTFS partition so if i plug my sd card into a random windows computer i will be able to access the files.)

Hopefully someone can lend a thought to this problem of mine!

---

### Post by thefuturism on 2009-09-21
Any ideas? I reinstalled UNR and the problem still occurs. as soon as i restart my computer and boot back into the newly installed unr, the menu bar will not show up.

---

### Post by beastrace91 on 2009-09-21
What model Aspire do you have? Also I know I personally had issue with the netbook launcher on NBR and I found it is easier to just use standard Ubuntu 32bit on my EEE

~Jeff

---

### Post by P4man on 2009-09-21
1. Im confused about 1. Does gnome load normally? do you have the netbook launcher interface thing to launch apps? Perhaps you can post a screenshot?

2. You have an internal drive (for windows) besides the sd card I assume? Where did you install grub to and what drive did you set as boot drive in the BIOS? Ive seen BIOS do weird things when you set a certain drive as primary boot, booting from it, but still making it the second drive, confusing the bootloader. Anyway, Im not really sure whats going on here either, as i don't see how you could boot into ubuntu without grub working? 

3. What network card do you have? please post the output of:

```
lspci
```
and/or
```
lsusb
```

---

### Post by thefuturism on 2009-09-21
Thanks for the replies!

**To beastrace91:**

I have the Aspire One D250. I've heard of trouble with UNR because it's set for a 11" screen while some of the net mini-laptops are 10.1" or less. If this claim is true, I don't believe it's the problem in my case. 
I have also heard that some people just install regular ubuntu on their netbook and then install the UNR packages so it LOOKS the same. Is this possible? (Also, will standard ubuntu run okay on a netbook? 


**To P4man:**

Sorry, I'll try to explain my situation more clearly.

1. I installed UNR to a partition on my SD card, while booting from my USB drive. The install finished fine, and everything was working okay (except my internet connection). Once I restarted my computer (I removed the USB drive for good, and changed the BIOS to boot from my SD card), GRUB loaded fine and I was able to choose "Load generic ubuntu" or whatever the first appearing option is to boot from. I select that and UNR loads okay, except for the (what I call) menu bar -- the bar at the very top that has the Time clock and such on it. That's the bar that disappears. I can restart and reboot many times but each time UNR loads, the bar will not show up - doesn't seem to load.

2. As I was saying above, GRUB does seem to load okay, and will boot into any of the ubuntu options. However, when I choose to boot via "Vista (Loader)" or "Windows XP", it just won't load. In the former option, it tells me something about a missing file and prompts me to restart. In the latter option, it just tells me that it is an invalid choice and bumps me back to the GRUB loader. On my first install of UNR, these buttons work though. I cannot figure out what's going on. 
I assume that GRUB is installed on the SD card as it does not boot if I remove the SD card (which is what I want so I can have a portable fully functioning operating system). My BIOS is set to boot from my SD card before my main internal hard drive. 

3. I'm confused as to what kind of output you want from me on the network card. How do I get that data through windows?

---

### Post by P4man on 2009-09-21
> **thefuturism said:**
> Thanks for the replies!

**To beastrace91:**

I have the Aspire One D250. I've heard of trouble with UNR because it's set for a 11" screen while some of the net mini-laptops are 10.1" or less. If this claim is true, I don't believe it's the problem in my case. 
I have also heard that some people just install regular ubuntu on their netbook and then install the UNR packages so it LOOKS the same. Is this possible? (Also, will standard ubuntu run okay on a netbook? 

I doubt that has anything to do with it. I had the NBR interface on my 22" desktop monitor for a short while, it worked fine. Although admittedly, I did install a regular ubuntu and added the NBR stuff afterwards. Still, I dont think thats it.



> 1. I installed UNR to a partition on my SD card, while booting from my USB drive. The install finished fine, and everything was working okay (except my internet connection). Once I restarted my computer (I removed the USB drive for good, and changed the BIOS to boot from my SD card), GRUB loaded fine and I was able to choose "Load generic ubuntu" or whatever the first appearing option is to boot from. I select that and UNR loads okay, except for the (what I call) menu bar -- the bar at the very top that has the Time clock and such on it. That's the bar that disappears. I can restart and reboot many times but each time UNR loads, the bar will not show up - doesn't seem to load.

weird. try pressing alt+F2 and start "gnome-panel". Does it appear then?
> 
2. As I was saying above, GRUB does seem to load okay, and will boot into any of the ubuntu options. However, when I choose to boot via "Vista (Loader)" or "Windows XP", it just won't load. In the former option, it tells me something about a missing file and prompts me to restart. In the latter option, it just tells me that it is an invalid choice and bumps me back to the GRUB loader. On my first install of UNR, these buttons work though. I cannot figure out what's going on. 
I assume that GRUB is installed on the SD card as it does not boot if I remove the SD card (which is what I want so I can have a portable fully functioning operating system). My BIOS is set to boot from my SD card before my main internal hard drive. 

Okay, i get it now. Thats probably not too hard to fix, and I bet its due to having a different boot order while you installed. Im no grub guru, but if you post the contents of /boot/grub/menu.lst, there will be someone able to figure it out.

> 3. I'm confused as to what kind of output you want from me on the network card. How do I get that data through windows?

From windows ? no idea :)
from ubuntu, open a terminal (probably somewhere in the UNR launcher, or otherwise alt+F2 and then "gnome-terminal". There type "lspci" and "lsusb" and ... ahem.. copy/paste the result here.  Heh, but you got no internet on ubuntu now I assume ?  You can put the output in a file with "lspci > lspci.txt" and "lsusb > lsusb.txt". Copy those 2 files from your homefolder to somewhere else (usb stick or that shared ntfs partition) and then post from windows. 

Or just look at the output, Im sure you won't understand most of it, but you'll probably see a line about "wireless ethernet controller 802.11" something. Thats the line Im interested in.

---

### Post by thefuturism on 2009-09-21
Okay, so I got around to testing your suggestions. 
alt+f2 does not launch the gnome-panel (I tried many times).
Consequently, I could not use the terminal to get the specs on my network card.

---

### Post by beastrace91 on 2009-09-21
The only difference between Ubuntu NBR and Ubuntu 32bit is the launcher Window. Everything else is 100% the same.

~Jeff

---

### Post by P4man on 2009-09-22
> **thefuturism said:**
> Okay, so I got around to testing your suggestions. 
alt+f2 does not launch the gnome-panel (I tried many times).
Consequently, I could not use the terminal to get the specs on my network card.

You dont need the panel to open a terminal? Its in accessories.
Also when you launch "gnome-panel" from a terminal, do you get an error message?

Lastly, try  alt+F1. It opens the main menu, which you dont have, but im wondering if its "offscreen". See if part of it becomes visibile when you press alt+F1

---

### Post by TR14RC3 on 2009-09-22
The reason that your wifi is not working is because you may have the wrong driver. The ath5k driver may or may not work with your netbook. If it does not detect right away, you may have to just enable the ath5k driver. It was not auto enabled when I installed 9.04. If you enable the ath5k, do a reboot not restart. And see if it works. If not, then the instructions to make the card can be found in my blog(depending on your wifi card but it works for most if you do it right). Also instructions on how to make the wifi light work because it usually does not work on the Acer Aspire One out the box with ubuntu. you have to make it work. Just to let you know, on the acer aspire one only one of the card reader work properly if you have two of them. One of them will only work if you have the card in at start up, but the other one works just fine. 

Here is my blog on the wifi card and light.   [http://tr14rc3linuxblogaceraspireone-tr14rc3.blogspot.com/](http://tr14rc3linuxblogaceraspireone-tr14rc3.blogspot.com/)

You may want to get another SD card just for your windows stuff and dedicate one for good old Linux. Or just try to see what happens if you don't partition that card. You can always go back and change it. Trail and error. You have to keep trying different things till you find what the answer is. It may just be the way you have that card set up. As far as the wifi, it has nothing to do with the card. I know that for sure. You need to get the wifi up and running manually if the ath5k driver does not work. It did not work with my netbook. It was manual install style. 

Have you tried installing Ubuntu with an external cd drive?

I heard that the acer wifi card and light not working out of the box with ubuntu is supposed to be fixed it Karmic Koala, but it is not a bad thing to know how to do manually. Depending on what you want to do with linux, you may need a different driver.

Forgot to say that it has been reported that if you go into suspend or hibernate mode, your netbook will delete everything on your sd card upon restarting. Yikes

If you have enough space, I would not use the netbook remix. I use the regular desktop/laptop version. 
Did not really care for netbook remix, but that just my opinion. 


If you are trying to keep windows on the computer and have linux on the SD card, when the computer starts is there an option to select windows or Linux or something like that?

Usually you will have an option to select the OS. Anyway, I am not sure how well that will work if you have one OS on a HDD and another on an SD card because of the boot order. So I am wondering if it gives you the option.

Another point I am trying to get at is: When having two versions of windows on a partitioned HDD, when ever you start one version or the other, it will delete all sytem restores from the other version. This could create problems trying to run linux and windows. I just prefer to keep windows and linux separate. Just to minimize conflicting issues and other problems. Thats why I got the netbook just for Linux.

---

### Post by moster on 2009-09-22
I have Acer aspire one too :)
I dont know why you insist in installing onto SD card when have perfectly large HDD inside. But, here is link how I got my wlan working atleast. It is really easy
[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html]("http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html")

---

### Post by thefuturism on 2009-09-22
**To P4man:**

I opened up the terminal and typed "gnome-panel", and it did show up at the top of the screen - but I couldn't get it to stay there. It kept disappearing. Here's what the terminal looked like:
> ~$ gnome-panel

** (gnome-panel:3231): DEBUG: Adding applet 0.
** (gnome-panel:3231): DEBUG: Initialized Panel Applet Signaler.

(gnome-panel:3231): libglade-WARNING **: Unexpected element <requires-version> inside <glade-interface>.
** (gnome-panel:3231): DEBUG: Adding applet 1.
** (gnome-panel:3231): DEBUG: Adding applet 2.
** (gnome-panel:3231): DEBUG: Adding applet 3.

** (gnome-panel:3231): CRITICAL **: panel_applet_frame_change_background: assertion `PANEL_IS_WIDGET (GTK_WIDGET (frame)->parent)' failed
** (gnome-panel:3231): DEBUG: Adding applet 4.

I'm not an expert but from what I know, seeing the word "Critical" usually isn't good?


**To TR14RC3:**

Thanks for all the information and experiments to try out - I will get back to you once I've tried everything out (right now I'm at school so I don't have a lot of time).

**To moster:**

Thanks for the link, I will experiment a bit later today. And the reason why I want the OS to be installed on the SD card is so I can have a completely portable version of UNR that I can essentially "plug-and-play" in any one of my computers. The added partition also lets me grab files from any windows-based computer.

---

### Post by TR14RC3 on 2009-09-22
> **moster said:**
> I have Acer aspire one too :)
I dont know why you insist in installing onto SD card when have perfectly large HDD inside. But, here is link how I got my wlan working atleast. It is really easy
[http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html](http://filthypants.blogspot.com/2009/03/ubuntu-904-jaunty-jackalope-on-acer.html)


I was wondering if your wifi light worked after just blacklisting the acer_wmi?

I tried with just that and it did not work.

There are actually 3 steps involved and it was the same process on two different netbooks..

You have to add some code to the etc/rc/.local 

and do this:
  
sudo aptitude install linux-backports-modules-jaunty

After all 3 steps it worked for me, but not with just one or two of the steps because I tried on 2 different netbooks and it was the same.

 To see Full instructions in my blog go here: [http://tr14rc3linuxblogaceraspireone-tr14rc3.blogspot.com/](http://tr14rc3linuxblogaceraspireone-tr14rc3.blogspot.com/)

---

### Post by moster on 2009-09-22
man, I have that very same Acer aspire one and everything is working but I do not have any SD cards.

I installed ubuntu remix 9.4 from usb aside XP and Windows 7. After installation I apply this tweak for wireless and that is that. Yes.. well, I could not boot to XP anymore, but I do not need it.

I guess source of your problems is that you install it onto SD card.


wlan tweak. It will just start working after this and restart. You will not have led active maybe. Mine seems off, but it work.
```
To fix this, hop onto a terminal and type:

    sudo gedit /etc/modprobe.d/blacklist

and add the line

    blacklist acer_wmi
```

---

### Post by P4man on 2009-09-22
> 
I'm not an expert but from what I know, seeing the word "Critical" usually isn't good?

If it was good it would be working :)

Anyway, using that error I found this thread:
[http://ubuntuforums.org/showthread.php?t=875887&page=2](http://ubuntuforums.org/showthread.php?t=875887&page=2)

A few different solutions in there, ranging from reinstalling gnome-panel to adding 2 commands to your session startup. Have a look, and give it a try.

---

### Post by thefuturism on 2009-09-22
> **P4man said:**
> If it was good it would be working :)

Anyway, using that error I found this thread:
[http://ubuntuforums.org/showthread.php?t=875887&page=2](http://ubuntuforums.org/showthread.php?t=875887&page=2)

A few different solutions in there, ranging from reinstalling gnome-panel to adding 2 commands to your session startup. Have a look, and give it a try.

Progress! Thanks P4man. I successfully fixed the first of my problems by adding "gnome-panel" and "metacity --replace" commands to the startup applications. It seems to have fixed the problems - my top panel is back, and I have borders on my open applications again.

The internet problem still persists, however. I opened a terminal and typed "sudo gedit /etc/modprobe.d/blacklist", I then added the line "blacklist acer_wmi". I turned off the computer and booted it back up into UNR but it still would not detect any network connections.

---

### Post by P4man on 2009-09-22
> **thefuturism said:**
> Progress! Thanks P4man. I successfully fixed the first of my problems by adding "gnome-panel" and "metacity --replace" commands to the startup applications. It seems to have fixed the problems - my top panel is back, and I have borders on my open applications again.

The internet problem still persists, however. I opened a terminal and typed "sudo gedit /etc/modprobe.d/blacklist", I then added the line "blacklist acer_wmi". I turned off the computer and booted it back up into UNR but it still would not detect any network connections.


Not all acer aspire one's are equal. AFAIK, they can use different wifi modules (among other things). So lets find out exactly what type of wifi card you have; open that terminal again, and post the output of:

```
lspci
```

If you dont have a wired connection at hand to copy/paste, you can redirect the output to a file:

```
lspci > lspci.txt
```

Put that textfile on a USB stick or shared partition, and post its contents.

---

### Post by thefuturism on 2009-09-22
Oh, right! I forgot about that. Here it is:

> 00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)

---

### Post by P4man on 2009-09-22
Do you have a (temporarily) wired connection ? If so, try this:

System>Administration>Software Sources and then check all options. 

then open a terminal and type:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-jaunty

```

reboot.

If you don't have a wired connection (or a different USB dongle you can borrow?), it will be a bit more tricky.

---

### Post by thefuturism on 2009-09-22
Yes, I have a wired connection I can play with once I get home - I am sitting in a psychology class right now. :)

Should I go back and undo the changes I made to the blacklist first?

---

### Post by P4man on 2009-09-22
> **thefuturism said:**
> Yes, I have a wired connection I can play with once I get home - I am sitting in a psychology class right now. :)

Should I go back and undo the changes I made to the blacklist first?

Im not entirely sure, but I think not. Keep it like that and try first.

---

### Post by thefuturism on 2009-09-22
> **P4man said:**
> Im not entirely sure, but I think not. Keep it like that and try first.

Okay so I plugged the cable into the side of my computer, and it still won't detect the internet in UNR. I have absolutely **no** idea where to go from here if the wired connection won't even work.

---

### Post by P4man on 2009-09-23
> **thefuturism said:**
> Okay so I plugged the cable into the side of my computer, and it still won't detect the internet in UNR. I have absolutely **no** idea where to go from here if the wired connection won't even work.

Oh dear. You're right. Your wired ethernet controller needs a driver. Thats like 1 in 1000. LOL.

There are a few things we can do to download the right packages from windows or a different computer, and put them on a usb stick or something, but before I talk you through that, are you *really* sure you don't have wireless working? Ive seen it too often ppl thinking its not working because nothing pops up, but if you click the network icon top right, do you not see a list with access points ?

---

### Post by thefuturism on 2009-09-23
> **P4man said:**
> Oh dear. You're right. Your wired ethernet controller needs a driver. Thats like 1 in 1000. LOL.

There are a few things we can do to download the right packages from windows or a different computer, and put them on a usb stick or something, but before I talk you through that, are you *really* sure you don't have wireless working? Ive seen it too often ppl thinking its not working because nothing pops up, but if you click the network icon top right, do you not see a list with access points ?

Yeah, when I right-click on the network indicator at the top there aren't any available networks in any of the tabs. Oh boy. Well, please, I'd appreciate the help.

---

### Post by P4man on 2009-09-23
> **thefuturism said:**
> Yeah, when I right-click on the network indicator at the top there aren't any available networks in any of the tabs. Oh boy. Well, please, I'd appreciate the help.

dont right click, LEFT click. Sorry to be a pain about this, but Ive spent a lot of time helping ppl getting their wifi drivers to "work", when they just worked out of the box :)

---

### Post by thefuturism on 2009-09-23
> **P4man said:**
> dont right click, LEFT click. Sorry to be a pain about this, but Ive spent a lot of time helping ppl getting their wifi drivers to "work", when they just worked out of the box :)

I've left-clicked, right-clicked, red-clicked, and blue-clicked. 

When I left click I am presented with: "No network devices available" and "VPN Connections /-> Configure VPN | Disconnect VPN" Disconnect is blanked out.

And when I right click to go "Edit Connections", nothing appears - that's what I was referring to earlier.

---

### Post by P4man on 2009-09-23
Try removing the acer_wmi from the blacklist, reboot, check again. Also try toggling the wifi button of your laptop. I believe the indicator light is non functional without newer driver, but most ppl seem to get it working nonetheless.

If not, well, you're gonna have to download some packages from another computer. Normally ubuntu does the package management, meaning it will download automatically any dependencies (other packages it needs to install the selected package). To help you with that on windows, you can try:

[http://keryxproject.org/](http://keryxproject.org/)

IT should work on windows. Use it to download the following packages:

**build-essential** (we will need that to compile the network controller driver)
**linux-backports-modules-jaunty** (hopefully that will include a wifi driver)

WHile you are on the internet, download the drivers for your wired network: get AR81Family-linux-v1.0.0.10.tar.gz from
[http://partner.atheros.com/Drivers.aspx](http://partner.atheros.com/Drivers.aspx)

Put all that stuff on a stick. Boot ubuntu again, copy it (temporarily) to your desktop. Then open a terminal and do:

```

cd Desktop
sudo dpkg -i *.deb
```

that will install the packages (someone correct me if im wrong here)

Then to compile the ethernet driver from source:

```
gunzip AR81Family-linux-v1.0.0.10.tar.gz
tar xvf AR81Family-linux-v1.0.0.10.tar
cd src
make
sudo make install

```

to load the driver try:

```
sudo modprobe atl1e
```

---

### Post by teh603 on 2009-09-23
If all else fails, there's always NDISwrapper...

---

### Post by hardawayd on 2009-11-14
> **thefuturism said:**
> Thanks for the replies!

**To beastrace91:**

I have the Aspire One D250. I've heard of trouble with UNR because it's set for a 11" screen while some of the net mini-laptops are 10.1" or less. If this claim is true, I don't believe it's the problem in my case. 
I have also heard that some people just install regular ubuntu on their netbook and then install the UNR packages so it LOOKS the same. Is this possible? (Also, will standard ubuntu run okay on a netbook? 


**To P4man:**

Sorry, I'll try to explain my situation more clearly.

1. I installed UNR to a partition on my SD card, while booting from my USB drive. The install finished fine, and everything was working okay (except my internet connection). Once I restarted my computer (I removed the USB drive for good, and changed the BIOS to boot from my SD card), GRUB loaded fine and I was able to choose "Load generic ubuntu" or whatever the first appearing option is to boot from. I select that and UNR loads okay, except for the (what I call) menu bar -- the bar at the very top that has the Time clock and such on it. That's the bar that disappears. I can restart and reboot many times but each time UNR loads, the bar will not show up - doesn't seem to load.

2. As I was saying above, GRUB does seem to load okay, and will boot into any of the ubuntu options. However, when I choose to boot via "Vista (Loader)" or "Windows XP", it just won't load. In the former option, it tells me something about a missing file and prompts me to restart. In the latter option, it just tells me that it is an invalid choice and bumps me back to the GRUB loader. On my first install of UNR, these buttons work though. I cannot figure out what's going on. 
I assume that GRUB is installed on the SD card as it does not boot if I remove the SD card (which is what I want so I can have a portable fully functioning operating system). My BIOS is set to boot from my SD card before my main internal hard drive. 

3. I'm confused as to what kind of output you want from me on the network card. How do I get that data through windows?

I have a Acer D250 with UNR-9.10, Ubuntu-9.10 and Xubuntu 9.10. They all work just fine.

---

