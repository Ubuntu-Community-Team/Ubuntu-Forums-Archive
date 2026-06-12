---
title: "Frustrated with Printer Problem"
date: 2009-12-23
forum: General Help
---

### Post by exstarguy on 2009-12-23
I have a two-computer home network with one Ubuntu 9.10 Linux box and one Windows Vista box, along with a Brother MFC-7440N network printer.  Several days ago the network printer disappeared from the list of available printers on the Linux box.  The printer continues to work fine from the Windows box, so it is not a printer issue.  The root cause may have been my use of the "Computer Janitor" function to remove "unneeded" files - I can't think of anything else unusual.

Anyway, I tried to reestablish the printer connection by asking Ubuntu to search for network printers (I specified its static IP address).  It quickly found the Brother MFC-7440N (BRN008077084144).  I accepted the recommended drivers for this model (it actually uses an MFC-7225N, which I suppose is an earlier model).  I then select the printer icon, and under the Properties tab ask it to print a test page.  Fails immediately, with the message "Stopped - Unable to Locate Printer BRN008077084144".  Then it attempts to diagnose my problem, and tells me to check the "Enable" box on the Policies tab.   Try to print a test page and fails immediately again.  Diagnostic process now hangs.  Then I close the diagnostic box and look back at the Policies tab - the "Enable" box is not checked.  I have also tried turning off the firewall via Firestarter - same problem.  I tried downloading the recommended drivers from the Brother web site, including the file "MFC7450.ppd" into /usr/share/cups/model.  One time I tried selecting this .ppd file for a driver - same error.

I'm not a system administrator type - just want to have my network printer back.  Does anyone have any ideas what I have done wrong, or what I can do to try and narrow down the problem?  This is frustrating, since the printer worked fine for a year!

---

### Post by Dazed_75 on 2010-01-05
I had a very similar problem tonight.  I recently did a clean install of 9.10 to a desktop and a laptop on the same home network.  I have been using Ubuntu and this printer for years and it has ALWAYS been easy to set up under Ubuntu and operated trouble free.  I have the printer working for both now but it was a PITA getting there.  

I actually got it working several times using different techniques and I have no way of knowing what will work for you.  You should not have to do all these things, but each one has a chance to solve it for you.

[LIST]
[*]My printer showed up under the Networked heading as two different names.  One (the name I have always used in the past) showed using a binary queue and no connection information.  The other name showed a connection dropbox when selected which showed something like dnssd.... and that one worked.
[*]At one point, I found the dnsmasq in my router had been turned off (I now remember doing it).  Turning that back on allowed me to ping it by name and one solution was that.
[*]I did have to check the enable box like you said and I also unchecked the sharing box since neither computer was acting as a print server for other machines.
[/LIST]

It surely seems to me that something got broken in 9.10 wrt network printers!

---

### Post by Jose Catre-Vandis on 2010-01-06
This might help

[http://ubuntuforums.org/showthread.php?t=1373928](http://ubuntuforums.org/showthread.php?t=1373928)

---

### Post by Scunizi on 2010-01-16
I've been struggling with my 7440n since 8.04 release.. with 9.10 I parsed and followed the Brother instruction for installation on the network.. no issues.. I can even use xsane without loading it as root.  The only thing I haven't got working is the fax portion which might just be a minor thing since my usb US Robotics faxmodem also stopped on this release.. The driver supplied by brother off their site is specific for the 7440.  I also thought that the 7450 or other driver was correct but after loading cups through [http://localhost:631](http://localhost:631) and running through the modification I found the right driver out of order in the list of brother drivers.. It's at the bottom.  I've attached a copy of my instructions that I"ve written up for the next upgrade :(.. maybe it will help.

---

### Post by tshanks on 2010-02-09
For those without Forum accounts, I am pasting the contents of the other user's text file here.

I have corrected some "typos" in the commands.

> How To Install a Brother MFC-7440N on the LAN Network

I did this on a fresh install of Kubuntu 9.10 64 bit.  My results are very encouraging since this is the first time I've been able to get the scanner working with xsane without having to start it with sudo.

This must be done on the command line.

If you have a 64 bit system then do the following, if not leave out the 32bit libraries.
sudo apt-get install ia32-libs **or** lib32stdc++
 
And everybody do these-
sudo apt-get install psutils sane-utils

sudo mkdir /usr/share/cups/model
sudo mkdir /var/spool/lpd

Connect the Printer to the Network and turn on.  Setup the printer on a static IP address, hopefully outside the DHCP range that is set in your router.

Printer Install--

sudo aa-complain cupsd

sudo dpkg -i --force-all <lpr driver name>
sudo dpkg -i --force-all <cups wrapper>
  To check .. dpkg -l | grep Brother

Open file /etc/printcap
  sudo nano /etc/printcap
    Edit the file in the following 2 line listings.. they are on the same line
    Even though the Brother site shows a "\" at the end you don't need it. Just leave what's there at the end
      :rm=<ip address of your printer>
      :rp=lp

Check to see if the Printer is installed
  dpkg -l | grep Brother

Scanner Install

sudo aa-complain cupsd

sudo dpkg -i --force-all <driver name>
  note: I did not install the brscan-skey file..

To check the driver
  sudo dpkg -l | grep Brother

Fax Install

sudo aa-complain cupsd
sudo dpkg -i --force-all <fax lpr driver name>
sudo dpkg -i --force-all <fax cupswrapper>

Note: If you see an error message "Unable to copy PPD file" .. then
  restart cups.. sudo service cups restart
  sudo cp /usr/share/cups/model/brfax_cups.ppd /usr/share/ppd
  sudo service cups restart

Check the install with... 
dpkg -l | grep Brother

The last command should show you 3 or 4 Brother listings..

Cups Modification

Now you have to do a little modifing in Cups.. Use your browser and head over to [http://localhost:631/printers](http://localhost:631/printers)
You may see 2 new printers installed already BRFAX and MFC7440N.  Pick one of them and click on it.. I'll start with BRFAX. 

You'll see a drop down tab labeled "Administration". Click it and choose "Modify".  

What ever the "Current Connection" says go further down the list and choose "LPD/LPR Host or Printer".  

If at some point during this process you have an opportunity to list the location of the driver (probably right after the previous step) you'll want to enter the following... lpd://<ip address of the printer>/binary_p1

Click "Continue" and "Continue" on the next screen.

Choose Brother from the list of printers and click "Continue"

No matter what the "Current Driver" shows, right below it will probably be "Brother BRMFCFAX for CUPS (en). Click that and click "Modify Printer". 

If at some point during this process you have an opportunity to list the location of the driver (probably right after choosing the LPD/LPR button) you'll want to enter the following... lpd://<ip address of the printer>/binary_p1.. 

Repeat this process for the printer in the CUPS interface. Note: the correct driver is at the BOTTOM of the list of drivers and will specifically mention 7440n.  Took me a while to find it since it was out of numeric order with the rest of the drivers.

As a last and final step restart cups again with .. sudo service cups restart

Try printing a document or use the Test Print function built into the cups server web page.  You'll find it by clicking the Printers Tab and then under the Maintenance drop down option.

NOTE:  I have not got the fax to actually send a fax yet.. still working on that.  However if you want to test your fax from the command line do the following.

brpcfax -o fax-number=<fax-number> <filename>

This opened a window on the desktop asking for the number and provided a send button but nothing happened for me.  Print an open document to the CUPS fax driver resulted in absolutely nothing other then documents stuck in the print server that I had to Cancel.

---

### Post by smokey_58au on 2010-07-19
I had the same problem as exstarguy with a networked Brother printer at work.  In the Device URI property of the printer settings I had to change the printer name to it's IP address and it came good.

---

