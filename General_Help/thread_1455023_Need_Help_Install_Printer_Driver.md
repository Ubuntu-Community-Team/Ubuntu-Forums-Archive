---
title: "Need Help Install Printer Driver"
date: 2010-04-15
forum: General Help
---

### Post by kernelles on 2010-04-15
I just installed Karmic, and need help installing the propietary driver for a Xerox Workcentre 7345, so I can print wirelessly from my Ubuntu laptop over a Windows office network. 

This printer has security set up on it, so each user has to enter a password to print to it for accounting purposes, which is why I need the actual Xerox driver. (I've installed other printers on this same network without any proprietary drivers, just using the print via Samba wizard, and they work fine, but when I do that with this one, it's able to send the job to printer, bu then I get a password error code).

I found the driver here:

[INDENT][http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC7328_WC7335_WC7345&Xlang=en_US&Xcntry=USA&prodName=WorkCentre%207328/7335/7345/7346](http://www.support.xerox.com/go/results.asp?Xtype=download&prodID=WC7328_WC7335_WC7345&Xlang=en_US&Xcntry=USA&prodName=WorkCentre%207328/7335/7345/7346)
[/INDENT]
And here is the readme:

[INDENT]* CentreWare Services for UNIX Systems is a two part installation process   *
* 1. a code package i.e SolarisXPXX_4.00.60.tar                             *
* 2. a printer support package i.e. PrinterPkgXPXX_2006_06_15.tar           *
*                                                                           *
* The code package must be installed first followed by the printer          *
* support package.                                                          *
*                                                                           *
* Installation requires the user have root or superuser privileges.         *
*                                                                           *
*******************************************************************
*******************************************************************
To install the package expand the tar file and execute setup.
NOTE: setup for the code package will expand and install the compressed tar
   file in the install directory; generate script files and other files
   that are needed at run time. You do not need to uninstall the package
   if you are upgrading or reinstalling.
The following syntaxes are supported:
1. setup
2. setup tmp_path
3. setup install install_path
4. setup install install_path tmp_path
install_path is the installation directory which will contain
              all of the Xerox software.
tmp_path      is a temporary work area. /tmp is the default work area.
To uninstall a previous installation:
1. Use xpadmin to remove all Xerox print queues.
2. For Solaris installation, use pkgrm to remove the CTRWxpxx package.
   For all other installations, remove the "Xerox" installation directory.
3. Remove /var/spool/Xerox directory.
[/INDENT]First, it says I need "a code package," (??) such as "SolarisXPXX_4.00.60.tar," but this package is not in Synaptic, nor can I find it with google, so I'm at a loss.

I downloaded the actual driver anyway, and when it is extracted, there is a "Setup" install file, so it looks like this will probably do the trick if someone can help me figure out the rest. When I click on it now, nothing happens, not even an error message or password request. 

By the way, I'm a Linux newbie, so you may need to dumb down your answer so I can understand it.

Thanks,

Les.

---

### Post by cgb on 2010-04-15
I wouldn't use the Centreware driver unless you need to for some reason I dont understand.  Their is also a Linux CUPS Printing Package on the link you provided.  I would use this driver.  Basically download the driver, extract it.  Then go to add the printer through the standard printing menu under Administration.  When it asks for what driver to use browse to the downloaded location and select.  Or if you are having problems with any of this their is a readme.txt with installation steps in the download.  Hope this helps!

---

### Post by kernelles on 2010-04-15
> **cgb said:**
> I wouldn't use the Centreware driver unless you need to for some reason I dont understand.  Their is also a Linux CUPS Printing Package on the link you provided.  I would use this driver.  Basically download the driver, extract it.  Then go to add the printer through the standard printing menu under Administration.  When it asks for what driver to use browse to the downloaded location and select.  Or if you are having problems with any of this their is a readme.txt with installation steps in the download.  Hope this helps!

Okay, I tried, but it still doesn't work. Here's what I did:

1. Add new printer
2. Network/Windows Printer via Samba
3. Choose Driver: Provide PPD file
4. Browsed to PPD file in extracted CUPS folder that matched my printer
5. Selected options & apply

When I try to print a test page, it sends to printer without asking for a password. Printer shows job completed with error code 016-757, which means it's the password/accounting issue.

---

### Post by cgb on 2010-04-15
I haven't worked a lot with Xerox MFP but with Ricoh's the accounting is typically done with user codes.  These can be set in the printer properties.  Basically go to Administration/Printing, right click on printer installed, select Properties.  Now under Printer Options scroll down and their should be a Job Log section with user code and all that.  Possibly this is the same for how the Xerox functions?

* did a little more research on the situation.  Look at the below thread, appears they have been able to resolve the issue by manually editing the ppd file before attaching it to the printer.  

[http://ubuntuforums.org/showthread.php?t=1081388&page=2]("http://ubuntuforums.org/showthread.php?t=1081388&page=2")

---

### Post by kernelles on 2010-04-15
> **cgb said:**
> I haven't worked a lot with Xerox MFP but with Ricoh's the accounting is typically done with user codes.  These can be set in the printer properties.  Basically go to Administration/Printing, right click on printer installed, select Properties.  Now under Printer Options scroll down and their should be a Job Log section with user code and all that.  Possibly this is the same for how the Xerox functions?

* did a little more research on the situation.  Look at the below thread, appears they have been able to resolve the issue by manually editing the ppd file before attaching it to the printer.  

[http://ubuntuforums.org/showthread.php?t=1081388&page=2](http://ubuntuforums.org/showthread.php?t=1081388&page=2)

Yes, I tried that, too. The closest thing is under "policies." There is an option there called "Operation Policy," with two options: Default Behavior, and Authenticated. I turned on authenticated, but no change.

About the link, I checked it out, but that's more involved than I have time for right now. I do notice his problem was different from mine though, in that his driver was asking for a password, and mine is not. But I'll have a closer look later on. Either way, thanks for trying to help!

---

### Post by kernelles on 2010-04-15
Okay, I tried the suggestion in the link you mentioned, but a search in my PPD file showed the words "userid", "id," "groupacct," "acct," and "account" are not even in it. I did find a line in the code that said password: "()", and I replaced the () with my password for the printer, but this didn't do it. Any other suggestions, anyone?

---

### Post by cgb on 2010-04-15
Well not sure how much more help I can be since I do not have this model here in the office but I believe you actually have to add the lines that they show in the link I previously provided to the ppd. They are not there by default.  Also you will need to change some of the information to provide your user/group id.  You may be best actually trying to contact Xerox regarding this and see what they have to offer.

---

### Post by kernelles on 2010-04-15
> **cgb said:**
> Well not sure how much more help I can be since I do not have this model here in the office but I believe you actually have to add the lines that they show in the link I previously provided to the ppd. They are not there by default.  Also you will need to change some of the information to provide your user/group id.  You may be best actually trying to contact Xerox regarding this and see what they have to offer.

I see. Well thanks again for the effort!

---

