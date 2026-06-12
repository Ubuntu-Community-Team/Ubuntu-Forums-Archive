---
title: "Stuck at 'Checking battery state'"
date: 2010-10-26
forum: General Help
---

### Post by MagnusWi on 2010-10-26
Tried to search for a similar problem, but did not find anyting that I could relate to. Anyway:

Updated from 10.04 to 10.10 about 2 weeks ago and it worked just fine until today. After rebooting, it's stuck at "* Checking battery state" and nothing happens. I've tried with power cord inserted/out and without battery but with no success. What I did before rebooting was that I tried to fix my iphone tethering problems with the following commands:

[I]# sudo apt-get uninstall gvfs ipheth-dkms ipheth-utils
# sudo apt-get install gvfs ipheth-dkms ipheth-utils[/I]

and also a system update. And here I am. Anyone knows what could have happened? I'm on a Acer Travelmate 8371.

Thanks.

---

### Post by Barajqial on 2010-10-26
I had A similar problem after moving from 10.04 to 10.10 with the online update,  it may have something to do with that.

---

### Post by hxcjonnysniper on 2010-11-13
bump.
same problem.
=[

---

### Post by Replicounts on 2010-11-14
Here's a FIX that worked for me, to recover from the "Checking battery state" problem. My guess is that it will work for most systems.

The key is that when this problem happens, you CANNOT "Try Ubuntu" and run 10.10 from a CD; the system just hangs. But I could "Install Ubuntu" from the same CD, and it worked. And then the problem was fixed.

Probably what's going on is this: At the end of the install process for 10.10, a bunch of packages including some "hardware configuration" get downloaded (this took about an hour on my slow WiMAX Internet connection, so a fair amount of software is coming in). Obviously this software isn't available when you try to run Ubuntu from the 10.10 CD itself (if it were, it wouldn't have to be downloaded). So apparently something getting downloaded and installed in this process is fixing the problem.

(Needless to say, once the fix is in, then 10.10 again works when running from the same CD.)

Notes:

* I like to erase everything and re-install when there's a problem. So how do you get your data files off the 10.10 system that's dead in the water? Fortunately, the 10.04.1 disk does run when the 10.10 doesn't, so you can copy your files to an external disk, flash drive, or whatever.

* Here's how I trashed my 10.10 in the first place (in case this helps a support team reproduce the problem). The built-in FTP wasn't working very well (under Places, Connect to Server); it worked to upload or download a file, but when downloading a folder that's a whole website, it only downloaded a handful of files and folders and then Nautilus stopped indefinitely. This happens every time. So I used apt-get to remove and then re-install Nautilus; oddly enough, the new one coming in used about half a meg less memory. But then 10.10 didn't boot at all, but stopped at the "Checking battery state" point (though you don't see the message usually -- in my system, there's a blinking underscore that normally appears in the upper left hand corner of the otherwise-blank screen during bootup, but with the problem, it just keeps blinking and the boot does not finish.

* Incidentally, after the complete re-install of 10.10, the FTP isn't any better. It's good enough for minor website maintenance, however.

* It's disappointing that Ubuntu 10.10 cannot always run from the CD alone, but depends on other software being in the machine. This could be a security problem. Is there any way this dependency could be eliminated? (10.04 already doesn't have this particular dependency, so at least it shouldn't be too to hard to fix.)

* Incidentally, I'm running the 10.10 32-bit Laptop version on a netbook (not the Netbook version), with an external CD/DVD drive. The netbook is an Eee 1005HA.

--
John S. James
[www.RepliCounts.org](www.RepliCounts.org)

---

### Post by lorentz.yip on 2011-02-28
I have the same problem after installing the ATI/AMD proprietary driver on my thinkpad w500 notebook. After having done some tests and settings in the BIOS, I found that it could be solved by setting the "Switchable graphics" option to "discreted" in the BIOS. Hope this could give you a clue and help.

---

### Post by zenwalker on 2011-03-01
Its the updated packages causing the problem. I did it on virutalbox. Then stuck up with the same state.

---

### Post by watersoup on 2011-04-22
Guys !!!

I got a solution... same thing happened to me... may be while installing some package it uninstalled gnome-power-manager.

just get into shell by keying in ctrl+alt+F5 or F6 it will take you to login prompt 

get in and type

sudo apt-get install ubuntu-desktop

Volla !!!

everything is fine... you get back your gui.

---

### Post by sksagar on 2011-06-04
> **watersoup said:**
> Guys !!!
 
I got a solution... same thing happened to me... may be while installing some package it uninstalled gnome-power-manager.
 
just get into shell by keying in ctrl+alt+F5 or F6 it will take you to login prompt 
 
get in and type
 
sudo apt-get install ubuntu-desktop
 
Volla !!!
 
everything is fine... you get back your gui.
 
I tried with sudo apt-get install ubuntu-desktop but sudo is not working and message is sudo wil find in "/usr/bin" and PATH environment variable in not set

---

### Post by Lovelyhard on 2011-08-22
YMMD!

After some installation my Ubuntu in a VirtualBox refused starting the graphical IF and remained in the state "Checking battery state". 
Reinstalling the ubuntu-desktop did the trick!

---

### Post by KSharma on 2011-12-24
I am running Ubuntu 11.10 64bit edition and encountered the same problem after I to played around with display managers. For me the fix was simple -

Open "/etc/X11/default-display-manager" and make sure that you have the full path to the display manager. For me this was:
/usr/sbin/lightdm

Note: I think the contents of the file will change to a path to GDM for older Ubuntu version users and for those people who are using gnome display manager.

---

### Post by ponsfrilus on 2012-03-08
I got this stuck after a X11 update,. Get ride of it by removing xorg.conf
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old && sudo rm /etc/X11/xorg.conf

my 2cents

---

### Post by kh.iftikhar@gmail.com on 2012-04-12
I had the same problem, so i tried ctrl+alt+f5 and logged in and tried running 

 - > lightdm start

But I got the message that I don't have enough disk space to run display manager. So I checked my home partition and it was completely full. The reason was that I had .xsession-errors file extremely large i.e. 146GB. So I removed the file and restarted the system and after that everything works perfectly fine.

---

### Post by cspdjp on 2012-05-25
I have the same problem but for me when I boot up it tells me I have to reconfigure my graphics car then when I push ok it says checking battery

---

### Post by Jack Kelly on 2013-01-16
I just had the same problem on 12.10 64-bit.

I pressed CTRL-ALT-F1 and logged in and then typed "sudo reboot" to reboot and after the restart, everything was fine.

---

### Post by fontipex on 2013-03-13
tried many, many things...  and what KSharma wrote above finally made the break-through...    after pressing Alt-F5 and loggin in, i could verify that /etc/X11/default-display-manager indeed contained just "lightdm", and changing it to "/usr/sbin/lightdm" made system-boot work again...   thanx a lot for your hint, KSharma!!!

---

### Post by supertramp.1607gm on 2014-02-11
i got the same error, as a workaround i went to a text virtual  console (cntl + Alt + F1) and logged in with the admin user.
then
ps -aef | grep lightdm 
sudo kill -9 <process id of the lightdm process>
if there are multiple lightdm process kill each one - it will automatically take you to your GUI console, if not after killing all your lighttdm processes do a 
sudo lightdm start

---

### Post by oldos2er on 2014-02-11
Old thread closed.

---

