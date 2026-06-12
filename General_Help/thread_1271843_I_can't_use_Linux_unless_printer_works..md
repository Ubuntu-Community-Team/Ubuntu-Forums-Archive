---
title: "I can't use Linux unless printer works."
date: 2009-09-21
forum: General Help
---

### Post by devilcat on 2009-09-21
I would like to be able to use Linux, but I have real work that needs to get printed and there are no clear instructions on how to get my printer working.

It is a Brother FAX-2820 printer.  (Fax, but also a printer.  Works fine in Vista,)

So, I select System -> Administration -> Printing

Select Server -> New - > Printer

Select Windows Printer via Samba

Browse for printer, it finds it.

Select Brother from printer database

FAX-2820 isn't listed in drivers, so I go back

There is a "Provide PPD file" option, so I go looking for a PPD file for Brother FAX-2820

So far, so good.  Should be able to find one them easily right?

Go to Brother's website.

Step through driver database up to FAX-2820 and choose Linux

No PPD files are listed, but they have files for "lpr" and "cups".  I don't know what "lpr" and "cups" is.  All I know is that I need my printer working.  Which one will have this "PPD" file in it?  Who knows.  In typical Linux fashion, have to start guessing.  So, lets install both of them and hope when I go back to that printer configuration program that the drivers will now be listed. 

Download these "rpm" and then follow the instructions on page to install them.

*sudo **rpm  -ihv  --nodeps driver.rpm*

rpm (of course isn't installed)
[I]
sudo apt-get install rpm[/I]

it installs and I try again

*sudo *[I]rpm  -ihv  --nodeps driver.rpm

[/I]It gives some BS about this not being a valid rpm.  Here we go, Linux is starting it's BS again.  Even though I followed the instructions exactly (and they were for Ubunto), it doesn't work.

I have real work that needs to get done and don't have time for this nonesense.

If anyone can give a clear instruction on how to get this printer working I will be very grateful.  Thank you.

---

### Post by Commander_Keen on 2009-09-21
O.k.. Calm down,
  We are all here to help.
 Ubunto does not use RPM, that's for Redhat. 
Ubunto Use's Deb files.
I have followed Brother's instruction for Freespire (Based off of Ubunto) and Ubutno 8.4 and it worked great both times.
I would give it one more chance.
If it doens't work You may have to purchase and HP printer.
Their also very easy to install.
yea. I know, the argument, you should have to buy a new printer to use Ubunto, but is the stress/headache really worth $50 ( the cost of a new printer?)

---

### Post by mike555 on 2009-09-21
Why don't you use the package manager? type "brother" in the search box and click on different ones till yours is listed then install ............. easy ..

---

### Post by devilcat on 2009-09-21
.deb doesn't work either.


$ [I]sudo dpkg -i --force-all cupswrapperFAX2820-2.0.1-2.i386.deb 
[/I]

dpkg-deb: `cupswrapperFAX2820-2.0.1-2.i386.deb' is not a debian format archive
dpkg: error processing cupswrapperFAX2820-2.0.1-2.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 cupswrapperFAX2820-2.0.1-2.i386.deb


$ *sudo dpkg -i --force-all brfax2820lpr-2.0.1-1.i386.deb *

dpkg-deb: `brfax2820lpr-2.0.1-1.i386.deb' is not a debian format archive
dpkg: error processing brfax2820lpr-2.0.1-1.i386.deb (--install):
 subprocess dpkg-deb --control returned error exit status 2
Errors were encountered while processing:
 brfax2820lpr-2.0.1-1.i386.deb

Which one has this "ppd" file it anyway?  Which one is going show up in list of drivers when I run that printer configuration program?  Why do you have to guess everything in Linux ??

---

### Post by devilcat on 2009-09-21
> **mike555 said:**
> Why don't you use the package manager? type "brother" in the search box and click on different ones till yours is listed then install ............. easy ..

Tried that.  Nothing "brother" gets found, except two games with "brother" in the name.

---

### Post by P4man on 2009-09-21
It looks like prepackaged  Brother drivers are available in the multiverse repo's. Your printer is listed here:
[https://wiki.edubuntu.org/BrotherDriverPackaging](https://wiki.edubuntu.org/BrotherDriverPackaging)

Try enabling multiverse in system > adminstration > software sources.

Then look for those drivers again in synaptic

---

### Post by devilcat on 2009-09-21
> **P4man said:**
> It looks like prepackaged  Brother drivers are available in the multiverse repo's. Your printer is listed here:
[https://wiki.edubuntu.org/BrotherDriverPackaging](https://wiki.edubuntu.org/BrotherDriverPackaging)

Try enabling multiverse in system > adminstration > software sources.

Then look for those drivers again in synaptic

Thank you!  Multiverse was already enabled, but I wasn't using Synaptic.  I was looking for the drivers in the "Add/Remove Programs" program.

I just used Synaptic and installed the Brother laser cups/lpr driver and now the printer is working great.

THANK YOU VERY MUCH !

---

