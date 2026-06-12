---
title: "Urgent help needed! Involves printing from VirtualBox"
date: 2009-09-13
forum: General Help
---

### Post by phantom3113 on 2009-09-13
I need to get this fixed as soon as possible. I need to print from my Windows XP Virtual Machine (using VirtualBox 3.0.6). I have an Epson Stylus CX-8400. I've printed from the VM before with no problems. I had initially connected through a USB filter from the settings of the VM and all worked fine. After returning to school from summer (having not printed anything for a while) I found my printer to be unresponsive to my VM. So after some searching, I set my printer up as a network printer using [http://[my](http://[my) ip]/printers/[printer name] and adjusting the settings under admin>>printers. Doing that resulted in success. However, it cannot find my printer yet again! I need to print things for school, so this is a *dire* problem :(

---

### Post by TransitMan on 2009-09-14
How about installing the required software in the Windows XP Virtual so that Windows can print.

I have a HP PSC 1410v and installed the required software in my Virtual Box drive and it prints just fine, without any tweaking, save the inclusion in the setup of the printer in VB.

---

### Post by phantom3113 on 2009-09-14
I forgot to mention, I did install the drivers for my printer off Epson's website (prior to setting it up as a network printer) I was going to use the cd, but I unfortunately misplaced it :( I had it working initially without having to install anything, so I'm confused as to why it won't work. I think the printer components are fine, the xp VM just seems to be having trouble connecting to it in every fashion. The usb filter I've set up for the printer always says "unavailable" and the network I had initially set up (and had working) now says that it either can't be found, or is unavailable. I put the address to my printer as: [http://[my](http://[my) ip]:631/printers/Stylus-CX8400 (which had worked the first time.

---

### Post by TransitMan on 2009-09-15
Have you set the permissions correctly in SAMBA?
If not, then you'll have problems connecting to the printer.

---

### Post by jzacsh on 2009-09-15
this may seem too simple - but sometimes, in dire need, i wish I'd remember I had this option:
install [pdf creator]("http://sourceforge.net/projects/pdfcreator/") on the XP, and print things to PDF - than move the PDFs onto your Ubuntu machine where you *aren't* having problems printing. This won't solve the problem, but this might get your school work onto paper in time.

just piece of advice w/pdf creator: be careful with **2 instances** of the sneaky "*install yahoo.. toolbar for firefox*" option that's checked off in the insatllation process. other than that, i love this pdf printer.

---

### Post by phantom3113 on 2009-09-15
I'll try the pdf printer thing so I can at least print my stuff. I don't think it's a samba issue though, because I had it working through the connection before. How would I check the samba permissions though?

---

### Post by tkoco on 2009-09-15
2 cents worth: Check the printers area for a new duplicate printer. I have had Windows XP create a "new" printer id for the connected printer. Unfortunately, when XP does that, the 'default' printer is disabled and the software does not know about the switch in printers. Easily fixed by designating the new printer as the default. Hopefully this will help you.

> **phantom3113 said:**
> I forgot to mention, I did install the drivers for my printer off Epson's website (prior to setting it up as a network printer) I was going to use the cd, but I unfortunately misplaced it :( I had it working initially without having to install anything, so I'm confused as to why it won't work. I think the printer components are fine, the xp VM just seems to be having trouble connecting to it in every fashion. The usb filter I've set up for the printer always says "unavailable" and the network I had initially set up (and had working) now says that it either can't be found, or is unavailable. I put the address to my printer as: [http://[my](http://[my) ip]:631/printers/Stylus-CX8400 (which had worked the first time.

---

### Post by phantom3113 on 2009-09-15
ok, let me clear up a little. Fall semester of '08 I setup and installed a windows xp virtual machine on Ubuntu 8.10 using Virtual Box 2.4. After doing so, I also set up the usb filters for my vm, as well as a networked folder (so I can move files to and from the vm and the ubuntu host). All of fall and spring semester, I could print from my printer absolutely fine through the usb connection as though it wasn't a vm or anything. However, Fall semester of '09, the printer is now unresponsive to the usb connection, and all my usb filters show up as unavailable under the Devices tab while running the machine. I've recently had to do a fresh install, but I backed up my entire /home folder, so I still have all the config files for my vm and such. Just to make sure, I redid the usb filter for the printer, but still nothing.

So, as another attempt to print, I set up the printer as a networked printer connected to my ubuntu host via ip address, making sure to give the printer permission to be shared, and that worked absolutely fine (once I installed the driver on XP) Now, the network keeps telling me that it's unavailable or couldn't be found. Sorry if it seems that I'm restating, I just want to make sure it's known that it worked before, but now it's not.

Also, @ tkoco, making the new printer as default was the first thing I did, but thanks :)

---

