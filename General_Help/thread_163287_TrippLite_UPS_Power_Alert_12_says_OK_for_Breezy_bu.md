---
title: "TrippLite UPS Power Alert 12 says OK for Breezy but....."
date: 2006-04-20
forum: General Help
---

### Post by DE Retiree on 2006-04-20
I have a TrippLite Omnivs1000 UPS (with PowerAlert software that works when I run WinXP) that I have not been able to get working with Breezy.  The TrippLite site indicates that PowerAlert 12 will work with Breezy.  I tried downloading their software for linux from the TrippLite site, but I can't get it to install under Breezy.  I'm a newbie so perhaps I'm not running the appropriate installation process????  I download the tar.gz file, extracted it, followed the directions shown below, and double clicked on the .bin file.  Installer opens but after a couple of screens says can't find several files.  Any suggestions?  I tried searching the repositiories for TrippLite and Power Alert but did not find anything that looked appropriate.

I'm running a Dell 8400, 3.4gig, 2GB memory, dual boot with Ubuntu Breezy on a separate harddrive.  

Here is the info from the TrippLite site:
***************************
SUPPORTED OPERATING SYSTEMS 
***************************
 Note: PowerAlert is a 32bit application that will run on the noted 64bit Operating
 Systems. All 64bit supported operating systems have been tested on 
 AMD64 and Intel EM64T platforms only. 

 WINDOWS-
 Windows 98/Windows Me
 Windows NT Workstation with Service Pack 4 or later
 Windows 2000 Professional
 Windows 2000 Server
 Windows XP Home Edition
 Windows XP Professional (32 & 64 bit)
 Windows 2003 (32 & 64 bit)

 Linux-
 RedHat 4 enterprise (32 & 64 bit)
 Fedora Core 3(32 & 64 bit)
 Fedora Core 4 (32 & 64 bit)
 Ubuntu 5.1 (Breezy Badger) (32 & 64 bit)
 SUSE 9.3 (32 & 64 bit)
 SUSE 10.0 (32 & 64 bit)

 Unix-
 AIX 5.1,5.2 and 5.3 
 SCO 6.0 
 Sun Solaris (Intel) 10
 Sun Solaris (Sparc) 8,9,and 10

To install PowerAlert 12 for Linux from a download, do the following:
• Open a terminal window
• Change to the directory that the .bin file was downloaded to
• Type chmod 777 pa12_1Linux.bin
• Begin the installation by performing one of the following:
o Double-click the .bin file to begin installation
o Type ./pa12_linux.bin

...........................
Note - the file I downloaded is pa1243_setup.bin.tar.gz so that is what I used in the above instructions instead of "pa12_1Linux.bin"

Thanks for any suggestins,   ... DE Retiree

---

### Post by stuporglue on 2006-04-20
> Note - the file I downloaded is pa1243_setup.bin.tar.gz so that is what I used in the above instructions instead of "pa12_1Linux.bin"


That's a compressed file, so you need to decompress it. 
 
tar xzf pa1243_setup.bin.tar.gz

xzf == x(extract)z(gzipped file)f(this file)

In that file, or a folder in that file should probably be the bin file they mention.

---

### Post by DE Retiree on 2006-04-20
I did decompress the file.  Then I tried to run the .bin file as specified.  That is when I got the error message.  

Sorry if I was not clear in original post.

Thoughts????

DE Retiree

---

### Post by stuporglue on 2006-04-20
> I did decompress the file. Then I tried to run the .bin file as specified. That is when I got the error message.

Sorry if I was not clear in original post.

Sorry. I thought you meant you used foo.tgz instead of foo.bin ...didn't check the numbers close enough. 

> • Begin the installation by performing one of the following:
o Double-click the .bin file to begin installation
o Type ./pa12_linux.bin

My next guess would be that it needs some super user privs to run. Try "sudo foo.bin". If that throws errors, you should post the erorrs here, as they might be helpfull.

---

### Post by DE Retiree on 2006-04-20
Attached are 3 screenshots (I hope ... I have never tried to upload files before) that describe what happens.  Yes, I have tried this using su privileges.  And, there is no log file in the folder!

Help,      ... DE Retiree

---

### Post by stuporglue on 2006-04-20
I don't know what to tell you except....

1) Do you have the latest Java or the Java they recomend (I see some Java errors in the terminal there)

2) If the folder where the error log is supposed to be put doesn't exist, create the folders, then run it again. Maybe it can't write the log because the folders don't exist.

---

### Post by rvergara on 2006-04-20
I have an omni 500 ups and I recently installed power alert 12 under breezy and it works fine

Upon decompressing the file do the following:

&#8226; Open a terminal window
&#8226; Change to the directory that the .bin file was downloaded to
&#8226; Type chmod 777 pa12_1Linux.bin
&#8226; Begin the installation by performing one of the following:
o Double-click the .bin file to begin installation
o Type ./pa12_linux.bin

In order for the file to be executed you need java installed in Breezy (J2SE 1.4.1 or above) since power alert is a java application.

Upon installation you need to type

sudo pa console

and then within pa go to settings, device and define your UPS

I hope this helps.

Regards

Ramiro

---

### Post by stuporglue on 2006-04-20
DE Retiree, <--EDIT: Sorry Ramiro

1) Post the console output from when you run the program.

2) Is your java installed correctly? What happens when you type  "echo $JAVA_HOME" "which java" and "java --version". Can you run other Java programs?

---

### Post by rvergara on 2006-04-20
I assume your comments were not intended for me but for DE Retiree.

My Power Alert works just fine.

Ramiro

---

### Post by DE Retiree on 2006-04-21
Well folks, I'm making progress but now have another problem.  I had to uninstall Java and then reinstall (I used automatix to get a later Sun version).  Was able to install PowerAlert and run the console using the sudo pa console.  New problem is that when I start up the PA console, I can't figure out how to configure the settings ... it will not autodetect.  Also, I'm running firestarter.  I made a new rule for opening ports 3664 and 3665 according to TrippLite FAQ's but still not able to connect.  See attached screenshot of terminal window error message and the PA setting screen.

Thanks for all your help so far.  I feel a bit dumb at this point since I can't figure this out.  I'm probably doing something stupid!

DE Retiree

---

### Post by DE Retiree on 2006-04-21
Sorry, forgot to upload screenshot.  Here it is.

---

### Post by rvergara on 2006-04-21
just go to settings-> devices, click add device.

If you have a db9 connector (as I do), then enter contact closure (nono) in the protocol field.

More info on slide 13 of:

[http://www.tripplite.com/support/download/PA12/install_guide/frame.htm](http://www.tripplite.com/support/download/PA12/install_guide/frame.htm)

Unfortunately you need IE for browsing the presentation. However with just setting the right protocol it should recognize your UPS.

Regards

Ramiro

---

### Post by DE Retiree on 2006-04-21
I now understand why I could not get PowerAlert to work with my system.  I call the TrippLite tech support and found out that my UPS does not work with USB support.  He said they have been working for a few years at TrippLite to get USB support for linux but so far they have not done it.  Oh well, maybe this will help someone else to know that.  Thus I thought I'd make this posting.

Thanks for everyone who offered suggestions to me and tried to help.  I should have thought about calling TrippLite sooner and not have wasted your time. :-? :-? 

DE Retiree

---

### Post by mexlinux on 2006-07-07
Do you mean: not any Tripp Lite UPS supports usb on linux???

---

### Post by moopere on 2006-07-16
> **DE Retiree said:**
> I now understand why I could not get PowerAlert to work with my system.  I call the TrippLite tech support and found out that my UPS does not work with USB support.  He said they have been working for a few years at TrippLite to get USB support for linux but so far they have not done it.  Oh well, maybe this will help someone else to know that.  Thus I thought I'd make this posting.

Thanks for everyone who offered suggestions to me and tried to help.  I should have thought about calling TrippLite sooner and not have wasted your time. :-? :-? 

DE Retiree

Hmm.  Linux support from UPS makers is spotty enough thats for sure and adding usb support under linux by most manufacturers is just laughable.

..however, in cases like this, has anyone tried a cheap off the shelf usb-serial converter?  Might be that the "A" versus "B" USB plug thing is the wrong way around?

Cheers,
Craig

---

