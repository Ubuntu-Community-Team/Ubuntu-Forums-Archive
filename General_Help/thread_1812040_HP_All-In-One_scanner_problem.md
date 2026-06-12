---
title: "HP All-In-One scanner problem"
date: 2011-07-25
forum: General Help
---

### Post by momist on 2011-07-25
Hi there,

I've just installed a new HP CN503B Photosmart Premium e-All-In-One C310a, and hit a problem with the HPLIP installation.  During the driver install, there was a failure of sudo apt-get install libsane-dev.  After installation, the printer works OK, but I can't access the scanner.

In a terminal,   ~$ hp-check -t     reveals the following:
```

---------------
| SYSTEM INFO |
---------------

Basic system information:
Linux shelob 2.6.32-33-generic #71-Ubuntu SMP Wed Jul 20 17:27:30 UTC 2011 x86_64 GNU/Linux

Distribution:
ubuntu 10.04

Checking Python version...
OK, version 2.6.5 installed

Checking PyQt 4.x version...
OK, version 4.7.2 installed.

Checking for CUPS...
Status: scheduler is running
Version: 1.4.3
error_log is set to level: warn

Checking for dbus/python-dbus...
dbus daemon is running.
python-dbus version: 0.83.0

```

And:

```

Checking for dependency: SANE - Scanning library...
OK, found.

Checking for dependency: SANE - Scanning library development files...
error: NOT FOUND! This is a REQUIRED/COMPILE TIME ONLY dependency. Please make sure that this dependency is installed before installing or running HPLIP.
To install this dependency, execute this command:
sudo apt-get install --assume-yes libsane-dev

Checking for dependency: scanimage - Shell scanning program...
OK, found.

Checking for dependency: xsane - Graphical scanner frontend for SANE...
OK, found.

```

If I try to load it from a terminal, the same thing happens, and in Ubuntu Software Centre, I get the following report:

```
This error could be caused by requiring additional software packages which are missing or not installable. Alternatively, there could be a conflict between software packages which are not allowed to be installed at the same time.
```

I'm considering uninstalling the HPLIP driver, trying then to put in the libsane-dev, and then reinstalling HPLIP. 

BTW, it seems to work fine with Windows XP and MacOS X  :)


What does anyone think please?

Cheers.

---

### Post by XubuRoxMySox on 2011-07-25
Before you try anything really complicated, try installing it using **[COLOR="Purple"]Synaptic Package Manager[/COLOR]** instead of the Ubuntu Software Center. I know it sounds silly, but Synaptic grabs "dependencies" that are needed better than the Software Center does, if my sense of it is right. Let us know if Synaptic does it for you!

-Robin

---

### Post by momist on 2011-07-26
Thanks for your suggestion dixiedancer.  I have tried synaptic and got the following results:

```
 Could not mark all packages for installation or upgrade.

The following packages have unresolved dependancies.
Make sure that all required repositories are added and
enabled in the preferences:


libsane-dev:
  Depends: libsane (=1.0.20-13ubuntu2) but 1.0.21-0ubuntu1
is to be installed
```


For some reason, "force package" is greyed out, and I can't seem to find any way past this.  How can I revert to the the, presumably earlier, 1.0.20-13ubuntu2?   Is that really what's needed?

Ian

---

### Post by momist on 2011-08-15
I am bumping this thread, as I have still not made scanning work for me with this All-In-One HP Printer.  Following advice from HP direct, and then also from the Launchpad people, I have upgraded to hplip 3.11.7 but still get the same error.  

In synaptic package manager, if I try to install libsane-dev I get the following report:

libsane-dev:
  Depends: libsane (=1.0.20-13ubuntu2) but 1.0.21-0ubuntu1 is to be installed

Can anyone tell me how to get round this?  It looks like I have to regress to an earlier version of ubuntu, but I really don't understand what these version numbers mean and don't want to muck up the rest of the system.  As I said earlier, "force package" is greyed out or I would have used that.

Thanks

---

### Post by gandaran on 2011-08-15
where did you get or how did you install the new hplip version that requires a newer version of libsane dependency not available on the ubuntu repositories?
so to fix it you either get and install the required libsane version or go back to the default ubuntu repositories packages

---

### Post by momist on 2011-08-15
> **gandaran said:**
> where did you get or how did you install the new hplip version that requires a newer version of libsane dependency not available on the ubuntu repositories?

Hi gandaran,
See: [email]question166677@answers.launchpad.net[/email]
The kind people there advised me to install the latest version of hplip, but unfortunately it made little difference.  The default Ubuntu packages had the same fault.

I will have to go back to the required libsane version, as you say.  But what are the likely side-effects, if any?  Also, how do I stop the system subsequently upgrading me to the latest version?

Ian

---

### Post by gandaran on 2011-08-16
> how do I stop the system subsequently upgrading me to the latest version?
I still don't know how you installed but if you used a repository to install then just remove or disable the same repository in software sources and remove all hplip and dependency packages then update software package list and then you will have the default ubuntu only packages in package manager.

---

### Post by momist on 2011-08-16
Sorry to confuse you gandaran.  If you re-read my posts, I was using the default packages before upgrading to the latest hplip, and it still had the same problem.  hplip requires a version of libsane-dev not available to me that way.  

The question is, how to get the required version, if it is not in the current default packages.

---

### Post by gandaran on 2011-08-16
> **momist said:**
> Sorry to confuse you gandaran.  If you re-read my posts, I was using the default packages before upgrading to the latest hplip, and it still had the same problem.  hplip requires a version of libsane-dev not available to me that way.  

The question is, how to get the required version, if it is not in the current default packages.
you are right, this is getting confusing, try running the package list update command then see if it solves the install problem
```
sudo apt-get update
```
also I cant figure out why libsane-dev is needed, hplip and hpijs are installed by default on ubuntu and is all you need for HP printers and they don't have libsane-dev as dependency so what else have you installed? xsane? hplip-gui?
if you need newer package versions you can get them from latest ubuntu releases at [ubuntu.packages.com]("http://packages.ubuntu.com/")

---

### Post by momist on 2011-08-16
> **gandaran said:**
> 
also I cant figure out why libsane-dev is needed, hplip and hpijs are installed by default on ubuntu and is all you need for HP printers and they don't have libsane-dev as dependency so what else have you installed? xsane? hplip-gui?


Yes, I need xsane.  From my post #1
> After installation, the printer works OK, but I can't access the scanner.

Printing works fine, thanks, it's just that I bought this all-in-one to replace a broken printer and an old Epson scanner that has only a SCSI interface, which only one of my systems now supports.  The HP scanner function works fine over wireless connections on my Windows and Mac systems, but not on Ubuntu.

Part of the problem is that the hplip packages needed require all dependencies to be met, and then runs 'make' and 'install', so simply loading the right package will not be enough anyway, I'll have to uninstall and start again.  The standard hplip from the Ubuntu repositories are not up to date enough for this model of printer anyway (although they permit printing), and I first installed the recommended one direct from HP, which then revealed the problem.  Then the launchpad people who develop these things suggested the later version, but that didn't cure it either.

---

### Post by gandaran on 2011-08-20
hi again
did you fix the problem?
I just found this HP website for linux drivers and your printer is on the supported list [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)
I think you can get the scanner working, remove all hp drivers and xsane installed, install the HP driver from this website then try the scanner with the ubuntu default simple scanner utility, I think it should work, you may not need xsane but you can also try with it.

---

### Post by talthing on 2011-08-22
I have an HP 6500a wireless printer.  Here is what I've found that works...
You will need HPLIP version 3.11.7 You download from HP website

Assign a static ip address to your printer (if you have one of the new cisco routers, you will need to add the static ip under the 'reserved DHCP address' section)

Under the HPLIP setup, add the printer as a network printer (choose the second option)  Manually find the printer via ip address (under advanced)

You will now see the printer and the fax added

Scanning on the flatbed will work but scanning from the ADF through xsane or simple scan will not.  To get around this you can go to the printer's config page (open browser and type your printer's ip address) and use the scanning feature from there.

The symptoms you see in xsane or simple scan is an I/O error (couldn't start scanner) and yet the document feeds through the ADF.  I have tried opening UFW to see if the firewall was blocking but this was not it...and there are no settings related to a timeout on the printer or within HPLIP application.

Hope this helps

---

### Post by linuxonbute on 2011-11-25
> **talthing said:**
> I have an HP 6500a wireless printer.  Here is what I've found that works...
You will need HPLIP version 3.11.7 You download from HP website

Assign a static ip address to your printer (if you have one of the new cisco routers, you will need to add the static ip under the 'reserved DHCP address' section)

Under the HPLIP setup, add the printer as a network printer (choose the second option)  Manually find the printer via ip address (under advanced)

You will now see the printer and the fax added

Scanning on the flatbed will work but scanning from the ADF through xsane or simple scan will not.  To get around this you can go to the printer's config page (open browser and type your printer's ip address) and use the scanning feature from there.

The symptoms you see in xsane or simple scan is an I/O error (couldn't start scanner) and yet the document feeds through the ADF.  I have tried opening UFW to see if the firewall was blocking but this was not it...and there are no settings related to a timeout on the printer or within HPLIP application.

Hope this helps
* I have been through this as well* but found that after doing as you have there is one more step which then allowed both xsane, simple scan and gimp to be used.
```

sudo hp-setup

```it worked for me

---

### Post by momist on 2011-11-25
> **linuxonbute said:**
> * I have been through this as well* but found that after doing as you have there is one more step which then allowed both xsane, simple scan and gimp to be used.
```

sudo hp-setup

```it worked for me

Hi, glad you got yours working OK.  

I should have marked this thread as "solved" and I'm sorry I didn't as I now can't remember what I did to load up the right libsanedev version.  However, getting the right version, I think by eliminating all of sane and then re-installing the expected version, cured my problems with scanning.

The one thing that still doesn't work is the scanner doesn't see Ubuntu as a client, I have to initiate things from the Ubuntu pc.  With Windows and the Mac, they are seen by the scanner and the control panel on the scanner can scan to a file and send it to the computer.  Who needs this though?

---

