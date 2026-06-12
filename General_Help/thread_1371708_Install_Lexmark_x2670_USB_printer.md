---
title: "Install Lexmark x2670 USB printer?"
date: 2010-01-03
forum: General Help
---

### Post by DaleEMoore on 2010-01-03
Hi folks;

I have been unable to make my new Lexmark x2670 USB printer print anything on Ubuntu 9.10. I've tried Generic text only and several other Lexmark printers like the z700 but nothing prints for me.

Any suggestions you have are very much appreciated,
Dale E. Moore

---

### Post by DaleEMoore on 2010-01-04
I wonder if there is some magical way to just make it print text without any fancy graphics or fonts?

---

### Post by cjazz on 2010-01-04
Have you installed a driver for this model?

---

### Post by Sef on 2010-01-04
Check out [Openprinting]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X2650").

---

### Post by DaleEMoore on 2010-01-06
> **cjazz said:**
> Have you installed a driver for this model?

Hi Cjazz; I'm sorry that I have been unable to locate a driver for this model. I wonder if Lexmark has a forum somewhere where they talk with their customers?

---

### Post by DaleEMoore on 2010-01-06
> **Sef said:**
> Check out [Openprinting]("http://www.openprinting.org/show_printer.cgi?recnum=Lexmark-X2650").

Hi Sef; I posted [this]("http://forums.linux-foundation.org/read.php?29,11173") at OpenPrinting, but have heard nothing from them yet.

---

### Post by DaleEMoore on 2010-01-07
---------- Forwarded message ----------
From: Dale E. Moore <daleemoore@gmail.com>
Date: Thu, Jan 7, 2010 at 3:58 PM
Subject: Re: Lexmark X2670
To: Michael Hipgrave <mih57@ymail.com>


Dear MIchael;

I am DELIGHTED to hear from you, thanks for stepping around Open Printing's Forum's problems; I have had numerous with them too!

I'm going to step through your instructions here (and hopefully have a wondrous solution!)
[www.lexmark.com](www.lexmark.com) automatically re-directs to
[http://www1.lexmark.com/products/](http://www1.lexmark.com/products/) has Find A Driver which links to  
[http://support.lexmark.com/index?page=home&locale=en&userlocale=EN_US&segment=DOWNLOAD](http://support.lexmark.com/index?page=home&locale=en&userlocale=EN_US&segment=DOWNLOAD) has several input, but one "Please start typing your model number to find your product", when I enter X2670 has a "select" link that gives me the error "Please try again. There was no product found for this model: X2670", but; also shows a picture of my printer and when clicked goes to
[http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X2670&page=recommendedDownloads#1](http://support.lexmark.com/index?segment=DOWNLOAD&userlocale=EN_US&locale=en&productCode=LEXMARK_X2670&page=recommendedDownloads#1) which gives several OS drop down boxes, one of which "Linux" has Ubuntu 8.04 selectable. When Ubuntu 8.04 is selected "lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip" can be downloaded.
lexmark-inkjet-08-driver-1.0-1.i386.deb.sh.zip is about 30 MB...
I am all bristly with excitement! I've un-zipped the .zip and run the .sh and I encounter:

The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.

You have gotten me much further than anybody else has, and I very much appreciate it. I'll dig into this and see if I can find a way past (what I think is) the install script bug. If you have thoughts or ideas about this, I will very much appreciate hearing your comments!

Stay warm and safe,
Dale

---

### Post by DaleEMoore on 2010-01-07
./lexmark-inkjet-08-driver-1.0-1.i386.deb.sh

gets to:

The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.

and here's where some of that is found:

root@judyaro-desktop:~/Desktop/Printer# grep CUPS -R x2670/*
x2670/config/run.lua:   install.setstatus("Checking CUPS minimum requirements")
x2670/config/run.lua:           MyInstallScreen_output:add("The system does not meet minimum CUPS version requirements.")
x2670/config/run.lua:           gui.msgbox('The installer has detected the operating system does not meet CUPS minimum version requirements. Please install CUPS version 1.2 or higher and run the installer again.')
x2670/config/run.lua:   install.setstatus("CUPS version ok")
x2670/files_extra/readme:6. Manually adding the Printer in CUPS:
x2670/files_extra/readme:   2. The open source Common UNIX Printing System (tm), ("CUPS (tm)") used in this driver is licensed
x2670/files_extra/readme:      To obtain source code files for the Lexmark modified CUPS licensed software, contact

I wonder if it will work, maybe the readme will help;
Dale E. Moore

---

### Post by DaleEMoore on 2010-01-08
I grepped for CUPS, found it in config/run.lua and commented out the version check. the x2670 installed and printed fine!

Thanks to everyone whom helped!
Dale E. Moore

---

### Post by DaleEMoore on 2010-01-12
After a 5 day wait I was delighted to hear from [email]support@lexmark.com[/email], but; thanks to you fine folks my printer already does.

---

### Post by vs8 on 2010-09-30
I have the same printer but I run Ubuntu 10.04 and 10.10 both AMD 64 so no luck for me.

I contacted Lexmark to let them know about the issue and also told them 8.04 is very old and that the current LTS is 10.04. They responded and told me this:

Here is your Service Request # 1-3016078301

Thank you for contacting Lexmark Technical Support. I really do apologize for the inconvenience you have in getting this printer to work on your 64 bit machine. I understand and appreciate your desire for 64 bit Linux driver but as of now we still don't have 64 bit Linux driver available. Thank you for notifying us of your concern. I will forward your request on to our development department, as it is only through input from you, our customers, that we can make these important business decisions.

If you have any more questions or concerns, please contact me at your convenience and I will be happy to assist you. (If I am not available, another representative may reply to your request.)

To respond, please select "Reply" in your e-mail software, and be sure that the past e-mail is included in this reply.

[AOL Users: In order to include the previous e-mail, you must highlight it with your mouse when you are replying.]

If your e-mail client automatically deletes prior e-mail thread information, it will cause a delay while we look up your support history. If this is the case you may want to save the old e-mails as attachments and attach them to the current e-mail.

Sincerely,
Efren
Lexmark eSupport Team
[http://support.lexmark.com](http://support.lexmark.com)

So let's bug them, a LOT so they start working on 64 bit drivers.

---

### Post by FrF on 2010-12-05
Installing the Ubuntu 32-bit driver for the Lexmark X2670 went well for me. Neither printing nor scanning poses any problem. I'm still using Ubuntu 8.04, so sooner or later (when Hardy's support cycle comes to an end) I will have to upgrade :-)

How are your experiences with Lexmark's 32-bit drivers using, respectively, Ubuntu 10.04 and 10.10?

Thanks for any answer!

---

### Post by aetherfunk on 2011-04-25
> **DaleEMoore said:**
> I grepped for CUPS, found it in config/run.lua and commented out the version check. the x2670 installed and printed fine!

Thanks to everyone whom helped!
Dale E. Moore


I am fairly new, can you help me with the grep command you used.

---

### Post by afrodeity on 2011-06-06
Untill Natty, this was the fix
[http://ubuntuforums.org/showpost.php?p=7713382&postcount=2](http://ubuntuforums.org/showpost.php?p=7713382&postcount=2)

Now this is the problem

[http://ubuntuforums.org/showpost.php?p=10908660&postcount=46](http://ubuntuforums.org/showpost.php?p=10908660&postcount=46)

---

### Post by psychok7 on 2011-06-17
so like no solution's yet for the x64 problem? i am thinking of buying this printer but only if it works with ubuntu 11.04 x64
by the way do you know any other alternatives for it that work at the same price??

---

### Post by afrodeity on 2011-06-18
This is the solution to the driver problem. [http://ubuntuforums.org/showpost.php?p=8454063&postcount=28](http://ubuntuforums.org/showpost.php?p=8454063&postcount=28)

However I strongly discourage anybody from buying a lexmark product. The ink cartridges are chipped and nonrefillable. You are forced to buy products from Lexmark. The way they have structured the business, the cartridges are the same price as the printer. You also get very little ink. The entire thing is a scam.[IMG]http://cf.blogetery.com/165862/files/2011/06/lexmarkripoff.jpg[/IMG]

---

### Post by freeworld23 on 2011-06-20
I have the same situation with my [hp cartridges]("http://http://www.inkjetsuperstore.com/ink-cartridges/hp-inkjet-cartridges").I have had a emachine pc connected to a lexmark x1270 printer for a few years and back in few months later i purchased a new laptop toshiba and i have tried to install the old printer that i have had hooked up to the pc, to the laptop without any success at all. They said the CD is for Windows, and doesn't enable you to set up your printer on Ubuntu. You can still probably set it up, just not with the software on that CD.

---

### Post by I-User on 2011-06-29
Hi...

I am not sure if this is the correct place to post this question but I have a lexmark p704 which i am trying to set up on ubuntu 11.04 and i am having very little luck.

does anyone know how to do this?

---

### Post by afrodeity on 2011-06-29
You can manage your X2650 from here: [http://localhost:631/](http://localhost:631/)
 
I have replaced the black ink cartridge with the official 14 cartridge replacement, however I get this:
Idle - "Color Cartridge Replacement Required."

Does this mean I HAVE to replace the damn colour cartridge too? I dont need colour, all I need to do is print B&W

Please help.

---

### Post by guelo18 on 2012-01-04
I have a lexmark x2670 and i havent been able to install the driver neither the package downloaded from lexmark.com. Whaat can I do?? Please anyone!

---

