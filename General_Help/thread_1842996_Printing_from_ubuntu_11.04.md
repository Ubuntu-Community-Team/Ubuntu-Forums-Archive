---
title: "Printing from ubuntu 11.04"
date: 2011-09-12
forum: General Help
---

### Post by eastwest on 2011-09-12
Guys,

I hope you can help me with this printing problem....

There seems to be others who have or had the same or similar problems but I was unable to find any resolutions that were clearly applicable or usable.

I have a very simple Windows 7 network that consists of two desktops and one laptop (connected wireless) and one HP Officejet Pro 8500  A909a Printer (connected to one of the desktop USB ports). I have no problems printing from any of the computers when using Windows 7.

I recently installed Ubuntu 11.04 on the laptop in a dual boot setup and have been unable to print from Ubuntu at all.

It appears that the printer installation wizard does complete and installs the drivers. How-ever if I try to either print a test page or print from a program such as LibreOffice Writer I only get error messages.

I have attached a screenshot of the message from the attempted test page and the error from the word processor is even more vague like “CUPS server error” or no message at all. When I look at the Document Print Status it says “processing” but it never prints....

Regards

Bill

---

### Post by gandaran on 2011-09-12
> I have a very simple Windows 7 network that consists of two desktops and one laptop (connected wireless) and one HP Officejet Pro 8500 A909a Printer (connected to one of the desktop USB ports). I have no problems printing from any of the computers when using Windows 7.
I see from the screenshot you have a samba url for the network printer setup do you need that?
what I do on ubuntu is just enable show shared printers and share printers connected to this system in printers settings, then as long as the windows firewall is open for printer sharing printing from ubuntu is just as simple as if the printer was connected to the ubuntu machine.

---

### Post by jeffb99 on 2011-09-12
I have almost the exact same set up and problem when I replaced an aging Epson with a HP F340 (printer, scanner, copier).  Make sure the printer device name in your Device URI is EXACTLY the same as what's on your Windows machine.  I added spaces and made sure the names were identical.  Not sure but I think that's what solved that problem.
 
My problem now is that Ubuntu sends the print file to the Windows 7 spooler but the file is ridiculously large...15MB for a simple "Print Test Page".  Printing from my Win7 machine is fine.
 
I still can't print thru Ubuntu.   :(
 
Hope that helps.
 
--Jeff

---

### Post by drdos2006 on 2011-09-12
Originally Posted by hidesertmlb in the Server Section

1- in /etc/samba/smb.conf ensure the following was uncommented in the PRINTING section in [global]

load printers = yes
printing = cups
printcap name = cups

added the following to [printers]

use client driver = Yes

2- restarted samba: sudo /etc/init.d/samba restart

On the Win7 client

- Add a printer->Networked printer
- for the location, specified the printer via CUPS http. So in the location box, where UBUNTU is the hostname of the printer that's shared, and the shared name of my printer (Epson C120)

[http://ubuntu:631/printers/Epson_C120](http://ubuntu:631/printers/Epson_C120)

You can determine the shared name of your CUPS printer by going to your UBUNTU host that's sharing the printer, specifying the following URL:
[http://localhost:631](http://localhost:631)

Go to the PRINTERS tab, point to the queue name of the queue name of the printer that's shared, rt-click and display properties. This is the URL that will be used on your Win7 printer location, except "localhost" will be replaced with the hostname of your ubuntu host (in my case, "ubuntu").

- specify print driver to use on your Win7 machine and print a test page 
//////////////////////////////////////////////////////////////////////////
Re: Printing to CUPS server via Windows 7
Hah! Got it working.

Navigate to HKEY_CURRENT_USER\Printers\Settings
Add a DWORD "PreferredConnection" with a value of 0
New printer, network printer, printer isn't listed, etc
[http://ubuntu-server:631/printers/PrinterName](http://ubuntu-server:631/printers/PrinterName) in the location box and use the MS Publisher Imagesetter driver from the Generic category.

Voila! Native UNIX printing in windows...good bye smbd

Apparently Win7 and Server 2008 default to RPC IPP printing...the PreferredConnection setting reverts it to HTTP!
///////////////////////////////////////////////////////////////////////

regards

---

### Post by eastwest on 2011-09-12
Guys, 
 
Really appreciate the efforts to help....
 
I tried the suggestions made (to the extent that they apply to my problem) but, none of them changed the situation at all...
 
I still need help if any other suggestions are available..
 
Regards

---

### Post by psrdotcom on 2011-09-13
Does both the printer and ubuntu laptop are in the same network?

Please check that?

---

### Post by eastwest on 2011-09-13
As requested I checked to be sure all computers are on the same network...

---

### Post by eastwest on 2011-09-13
Are we going to have to give-up on this? :confused:

---

### Post by eastwest on 2011-09-16
Guys,
 
Just to let you know how much I appreciate your efforts to help with the print problem.
It is curious that printing is such a big problem for Linux , especially for Ubuntu one would have to assume that neither are ready for simple folk like myself....
 
Regards...

---

### Post by Muflon on 2011-11-03
I got the exact same printer this week and connected it directly to the router (Ethernet cable or wireless works).  I was then able to set it up on my Windows Vista PC and Ubuntu 11.10 laptop.  Both printing and scanning works effortlessly.  Incidentally the printer installation took about 2 minutes on Ubuntu and required no special setup.  It works straight out of the box.

Muflon

---

### Post by eastwest on 2011-11-03
Hello, folks....
 
I'm not sure what happend, there seems to be a post of mine that is missing. If it was operator error I apologize for leaving this thread open when in fact it was resoled by my upgrading to 11.10 in the same manner as Muflon in the latest post ...
 
It would be nice to know, if anyone knows, (for future reference) why 11.04 failed to work in the same way...
 
I do appreciate all your efforts to help me resolve the problem with 11.04 but in fact nothing suggested seemed to work or improve the situation....
 
Regards,
 
eastewst

---

