---
title: "Zinio Reader 4 for Ubuntu"
date: 2012-06-06
forum: General Help
---

### Post by Welly Wu on 2012-06-06
I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB Solid State Drive running Ubuntu 12.04 64 bit Long Term Support.  installed Adobe Flash, Air, and Reader. I paid for several Zinio digital magazines and Linux Format requires that I download and install Zinio Reader 4. When I visit the Zinio website at [http://www.zinio.com](http://www.zinio.com) and I try to download and install Zinio Reader 4, it stays stuck at the INITIALIZING screen and it does not launch Adobe Air to install Zinio Reader 4. I tried this using Google Chrome, Mozilla Firefox, and Opera web browsers with the same result.

How do I get Adobe Air to launch so it will install Zinio Reader 4 in Ubuntu 12.04 64 bit Long Term Support on the Zinio website?

---

### Post by Welly Wu on 2012-06-06
I downloaded the Zinio Reader 4 Adobe Air installation file and I used Adobe Air to install it. It works. I can read my all of my Zinio digital books and magazines now.

---

### Post by jeffmings on 2012-07-08
FYI, you can grab the Zinio 4 Adobe Air binary at:
[http://imgs.zinio.com/zinio-reader/installers/ZinioReader4.air](http://imgs.zinio.com/zinio-reader/installers/ZinioReader4.air)

---

### Post by aashish351 on 2012-07-10
Hi, I am a first time Linux & Ubuntu user. I am trying to completely move over to Linux and don't want turn back this time.

I read a lot of magazines through Zinio. I have Wine installed and Adobe AIR version 3.3 for windows too. I have also downloaded the .air application and installed it in Adobe AIR. But when I ran the Zinio Reader first time, it showed me the Terms & Conditions with an option to accept / reject. After accepting it, I waited but it did not move forward. I turned off everything, restarted and ran the application again. This time & all the times onwards it just hangs on the opening screen with Zinio Reader 4 logo window on top of the Black background. It does not move forward to where I can put my library username & password and access my library.

Any ideas....?

---

### Post by Welly Wu on 2012-07-10
You need to download the old version of Adobe Air for Linux and re-install it:

[http://helpx.adobe.com/air/kb/archived-air-sdk-version.html](http://helpx.adobe.com/air/kb/archived-air-sdk-version.html)

You are looking at Adobe Air version 2.60 for Linux.

Make sure that you remove Adobe Air prior to re-installing it in the Ubuntu Software Center. Perform an Update Manager prior to launching the Ubuntu Software Center to make sure that you will be able to remove the current version of Adobe Air.

Re-install Adobe Air:

chmod +x AdobeAirInstaller.bin

sudo sh ./AdobeAirInstaller.bin

Accept the license terms and conditions

Download the Zinio Reader 4 Adobe Air installation file:

[http://imgs.zinio.com/faq/zr4.htm#manualinstall](http://imgs.zinio.com/faq/zr4.htm#manualinstall)

Find and download the Zinio Reader 4 Adobe Air installation file

Double click on the icon and launch it using Adobe Air to install it. Accept the license terms.

You should be able to login to your Zinio account now. Login and download your Zinio magazines.

It worked for me.

---

### Post by Welly Wu on 2012-07-10
Let me know if you are having problems. You need to download and install the Adobe Air for Linux software application. You can not use the Adobe Air for Microsoft Windows software application using WINE. I have Codeweavers CrossOver for Linux 64 bit 11.2.0 and I use the Adobe Air for Linux software application. You must download and install the Zinio Reader 4 Adobe Air installation file and install it using Adobe Air for Linux. Then, it will work properly. You will be able to log in to your Zinio account and download your Zinio magazines.

I subscribe to Android Magazine, Linux Format Magazine, MacWorld Magazine, Poets & Writers Magazine, Stereophile Magazine, and Tone Audio Magazine through Zinio. I also subscribe to Laptop Magazine, The Absolute Sound Magazine, Full Circle Magazine, and Playback Magazine, but those use the Adobe .PDF format and I visit the publisher's websites to download the latest monthly issues. I use Adobe Reader for Linux to read those magazines.

I used to be the Help Desk and Support Technician at New Jersey Institute of Technology in Newark, New Jersey 07102 in the United States of America. I will provide you with Help Desk and Support for this single issue because you are a fellow Ubuntu and Zinio user for free.

---

### Post by aashish351 on 2012-07-10
Thanks Wu!

I really appreciate you helping me out with this.

My .bin file is in the downloads folder. I ran the commands in terminal window as suggested by you. This is the error I am getting:

aashish351@aashishmahindru:~$ chmod +x AdobeAIRInstaller.bin
chmod: cannot access `AdobeAIRInstaller.bin': No such file or directory
aashish351@aashishmahindru:~$ chmod +x /home/aashish351/Downloads/AdobeAIRInstaller.bin
aashish351@aashishmahindru:~$ sudo sh ./AdobeAIRInstaller.bin
[sudo] password for aashish351: 
sh: 0: Can't open ./AdobeAIRInstaller.bin
aashish351@aashishmahindru:~$ sudo sh /home/aashish351/Downloads/AdobeAIRInstaller.bin
/home/aashish351/Downloads/AdobeAIRInstaller.bin: 1: /home/aashish351/Downloads/AdobeAIRInstaller.bin: Syntax error: "(" unexpected
aashish351@aashishmahindru:~$

---

### Post by Welly Wu on 2012-07-10
I apologize. I made a small mistake.

Type in this command exactly:

sudo ./AdobeAIRInstaller.bin

This will launch the Adobe AIR installer for GNU/Linux properly.

---

### Post by aashish351 on 2012-07-10
If I type the command without 'sh':

aashish351@aashishmahindru:~$ sudo ./AdobeAIRInstaller.bin
[sudo] password for aashish351: 
/tmp/air.f76ipu/setup: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
aashish351@aashishmahindru:~$

---

### Post by Welly Wu on 2012-07-10
What version of Ubuntu did you install and are using?

I did a search of the missing file that you reported and I found this Linux Questions thread:

[http://www.linuxquestions.org/questions/linux-software-2/error-while-loading-shared-libraries-libgtk-x11-2-0-so-0-cannot-738695/](http://www.linuxquestions.org/questions/linux-software-2/error-while-loading-shared-libraries-libgtk-x11-2-0-so-0-cannot-738695/)

Type this in exactly:

sudo apt-get install libgtk2.0-0

and then, type in this exactly:

sudo apt-get reinstall libgtk2.0-0

Tell me what happens next.

---

### Post by aashish351 on 2012-07-10
This is what happens:

aashish351@aashishmahindru:~$ sudo apt-get install libgtk2.0-0
[sudo] password for aashish351: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtk2.0-0 is already the newest version.
The following packages were automatically installed and are no longer required:
  libipc-run-perl libnet-ip-perl libunistring0:i386 diffstat libnet-dns-perl
  libclone-perl libsub-name-perl libparse-debianchangelog-perl
  language-pack-kde-zh-hans-base libio-pty-perl compiz-plugins-extra
  dh-apparmor libgomp1:i386 firefox-locale-zh-hans libcroco3:i386
  libio-string-perl language-pack-kde-en kde-l10n-engb libgettextpo0:i386
  libnet-domain-tld-perl libemail-valid-perl language-pack-zh-hans-base
  html2text libapt-pkg-perl libclass-accessor-perl kde-l10n-zhcn
  language-pack-zh-hans language-pack-kde-zh-hans libmail-sendmail-perl
  language-pack-kde-en-base libsys-hostname-long-perl libdigest-hmac-perl
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.
aashish351@aashishmahindru:~$ sudo apt-get reinstall libgtk2.0-0
E: Invalid operation reinstall
aashish351@aashishmahindru:~$

---

### Post by Welly Wu on 2012-07-10
Type this in exactly:

sudo apt-get install ia32-libs-libnss3 ia32-libs-gtk

Tell me what happens exactly.

---

### Post by Welly Wu on 2012-07-10
Which specific version of Ubuntu are you using and which architecture are you using?

---

### Post by Welly Wu on 2012-07-10
After you post what happened, type this in exactly:

sudo ./AdobeAIRInstaller.bin

Tell me exactly what happens from this specific command in a separate reply post.

---

### Post by aashish351 on 2012-07-10
aashish351@aashishmahindru:~$ sudo apt-get install ia32-libs-libnss3 ia32-libs-gtk
[sudo] password for aashish351: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'ia32-libs' instead of 'ia32-libs-gtk'
E: Unable to locate package ia32-libs-libnss3
aashish351@aashishmahindru:~$

---

### Post by aashish351 on 2012-07-10
I am using Ubuntu 12.04 Precise

---

### Post by aashish351 on 2012-07-10
aashish351@aashishmahindru:~$ sudo ./AdobeAIRInstaller.bin
/tmp/air.XXEVjI/setup: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
aashish351@aashishmahindru:~$

---

### Post by Welly Wu on 2012-07-10
Please launch the Ubuntu Software Center and install the following software applications:

Adobe Flash version 11.2 for Linux
Adobe Reader 9.5.1 for Linux

Then, type this in exactly:

sudo ./AdobeAIRInstaller.bin

If this does not work, then contact me again in this thread.

---

### Post by aashish351 on 2012-07-10
flash was already installed and i installed adobe reader 9.5.1

This time i got a pop up saying... running 32-bit AIR 2.6 on 64-bit Ubuntu has not been tested, but can be run if the required 32 bit libraries and packages are installed. there was a link given to explain how which i tried but could not install getlibs-all.deb

---

### Post by Welly Wu on 2012-07-10
You need to show me all of your information for me to be able to help you. Please provide me with the link.

What brand, make, and model of computer are you using?

At this point, I am running low on available solutions for you to try. My best recommendation to you is to re-install Ubuntu 12.04 64 bit Long Term Support bare metal on your computer from scratch. I simply don't know what else you have done or changed in Ubuntu with your current installation to pin point whether it has any bearing on this specific problem with Adobe AIR. Make sure that you backup your personal and private data and you test your backup before you choose to re-install from scratch. This should resolve the problem if you take my advice.

---

### Post by aashish351 on 2012-07-11
This is the screenshot of what happens now.

I am using Sony Vaio VGN-Z58GG. I really appreciate your help and understand that being a first time ubuntu user, I may not be able to be of much help to get this resolved. I will move towards re-installing Ubuntu. What is the difference between 12.04 Precise Pangolin & LTS

---

### Post by aashish351 on 2012-07-11
I posted the screenshot but it is not visible. 

Anyway... I am going to re-install Ubuntu from scratch and will try and get the LTS version.

Really don't want to go back to Windows this time!

---

### Post by Welly Wu on 2012-07-11
Ubuntu 12.04 64 bit Long Term Support is Precise Pangolin.

You should re-install Ubuntu from scratch. This should solve your problems.

---

### Post by Welly Wu on 2012-10-04
[http://helpx.adobe.com/air/kb/troubleshoot-encrypted-local-storage-els.html](http://helpx.adobe.com/air/kb/troubleshoot-encrypted-local-storage-els.html)

---

### Post by wolverinepr on 2013-01-21
Hi!

I am using Ubuntu 12.10 64-bits. I followed your instructions step by step. However, when launching Zinio4 it only shows the blacs splash screen only. I am not presented with the logon informatino to access my Zinio Account. I have installed Adobe AIR 2.6 for Linux. I installe DestroyTwitter and it runs perfectly. 

Is there any other missing configuration step to make Zinio4 works.

---

### Post by proze on 2013-01-24
I have the same problem... just a black & grey screen and nothing else. Would be great if I could get it to work. Anyone?

EDIT: I'm using XFCE and it turns out I was getting the error "Unknown desktop manager. Only Gnome and KDE are supported.". A quick 'export GNOME_DESKTOP_SESSION_ID="xfce"' fixed it for me and all is well. It's still crap that Zinio rely on AIR, but there you go.

---

### Post by cobra2411 on 2013-04-09
Got it working on 12.10 64bit. 

I used gksudo ./AdobeAIRInstaller.bin vs sudo because my multi-monitor setup was unhappy with just using sudo. 

I also had issues with the KDE/Gnome keyring, so I did the following. 

$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0 /usr/lib/libgnome-keyring.so.0
$ sudo ln -s /usr/lib/x86_64-linux-gnu/libgnome-keyring.so.0.2.0 /usr/lib/libgnome-keyring.so.0.2.0

Then I just double clicked the .air file and it installed. The first time the reader loaded it was a blank black screen but I closed it and when I reopened it it worked fine. 

Thanks guys

---

