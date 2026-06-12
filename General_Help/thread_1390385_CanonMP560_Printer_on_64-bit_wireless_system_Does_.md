---
title: "CanonMP560 Printer on 64-bit wireless system Does Not Work"
date: 2010-01-25
forum: General Help
---

### Post by jwvraets on 2010-01-25
It seems that when I asked this last week the thread I posted in was likely a bit tired and I did not receive any responses/suggestions, etc. As a result I am posting this anew to see if I can get some help in something that has really started to get to me .

I am hoping someone can steer me in the right direction because I am trying to install the MP560 onto a 64bit (AMD Athalon II x4) Ubuntu 9.10 (fully updated) and having no luck even using the process from jmcvey (msg#10 in this thread, dated 13 Nov 2009:)

    [http://ubuntuforums.org/showthread.php?t=1264928](http://ubuntuforums.org/showthread.php?t=1264928)

in which he outlined the following process ( I refer to this message as jmvey #10):

= START = = = = = = = = jmcvey - 13 Nov 2009 = Re: printing with Canon Pixma MP560= = = =

If you check the Canon Asian site, they have drivers available (although the MP560 is the MP568 on the site; once you get to the driver page it states "MP560").

Actually, here:

[http://support-asia.canon-asia.com/P...os&ca_os=Linux](http://support-asia.canon-asia.com/P...os&ca_os=Linux)

Look for:

MP560 series IJ Printer Driver Ver. 3.20 for Linux (debian ...

and download the file.

Use Archive manager to extract the file and then look inside the directory it created. There should be a "packages" directory with 2 .deb files.

You can use dpkg to install the files (install the common file first) and if you're on a 64-bit system use the force option to make it work (that's why I had to use dpkg in the first place).

So you issue:

sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb

Then use the Printer configuration tool to add the new printer.

I use the Pixma over it's wireless connection and the printer tool found it and installed it without a problem once the steps above were done. Printed a test page and then a couple of documents. So far it handles the basic printing tasks without a problem.

Haven't tried the other software available on that site (that's for this weekend) but looks like there's a scanner package as well that I'll see if I can get working.

Jer


= End = = = = = = = =

This is a process that others seem to find works or so it would seem and nobody seems to be saying it doesn't.


So ....Here is what I did...


I initially installed the printer using a Windows Vista laptop using a USB cable. Systems was fully operational.


I installed the printer on an AMD Athalon II quad core (i.e. 64-bit architecture) using a USB cable and it did work for printing (but not for scanning) after installing the drivers as per the process described by jmcvey #10.


I decided to change over to a wireless link rather than USB and in preparation for that I gave the printer a fixed IP address using the printers internal web page tools. I set it to a fixed IP address (192.168.15.203) and it is fully operational from Vista.


I reran the driver installation on the Ubuntu machine as per jmcvey #10 in hopes that the re-installation would clobber/replace the previous USB based installation (just in case).


The output of the forced re-installation as per jmcvey #10 was:
= = = = = =
jwvraets@atilla:~$ cd /data/sys_updates/temp_mp560/print
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ ls -la
total 1824
drwxr-xr-x 2 jwvraets jwvraets 4096 2010-01-20 16:42 .
drwxr-xr-x 4 jwvraets jwvraets 4096 2010-01-20 16:41 ..
-rw-r--r-- 1 jwvraets jwvraets 103882 2009-09-27 21:53 cnijfilter-common_3.20-1_i386.deb
-rw-r--r-- 1 jwvraets jwvraets 1742604 2009-09-27 21:53 cnijfilter-mp560series_3.20-1_i386.deb
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
[sudo] password for jwvraets:
dpkg: warning: overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
(Reading database ... 214093 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.20-1 (using cnijfilter-common_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jwvraets@atilla:/data/sys_updates/temp_mp560/print$ sudo dpkg -i --force-architecture cnijfilter-mp560series_3.20-1_i386.deb
dpkg: warning: overriding problem because --force enabled:
package architecture (i386) does not match system (amd64)
(Reading database ... 214093 files and directories currently installed.)
Preparing to replace cnijfilter-mp560series 3.20-1 (using cnijfilter-mp560series_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-mp560series ...
Setting up cnijfilter-mp560series (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
jwvraets@atilla:/data/sys_updates/temp_mp560/print$


= = = = = =
I can ping the printer using a terminal window on the Ubuntu machine. I then accessed the printer's buit-in web page at its URL (i.e. the fixed IP of 192.168.15.203) and it displays properly in Firefox on both the Vista and the Ubuntu systems.


When I then try to find the printer using:
System > Administration > Printing
I get “Printing configuration localhost” window as expected. No printers are listed (I deleted the printer before I started this whole re-installation process). Then I clicked on the “New” button and it begins to search for printers. After a short time a window is brought up with the title “New Printer” a a window on the left which labeled “Select Device”, below which a window lists the options. These are grouped under a label “Devices” as LPT #1, Serial Port #1, and other in the first group and an expandable entry labeled “Network Printer”. Clicking on the “Network Printer” it expands to the following options: Find Network Printer, AppSocket/HP JetDirect, Internet Printing Protocol (ipp), LPD/LPR Host or Printer, and Windows Printer via Samba.
From that list I selected “Find Network Printer” and a Network Printer Host data entry area is provided into which I entered the fixed IP address of the printer (i.e. 192.168.15.203) and then I click on the adjacent Find button. A “Queue” selection list window is presented with the only option being “PASSTHRU” and a small “Connection” expansion button is provided at the bottom of the window (options are a variety of LPD?LPR , queue types, covering LPT and Com options) the default of which is the first entry LPD/LPR queue 'PASSTHRU'. I left that alone and hit the “Forward” button.
A new window appears with the title “New Printer” and it asks me to choose a driver. Its options are:

   1. Select printer from database
   2. Provide PPD File
   3. Search for printer driver to download.

The default is “Select printer from database which I kept. The text below the options refers to “The foomatic printer database...” and then lists manufacturers. I selected Canon and the clicked on forward to view a list of models which do not included the MP560 (no surprise there).

That was last week and the above is (essentially) the body of my post in the thread mentioned above.

Today, I did some more diging and as a result I deleted the two files:
   /usr/share/cups/model/canonmp560.ppd
which is a link to the actual file:
   /usr/share/ppd/splix/canonmp560.ppd

and reran the installation instructions in mcvey #10. Doing so restored the files and hoping these were fresh/clean versions. I redid the routine to discover the printer. The results did not change. Cannot find it.

I then tried to scan the ports on the printer and found the following:

   Port #    Status    Name:
   80        open    www
   139        open    netbios_ssn
   515        open    printer

Based on this I tried to add the port number (i.e. 515) to the printers IP address. Still unable to find it.

And there I sit.

I apologize for the lengthy description but I hope it is helpful in tracking down where/how I went off the rails in this exercise. I bought the printer based on the information in the list of printers at:

   [http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP560](http://www.openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP560)

which (combined with the main list page for Canon) gave me a high level of confidence it would be viable. Well it may be in some limited set of circumstances, but certainly not in my case. Perhaps this is a cautionary tale?

And BTW this is a dual boot setup with Windows XP which has the Canon drivers installed and works flawlessly on the network (in case you wondered).

With all that said, is there anyone who has successfully installed the drivers for wireless use on a 64-bit system identify what I am doing wrong and (if possible) suggest how I can get this on track? Help would be very much appreciated.


(and I have not even started on the scanner section yet...)

JW

---

### Post by jwvraets on 2010-01-26
Is there anyone with any help to offer? 

JW

---

### Post by jwvraets on 2010-01-27
Anybody? I am dying here.

JW

---

### Post by jwvraets on 2010-01-30
Does this mean nobody has been able to do this? If so why is it listed as working perfectly in the Open Printing database?

Somebody must be able to help me here - Please....

---

### Post by bakinsoda on 2010-08-03
Hi.  Just recently migrated back to Ubuntu and ditched Mac OS X.  Did you ever get this working in a 64 bit Ubuntu machine?  I really can't see why it wouldn't work -- the compilation occurs on a different architecture thats all.

---

