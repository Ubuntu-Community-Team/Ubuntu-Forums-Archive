---
title: "Printing to Brother MFC 240C"
date: 2010-02-27
forum: General Help
---

### Post by jereece on 2010-02-27
I am using Ubuntu 9.10.  I have a Brother MFC 240C printer.  I installed the print driver from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C"). Driver installed with no problem.  When I print something, it goes through the print que to the the printer with no error messages, however the printer never prints the document.  When I take the printer off line, Ubuntu senses it's offline and when I return the printer online Ubuntu knows it's back online.  So I know Ubuntu is talking to the printer.  It's just the print jobs never print. I am dual booting with Windows XP.  The printer works fine when in XP.

Any suggestions?

Thanks,
Jim

---

### Post by kerxon on 2010-02-27
Are you using the printing gui from the menu or CUPS? I was having a similar problem with my Brother printer until I set it up through CUPS. Haven't had any problems since.

---

### Post by jereece on 2010-02-27
I am clicking on File, Print and then selecting my printer.  Please educate me on CUPS. I don't have a clue what that is.  Sorry...I am a bit new to Linux.

I appreciate the help.
Jim

---

### Post by jereece on 2010-03-01
bump.

---

### Post by plucky on 2010-03-01
> **jereece said:**
> I am using Ubuntu 9.10.  I have a Brother MFC 240C printer.  I installed the print driver from [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-240C"). Driver installed with no problem.  When I print something, it goes through the print que to the the printer with no error messages, however the printer never prints the document.  When I take the printer off line, Ubuntu senses it's offline and when I return the printer online Ubuntu knows it's back online.  So I know Ubuntu is talking to the printer.  It's just the print jobs never print. I am dual booting with Windows XP.  The printer works fine when in XP.

Any suggestions?

Thanks,
Jim


Did you install both the cupwrapper and lpr drivers from the website?

The driver packages are in **Synaptic Package Manager** and are called ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
``` if you want to install them using Synaptic.


The CUPS web interface is accessed from FireFox by putting ```
http://127.0.0.1:631/admin
``` into the address bar.


Please post output from a terminal of ```
sudo dpkg -l | grep brother
```

Good Luck

---

### Post by billstowell on 2010-03-02
I'm having a similar problem with my new Brother mfc5890cn.  I dual boot to XP and Kubuntu 8.04.   I followed all of the Brother installation instructions and printed a small file--all seemed to be o.k.  I then used the installation disks to install the printer on the XP boot-up.  Now, I can't get it to print from the Kubuntu boot-up.

sudo dpkg -l | grep brother  yields a blank.

cat /etc/printcap  yields

# /etc/cups/printers.conf file.  All changes to this file
# will be lost.
BrotherHL2040--HL1240Drivers|BROTHER HL-1240:rm=home:rp=BrotherHL2040--HL1240Drivers:
MFC5890CN:\
        :mx=0:\
        :sd=/var/spool/lpd/mfc5890cn:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/Printer/mfc5890cn/lpd/filtermfc5890cn:
bill@home:/etc$
Any thoughts on how to fix this problem would be appreciated.  I have run dpkg -P on the cupswrapper file and reinstalled it--

Hopefully there is something simple about cups that I'm missing.

thanks for your help

Bill Stowell

---

### Post by billstowell on 2010-03-02
More from Bill:

bill@home:/etc$ lpstat -p -d
printer BRFAX is idle.  enabled since Tue 02 Feb 2010 03:14:12 PM EST
printer BrotherHL2040--HL1240Drivers now printing BrotherHL2040--HL1240Drivers-432.  enabled since Tue 02 Mar 2010 09:31:05 PM EST
printer MF5750 is idle.  enabled since Mon 19 Oct 2009 10:05:10 AM EDT
printer MF5750_(FAX) is idle.  enabled since Mon 19 Oct 2009 10:05:10 AM EDT
printer MFC-5890CN is idle.  enabled since Fri 26 Feb 2010 05:21:37 PM EST
printer MFC5890CN is idle.  enabled since Tue 02 Mar 2010 09:08:31 PM EST
printer MFC620CN is idle.  enabled since Fri 26 Feb 2010 05:21:37 PM EST
printer PDF is idle.  enabled since Mon 28 Apr 2008 10:30:14 PM EDT
no system default destination
bill@home:/etc$ sudo dpkg -P MFC620CN
dpkg - warning: ignoring request to remove mfc620cn which isn't installed.


What does this mean?  I have a Canon MF5750 that doesn't run on Kubuntu at all.  I have my new Brother MFC5890cn that isn't working.  I don't have  an MFC620CN and dpkg couldn't purge any drivers for it when I tried.  So why did it show up?  Is something confused so that my system is sending print files to "null" instead of to my MFC5890cn?

I removed my Brother HL-2040 from my system--  I don't know how to uninstall its drivers--could that be the problem?

Any insight would be appreciated.

thanks for your help

Bill Stowell

---

### Post by jereece on 2010-03-08
Plucky - I searched for "brother" in package manager.  It found a cups and lpn driver.  The name was slightly different than you noted but I believe they are the right ones because they have my printer model number in the name.  Below is the output from Terminal that you asked for.  I still can't print.  I appreciate any help.


```
ii  brother-lpr-drivers-common           1.0.0-4-0ubuntu1                           Common files for brother-lpr-drivers package

```

---

### Post by plucky on 2010-03-09
> dpkg -l | grep brother
ii  brother-cups-wrapper-common                       1.0.0-10-0ubuntu5                               Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra                        1.2.1-0ubuntu3                                  Cups Wrapper drivers for extra brother printers
ii  brother-lpr-drivers-common                        1.0.0-4-0ubuntu1                                Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra                         1.2.0-2-0ubuntu3                                LPR drivers for extra brother printers


This is what I get when I use the command in a terminal.My printer uses the MFC-210C drivers which are in the repositories.
Your drivers are also in the repositories,so you should use  synaptic package manager and search for the drivers specified in the earlier post and install them.

Then connect and power on the printer and select "Add new Printer" and it should take you through the installation process.Just select the correct driver when it asks you to pick a driver.If it doesn't find the drivers,reboot and try again.


Good Luck

---

### Post by jereece on 2010-03-12
I guess this is a problem that no one can resolve?  

As an update, after trying several things I began getting the following message.

Printer Warning:  'Printer Brother MFC-240-C': 'CUPS-missing-filter'

I deleted the printer and walked through the Ubuntu printer setup again.  It could not set up my printer automatically.  It gave me a list to select from but recommended "Generic".  I looked under the Brother Printers but MFC-240C was not listed. So I chose Generic.  But that gives me the following error message.

CUPS Server Error:  There was an error during the CUPS operation.  'Client-document-format-not-supported.'  

Note I was not trying to print a document, just set up the printer.  Even after this error, my printer is listed in System/Administration/Printers with a big green check mark on the icon.  However the printer will not print.

I also emailed Brother but they basically said they don't support Linux.   

So, one last time, does anyone have any suggestions?  In my quest to convert from Windows to Linux, this is my last hurdle.

Jim

---

### Post by jereece on 2010-03-12
I also tried the information on [this page]("http://ubuntuforums.org/showthread.php?t=590793"), but when I downloaded the LPR Debian file from [this page]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html") and tried to install it in Terminal per the directions, Ubuntu gave me the message as shown below.

```
dpkg-deb: `mfc240clpr-1.0.1-1.i386.deb' is not a debian format archive
dpkg: error processing mfc240clpr-1.0.1-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 mfc240clpr-1.0.1-1.i386.deb
```

So I am still looking for a solution.

Thanks,
Jim

---

### Post by plucky on 2010-03-12
Post output of ```
dpkg -l | grep brother
```

You should have ```
dpkg -l | grep brother
ii  brother-cups-wrapper-bh7              1.0.0-10-0ubuntu5                          Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common           1.0.0-10-0ubuntu5                          Common files for Brother cups wrapper packages
ii  brother-lpr-drivers-bh7               1.0.1-1-0ubuntu3                           LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common            1.0.0-4-0ubuntu1                           Common files for brother-lpr-drivers packages

```

If you haven't then the drivers aren't installed.Install them from Synaptic.

---

### Post by jereece on 2010-03-12
Results are below.  Like I said, when I download and try to install download the LPR driver from the Brother web site, I get the error that it's not a debian format archive so it will not install.  I also get the same with the cupswrapper driver from the Brother web site. 


```
ii  brother-lpr-drivers-common           1.0.0-4-0ubuntu1                           Common files for brother-lpr-drivers package

```

---

### Post by plucky on 2010-03-13
Go to **System > Administration > Software Sources** and on the first page make sure all the boxes are ticked.(See screenshot)

Reload the index files.

Then open **System > Administration > Synaptic Package Manager** and search for **mfc-240c**.
It will find two packages ```
brother-cups-wrapper-bh7
brother-lpr-drivers-bh7
```
Tick the box for the cupswrapper driver and it will install both drivers.
After the installation,if there are no errors,run from a terminal ```
dpkg -l | grep brother
```
If you don't see what I posted earlier,then something didn't install correctly.Post any error messages.

Good Luck

---

### Post by jereece on 2010-03-13
WOW!  That worked!  Thank you so much Plucky!  I was about to give up hope but your persistence paid off.  I can't tell you how much I appreciate your help.

As a follow-up question, in general is this the proper way to install a print driver?  i.e. search for the model number in Package Manager and install the LPR and Cups drivers, then in stall the printer in Administration/Printing?  Initially I just tried to install the printer but when that did not work I searched Brother's web site and found those drivers which I tried unsuccessfully to install. I did not know to search Package Manager for the printer model number to install the drivers that way.  So is this the proper way for any printer?

Thank you again for your help.

Jim

---

### Post by home28 on 2011-03-15
Please help, i don't know what i am doing wrong,
I downloaded all the packages and followed the instructions.

When i type this into terminal


dpkg -l | grep brother

I get this

ii  brother-cups-wrapper-ac              1.0.3-1-0ubuntu1                                  Cups Wrapper drivers for ac brother printers
ii  brother-cups-wrapper-bh7             1.0.0-10-0ubuntu5                                 Cups Wrapper drivers for bh7 brother printers
ii  brother-cups-wrapper-common          1.0.0-10-0ubuntu5                                 Common files for Brother cups wrapper packages
ii  brother-cups-wrapper-extra           1.2.1-0ubuntu3                                    Cups Wrapper drivers for extra brother printers
ii  brother-cups-wrapper-laser           2.0.1-2-0ubuntu5                                  Cups Wrapper drivers for laser brother printers
ii  brother-cups-wrapper-laser1          1.0.2-1-0ubuntu7                                  Cups Wrapper drivers for laser1 brother printers
ii  brother-cups-wrapper-mfc9420cn       1.0.0-1-0ubuntu5                                  Cups Wrapper drivers for mfc9420cn brother printers
ii  brother-lpr-drivers-ac               1.0.3-1-0ubuntu1                                  LPR drivers for ac brother printers
ii  brother-lpr-drivers-bh7              1.0.1-1-0ubuntu3                                  LPR drivers for bh7 brother printers
ii  brother-lpr-drivers-common           1.0.0-4-0ubuntu1                                  Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-extra            1.2.0-2-0ubuntu3                                  LPR drivers for extra brother printers
ii  brother-lpr-drivers-laser            2.0.1-3-0ubuntu3                                  LPR drivers for laser brother printers
ii  brother-lpr-drivers-laser1           1.0.0-3-0ubuntu4                                  LPR drivers for laser1 brother printers
ii  brother-lpr-drivers-mfc9420cn        1.0.0-3-0ubuntu3                                  LPR driver for mfc9420cn brother printer


My printer says receiving data but then stops and does nothing. 
What am i doing wrong? I checked several forums but none of them worked either.

---

### Post by plucky on 2011-03-15
> My printer says receiving data but then stops and does nothing.
What am i doing wrong? I checked several forums but none of them worked either. 

Is your printer an MFC-240C?

The drivers for that printer is in the ```
ii brother-cups-wrapper-bh7 1.0.0-10-0ubuntu5 Cups Wrapper drivers for bh7 brother printers
ii brother-lpr-drivers-bh7 1.0.1-1-0ubuntu3 LPR drivers for bh7 brother printers
``` package.

Did you select the right driver when it searched for drivers when you added the printer using **System > Administration > Printing**?

It should be usb://Brother/MFC-240C

---

