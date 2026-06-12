---
title: "Lexmark Printer...Why?"
date: 2012-06-07
forum: General Help
---

### Post by Conscript on 2012-06-07
The wife has a morbid obsession with printing coupons now.  Normally I wouldn't care, but since money is a commodity I am low on I have decided to look for a way to make this happen.

I am running 12.04 32 bit with the Gnome fall back (due to wrath at Unity interface) on a dinosaur (still has a 3.5 inch floppy drive!) Dell machine I rescued from a dumpster.  Runs okay, but I can't get the blasted printer to work.  In all fairness I could be the source of the problem- still very new to the Land of Linux, and even newer to the world of troubleshooting.

Printer:  Lexmark x5650.

Problem:  No driver exists for this distro of Ubuntu, it stops at Ubuntu 10.04 I think.  Out of hope I downloaded the suspect deb file, do some damage in the terminal window and still no luck.  It goes through all the motions of installing, and then at the end it tells me that it has finished uninstalling.

Source of drivers:

[http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_X5650&page=product&frompage=null#3](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_X5650&page=product&frompage=null#3)

I now supplicate the Ubuntu Gods for their wisdom.  

Is there a way to make this printer/scanner/copier/fax abomination work without formatting and reinstalling the older distro?  Because I would love to not have to back up all the data and have to download all the programs again...

Any assistance would be appreciated.

---

### Post by 123456789123456789123456 on 2012-06-08
> **Conscript said:**
> The wife has a morbid obsession with printing coupons now.  Normally I wouldn't care, but since money is a commodity I am low on I have decided to look for a way to make this happen.

I am running 12.04 32 bit with the Gnome fall back (due to wrath at Unity interface) on a dinosaur (still has a 3.5 inch floppy drive!) Dell machine I rescued from a dumpster.  Runs okay, but I can't get the blasted printer to work.  In all fairness I could be the source of the problem- still very new to the Land of Linux, and even newer to the world of troubleshooting.

Printer:  Lexmark x5650.

Problem:  No driver exists for this distro of Ubuntu, it stops at Ubuntu 10.04 I think.  Out of hope I downloaded the suspect deb file, do some damage in the terminal window and still no luck.  It goes through all the motions of installing, and then at the end it tells me that it has finished uninstalling.

Source of drivers:

[http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_X5650&page=product&frompage=null#3](http://support.lexmark.com/index?segment=SUPPORT&userlocale=EN_US&locale=en&productCode=LEXMARK_X5650&page=product&frompage=null#3)

I now supplicate the Ubuntu Gods for their wisdom.  

Is there a way to make this printer/scanner/copier/fax abomination work without formatting and reinstalling the older distro?  Because I would love to not have to back up all the data and have to download all the programs again...

Any assistance would be appreciated.

ok I don't know if any of these links will help you any, I found the first one from a ubuntu forum in an entirely different language, looked to be italian, any way, it seems to be related to an error installing the driver in 12.04, even though it mentions a different driver package, or at least it seems to.  the second, seems to be a possible way to at least get the printer to print, but not be able to use the other advanced features of the printer.

here they are.
[http://archbird.blogspot.com.es/2012/04/fix-error-blank-line-installing-lexmark.html](http://archbird.blogspot.com.es/2012/04/fix-error-blank-line-installing-lexmark.html)
[https://answers.launchpad.net/ubuntu/+source/cups/+question/197609](https://answers.launchpad.net/ubuntu/+source/cups/+question/197609)
hope they help.

---

### Post by traditionalist on 2012-06-08
You can get it to work easily enough but it might be a bit slow. Just install a virtual machine with a distribution that works with the printer and print from there. I know it sounds odd but it works. If you have an XP disk lying around you can use that, or indeed any system that works with the printer should work.

Install virtual box;

[[IMG]http://img849.imageshack.us/img849/5416/ubuntusoftwarecenter002.th.png[/IMG]](http://img849.imageshack.us/i/ubuntusoftwarecenter002.png/)

set it up as desired and away you go.

---

### Post by Conscript on 2012-06-08
> **traditionalist said:**
> You can get it to work easily enough but it might be a bit slow. Just install a virtual machine with a distribution that works with the printer and print from there. I know it sounds odd but it works. If you have an XP disk lying around you can use that, or indeed any system that works with the printer should work.

Install virtual box;

set it up as desired and away you go.


I tried doing a work around with wine but had no luck, I will give that a shot.  Problem is that I don' t have any other OS's lying around at the moment.  I guess I could load Ubuntu 10.4 in the VMware as odd as that sounds.  Or Linux Mint, something that supports the patchs available.

---

### Post by mastablasta on 2012-06-08
how did you install the .deb file? what commands did you use?
 
was there any error output? and if so what was it exactly.
 
simply saying it doesn't work won't help much.
 
edit it seem plenty had problme with this printer, but doesn't seem like anyone actually made an effort of filing a bug report, so someone could get it fixed. 
[https://answers.launchpad.net/ubuntu/+source/cups/+question/174874](https://answers.launchpad.net/ubuntu/+source/cups/+question/174874)
or i could be wrong...
 
someone did it in 10.04 but since no further info was provided bug got closed (kind of).
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/620473](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/620473)

---

### Post by traditionalist on 2012-06-08
> **Conscript said:**
> I tried doing a work around with wine but had no luck, I will give that a shot.  Problem is that I don' t have any other OS's lying around at the moment.  I guess I could load Ubuntu 10.4 in the VMware as odd as that sounds.  Or Linux Mint, something that supports the patchs available.

Any system that supports the printer and will run in the VM will do.  I have even run MSDOS in a VM to support a very old dot matrix printer.

---

### Post by mike555 on 2012-06-08
In order to print coupons you will probably need Windows , because most coupon sites insist on installing their spyware called "coupon printer"

---

### Post by kurt18947 on 2012-06-08
> **mike555 said:**
> In order to print coupons you will probably need Windows , because most coupon sites insist on installing their spyware called "coupon printer"

Oh yeah.  You can call the company whose coupons you want.  They'll likely mail you a handful of the desired coupons though it may take a couple weeks.  They also learn that "coupon printer" is not universally supported .  We went through this with Arm & Hammer products.

---

### Post by kurt18947 on 2012-06-08
I have no experience with this so take it for what it's worth.  When I installed PCLinuxOS on an old machine, I noticed  software that looked like it supported Lexmark printers.  I also discovered that Lexmark does not have Vista/Win 7 drivers for many of their non-current SOHO printers.  XP is as recent as they go.

---

### Post by Conscript on 2012-06-08
Well, printing coupons is the catalyst of the operation, but not the entire reason.  Going to school at this point in life and sometimes you just gotta print something out at home.

Got Virtual Box, but I have a question with it. Will I need to get all the programs I need to print from installed on this new virtual OS as well?
I'll post the progress, or lack thereof when I get home today.  10 ish hours?  Downloading a few compatible OS's for the right now. Going to try Ubuntu 10.10, Linux Mint 11, and see how that goes.

This might be a better option because my wife like myself, knows just enough to really smash the system.  So a virtual environment might be best for all of us for the time being.

---

### Post by traditionalist on 2012-06-08
Well, you can do practically anything but it can become complex.  If you try to run MS compatible programs on Linux in a VM  on Wine for instance, it may work, but it also may not and may also be very complex to set up.

If you need MS compatibility then you really need to install XP in the VM. You can still buy XP licences in various places for very little money.  Because XP ran for such a long time  there are a very large number of drivers available for various devices on it.

---

### Post by Conscript on 2012-06-09
I think I have a license from an old perished netbook that came with XP, but no install disc.  So I am back at square one when it comes to XP I guess.

---

### Post by Conscript on 2012-06-09
> **traditionalist said:**
> Well, you can do practically anything but it can become complex.  If you try to run MS compatible programs on Linux in a VM  on Wine for instance, it may work, but it also may not and may also be very complex to set up.

If you need MS compatibility then you really need to install XP in the VM. You can still buy XP licences in various places for very little money.  Because XP ran for such a long time  there are a very large number of drivers available for various devices on it.

Okay, so I got the printer driver to install on Ubuntu 10.10 32 bit under the virtualbox VM.  I gave 8 gigs to it because that was what was recommended.  It installed without a problem.

New problem: it won't believe that I actually connected it via USB.  Fiddled with USB settings in virtualbox and also downloaded he extension for USB 2 and what not.  Still nothing.  But I also discovered that it will not recognize any USB I stick in there.  Not even a lowly thumb drive.  

Re-cap: driver installed under VMware, but the the virtual Ubuntu 10.10 will not recognize USB devices that are plugged in.

How do I proceed from here?

---

