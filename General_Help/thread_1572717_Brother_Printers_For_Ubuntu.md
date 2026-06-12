---
title: "Brother Printers For Ubuntu"
date: 2010-09-11
forum: General Help
---

### Post by pepperwood on 2010-09-11
Would like to hear from our Forum Family on what Brother printers you are using that work well with Ubuntu. Considering the DCP-395CN. Print, copy & scan. Your assistance would be appreciated very much. Thank you for taking the time to post. PM

---

### Post by ajgreeny on 2010-09-11
I know the MFC-5860CN is great with the brother printer drivers from the repos and the scanner driver from [http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html](http://www.brother-store.co.uk/category/brother-linux-printer-fax-dcp-mfc-software-drivers_MjQzMg==.html).

It looks as if your 395 should also be OK with drivers available at that site.  Brother printers are very good from what I've seen, and manage to print large numbers of pages with no problems at all so far and that is after about 12 months of heavy use.

---

### Post by Cityscape on 2010-09-11
I use an older MFC-4800 and it works fine. It has both printer & scanner drivers (I actually haven't tried scanning yet but printing is great) at the Brother website. Drivers are a little tricky to install for a beginner but if you find the right pages (on the brother site) and follow the instruction it should be okay.

But it does seem that HP (depends on model) is generally the best for Linux. All I do is plug mine in and it work.

---

### Post by alliance1975 on 2010-09-11
I have a Brother HL-2040 that works great. It is connected to a Linksys WPSM54G wireless printserver and I print from windows and ubuntu computers. All drivers were available from Brother at their linux website: [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html).

Brother is great if only because they provide reasonably priced printers with linux drivers.

---

### Post by jmszr on 2010-09-11
pepperwood,

This may be of use to you: [http://www.openprinting.org/printers/manufacturer/Brother](http://www.openprinting.org/printers/manufacturer/Brother) .

---

### Post by vadarfone on 2010-09-11
Hi,

I am having trouble with a Brother DCP-155c printer, with Ubuntu 10.10.

I have an IBM Thinkpad T43.

I followed the instructions used to install the Printer, in this thread, and everything seemed to install OK.  When I go to print, however, nothing happens.

The Printer can make photocopies by itself, so it is on and working.  I just can't seem to get it to work with the computer.

Any help or anything you need to me to post for you to have a look at?

Thanks in advance.

---

### Post by wojox on 2010-09-11
My mother-in-law has a MFC-490CW that I installed the drivers for on my laptop. No complaints here.

---

### Post by wojox on 2010-09-11
> **vadarfone said:**
> Hi,

I am having trouble with a Brother DCP-155c printer, with Ubuntu 10.10.

I have an IBM Thinkpad T43.

I followed the instructions used to install the Printer, in this thread, and everything seemed to install OK.  When I go to print, however, nothing happens.

The Printer can make photocopies by itself, so it is on and working.  I just can't seem to get it to work with the computer.

Any help or anything you need to me to post for you to have a look at?

Thanks in advance.

Go here [DCP-155C]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-155C") and download the LPR and Cupswrapper Drivers in .deb format.

---

### Post by vadarfone on 2010-09-11
Hi

Thanks for the reply.

I have already done that and followed the instructions through to the end.

No luck, unfortunately!

Is there anything I should be checking after I have installed these to make sure things are all in the right place?

---

### Post by wojox on 2010-09-11
> **vadarfone said:**
> Hi

Thanks for the reply.

I have already done that and followed the instructions through to the end.

No luck, unfortunately!

Is there anything I should be checking after I have installed these to make sure things are all in the right place?

I used this tutorial [HOWTO: Ubuntu All Brother Printer & Scanner Driver Installation for Newbies!]("http://ubuntuforums.org/showthread.php?t=590793&highlight=Brother+printer") 

Pretty much from [COLOR="Red"]Step 4[/COLOR] down

---

### Post by vadarfone on 2010-09-11
Thanks a lot!

I will work thorough and let you know how it goes.

Out of interest; which Brother printer are you using?

---

### Post by wojox on 2010-09-11
The MFC-490CW

I just substituted the numbers the OP was using for mine.

Good Luck  ;)

---

### Post by vadarfone on 2010-09-11
OK, I have followed this through, and checked everything.

This was exactly what I had initially done, so according to this, everything is fine.

It is still not working, unfortunately.

The message I am getting when I try to print a test page, I am told that the printer is busy...

EDIT>  I fixed the problem.  Once I had installed everything properly, I had to turn off the printer and unplug the USB cable, leave it for a couple of seconds, then turn it back on and turn on again.

Just tested the printer and it works fine!

Great stuff, thanks a lot!

---

### Post by wojox on 2010-09-11
> **vadarfone said:**
> OK, I have followed this through, and checked everything.

This was exactly what I had initially done, so according to this, everything is fine.

It is still not working, unfortunately.

The message I am getting when I try to print a test page, I am told that the printer is busy...

EDIT>  I fixed the problem.  Once I had installed everything properly, I had to turn off the printer and unplug the USB cable, leave it for a couple of seconds, then turn it back on and turn on again.

Just tested the printer and it works fine!

Great stuff, thanks a lot!

Now go to System > Administration > Printing

Delete the printer in there.
Click New and it should search for printers.

Now open the Network Printer and select the Brother Whatever version you have
Let it print a test page.

---

### Post by wojox on 2010-09-11
I can't use the drivers right now because I'm not at her house. That's about all the help I can give you.

Are you using Ubuntu 32 or 64 bit?

---

### Post by pepperwood on 2010-09-12
> **pepperwood said:**
> Would like to hear from our Forum Family on what Brother printers you are using that work well with Ubuntu. Considering the DCP-395CN. Print, copy & scan. Your assistance would be appreciated very much. Thank you for taking the time to post. PM

Thanks to all that took the time to read and reply. The information and sites provided were great. Hopefully when I receive the Printer everything will work out accordingly. You all were just great. :D PM

---

### Post by tsetse1986 on 2010-10-11
Just took delivery of a Brother DCP-395CN.  My son Mike is a computer engineer and made the printer and scanner work using the drivers provided by Brother. It was necessary to make a lpd directory under /var/spool before installing the drivers.  All seems to work well at the moment!

Tim

---

### Post by ratcheer on 2010-10-11
I am using an old **Brother HL-1440** B&W laser printer with 10.10, networked via a Win XP machine. It was working perfectly on my Maverick test installation, I need to re-check it on my production system, which I upgraded this morning. Thanks for reminding me.

Tim

PS - Later - Yep, added it to new 10.10 as a network printer, installed driver, and in business.

---

