---
title: "Getting laptop to print wireless"
date: 2010-11-17
forum: General Help
---

### Post by Wuxin on 2010-11-17
I just bought an IBM ThinkPad T43 and I want to be able to print from it wireless on my Brother HL 2170w printer.  I've identified the printer on Ubuntu's list of printers, but I'm unable to print through my router.  My printer is presently configured to print, wireless, from my Mac OSX desktop and I don't know if that creates a conflict.  According to the Linux dictum, however, the laptop, once configured for the Brother printer, should "just work."  Well, it doesn't!  Can anyone suggest anything that needs to be done to get the laptop to send data and print from the printer?  Suggestions will be greatly appreciated.  (Please keep explanations simple and straightforward as I'm a newbie.)

---

### Post by nunrgguy on 2010-11-17
Have you done the following:
System - Administration - Printing

Add

Network Printer
Find Network Printer

Then click on found printer

Drivers will auto install

Print test page

Close and done.

If it doesn't auto find the printer you can add it by typing in ip address etc

---

### Post by Wuxin on 2010-11-17
Where can I find the IP address, etc.?  Is it in the  basic information about my router?

---

### Post by TBABill on 2010-11-17
You shouldn't need the IP address. Click find network printer and just wait a couple minutes. It should find the printer for you, then click it and click next so the system can install the software for it.

---

### Post by Wuxin on 2010-11-17
[FONT=Times New Roman][SIZE=4]Hey thanks a lot folks...it really worked!  I'm impressed with those of you who have a good handle on Ubuntu/Linux.  Are there any good books you would recommend that can help expedite the learning curve?  (You have to forgive me--I'm of the analog "book" generation.  I need a tangible text in order to absorb large quantities of complex information!)  But again, thanks so much for your kind help and assistance![/SIZE][/FONT]

---

### Post by Kittykathy on 2010-11-25
@Wuxin

I finally was able to get this printer to work under lucid 10.04.  I already had the printer on my network installed under Windows.

You don't provide the version of Ubuntu that you've installed.  I had no problems with 9.10 and the Brother 2170W on one laptop but when I put lucid (10.04) on an Acer laptop the problems began.

I have spent numerous hours on this problem.  Scoured the forums, etc.  I tried installing using the System/Administration/Printing function.  That worked but the printer wouldn't stay enabled so when I printed  a test page it always gave me an error message, "printer not enable".  With_*** Sy***_[***syphusiian ***]("http://www.google.com/search?hl=en&&sa=X&ei=xXTuTLTFMMOqlAeL0KilDA&ved=0CB0QvwUoAQ&q=sisyphus&spell=1") effort,I enabled then tried to print and the 2170 would become magically un-enabled.

I played with cups too.  [http://localhost:631/](http://localhost:631/).

I tried this too from a forum entry by [flymw]("http://ubuntuforums.org/member.php?u=661594").

1. in web browser open [http://localhost:631/printers](http://localhost:631/printers)
  2. Click "Modify Printer"
  3. when promted enter the following:
  	LPD/LPR Host or Printer			Device
  	lpd://(192.168.0.5)/binary_p1	Device URI (***replace this with your IP adress you noted before!!!***)
  	confirm with Linux username and password

I played around with all of the information on the Brother linux support page too. Their information is really confusing and incomplete.  They don't differentiate very plainly between Intel processor installations and AMD installations.  

I added folders based upon the Brother support page.  Whether or not I really needed these folders is a mystery.  

If the 2170 is already installed wirelessly under Windows then try this.

go to System/Administration/Printing, select Add, Network Printer then find Network printer.  I selected my printer BRW00234ECE1673  which is the standard brother name with the mac address appended.

Then I modified the driver and selected the HL-2140 Foomatic/hpijs-pcl5e driver.  

Work your way back through the prompts and finish the installation.

My device URI is :  dnssd://Brother%20HL-2170W%20series._printer._tcp.local/

I attached the printer properties image.

I can't say for sure this will work for you since I tried so many other things and can't say for sure what is modified in the system but I do believe the 2170 driver does not work with lucid 10.04.  I am still a newbie plus my self but have spent numerous hours solving problems.  I have 3 linux systems, a desktop with 8.04, laptop averatec with 9.10 and an Acer 6930G plus dual boot and stand alone Windows 7 system.

I emailed Brother and they said they would assist me but the queue must be really long and like so many other companies, they are lean and mean with their customer support in India or someplace like that so bottom line I never heard back from them.

Hope this helps.

---

### Post by Wuxin on 2011-02-15
I hate to say this, but I'm still having problems getting my IBM ThinkPad to print wirelessly to the Brother HL 2170w printer.  It was working for a short time, but now all I have are a series of uncompleted text files in a document print status box with the designation "pending" by all of them.  What is this?  The printer is obviously recognized by the computer and the documents are being sent, but the print action won't go into effect.  What do I need to do?  I am running Ubuntu 10.10 with all the updates so everything should be in order as far as the OS is concerned.  Any help on this would be welcomed!  Thank you in advance!

---

### Post by marshag63 on 2011-02-16
Try deleting all the pending jobs.

MDG

---

### Post by Ibidem on 2011-02-16
[http://localhost:631/](http://localhost:631/) Add Printer Find Network Printer When it asks for driver, select: hpijs-pcl5e (See: [http://www.openprinting.org/printer/Brother/Brother-HL-2170W](http://www.openprinting.org/printer/Brother/Brother-HL-2170W)) The "Recommended" one stopped working around Lucid beta 1. Works here...eventually (DON'T try with a 24 mb postscript file!)

---

### Post by Wuxin on 2011-02-16
When I went to the print documents window, I tried to delete all of the outstanding unprinted documents, but they wouldn't delete!  I highlighted them, and clicked on "delete" but they wouldn't budge!  What goes on here?

Thanks

---

### Post by Wuxin on 2011-02-16
Okay, I already have the driver hpijs-pcl5e and still the thing won't print.  What now?

---

