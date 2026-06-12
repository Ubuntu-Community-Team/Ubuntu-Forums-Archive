---
title: "Helppp!! printer issue"
date: 2012-07-12
forum: General Help
---

### Post by choochoousmc on 2012-07-12
I am using Ubuntu 11.04 on an Acer Aspire I have a Epson NX510 all in one.
I installed 11.04 last year with the printer.
EVERYTHING worked great till this spring.
Printing from Libre office seemed ok, but print was very light.
Printing my checkbook register from online from bank Was great.
All of a sudden, the print icon would appear, then system would lock up.
Have to reboot.
Then the first page header info from bank (ACCOUNT NUMBER ETC) would print fine.
But the data (deposits, debits, credits amounts) either would not print or be so light as to barely see.
If I pretended to change ink cartridge and let recharge, then all would print.
So I deleted the printer, unplugged let set couple days. Rebooted system and tried again
Reinstalled the printer. Test pages print perfectly. But again the bank statement wouldn't.
I have deleted and rebooted and reinstalled several times same results.
Today I tried a bank statement again. Main page header printed fine, but rest NO.
I tried to do a reprint of the the statement, printer won't even activate and the print icon does not show up.

So does anybody know what to do to get the printer working again?
Thanks

---

### Post by irv on 2012-07-12
The first thing I would try is to delete the printer and then re-add it. I has some issues with a printer in 12.04, and I did this and it fixed the problem.
At least this a place to start.

---

### Post by choochoousmc on 2012-07-12
i have done the delete and add several time. no good

---

### Post by jmfal on 2012-07-12
Go to printer in systems settings, click on printer to highlight then right click>>>properties>>check for error messages

---

### Post by choochoousmc on 2012-07-12
nope no error messages
s;; the info I have is in the first post.
It just will not print the data at the bank website, but yet windows will with the
same printer

---

### Post by kurt18947 on 2012-07-13
How does your printer behave when printing from other applications?  For example printing a Libre Office document or a simple .txt file in gedit?  I'm wondering if it's a printer problem or a browser/web site problem.  How do the pages look when viewed in print preview?  You could try printing your problem pages to pdf -- select "print to file" as the printer and save.  Then see how the .pdf file opens in viewer and how the  file prints.  If the printer prints test pages properly it doesn't really sound like a hardware problem IMO.

SWMBO *loves* to print shopping-related web pages.  Some pages print quite well, quite a lot don't.  I installed a Firefox add-on, Screenshooter to save the page as a .png file then print the .png file.  Not an elegant or optimal solution but it works most of the time.

---

### Post by irv on 2012-07-13
What browser are you using? Have you tried a different browser to see it this make a difference? Just trying to pin point where the problem is. Maybe it could be the browser is the problem?

---

### Post by choochoousmc on 2012-07-13
> **kurt18947 said:**
> How does your printer behave when printing from other applications?  For example printing a Libre Office document or a simple .txt file in gedit?  I'm wondering if it's a printer problem or a browser/web site problem.  How do the pages look when viewed in print preview?  You could try printing your problem pages to pdf -- select "print to file" as the printer and save.  Then see how the .pdf file opens in viewer and how the  file prints.  If the printer prints test pages properly it doesn't really sound like a hardware problem IMO.

SWMBO *loves* to print shopping-related web pages.  Some pages print quite well, quite a lot don't.  I installed a Firefox add-on, Screenshooter to save the page as a .png file then print the .png file.  Not an elegant or optimal solution but it works most of the time.

Just reconfirmed everything I can.
I am using a netgear router. Been using it since day 1
Printer nx515   first install 2 yr ago, has worked great until recently.
WIFI light is on on the printer.
Just confirmed the url 192.168.1.2 is the same on the printer and in the printer setup on Ubuntu.
Computer WIFI is working as It talks with the router.
Just tried printing a document from Libre office.  Nothing happens.
The printer icon is not popping up in the upper menu bar.
Pull up the printer properties, the print job is queued, but nothing happens.
I too thought it was an online thing. But apparently not.
The computer system for some reason has stopped talking to the printer.

I wonder, is there a key combination that I have to use to turn on the radio signal from the computer to the printer.
My cat sometimes get's up and maybe he inadvertently hit the right keys and turned it off??
Since I wiped the disk when I installed Ubuntu I don't have access to the help file.

It's a Acer Aspire 5532

---

### Post by choochoousmc on 2012-07-13
> **irv said:**
> What browser are you using? Have you tried a different browser to see it this make a difference? Just trying to pin point where the problem is. Maybe it could be the browser is the problem?


Been using firefox all along. 
I just replied to another helper. 
I wonder if my radio signal to the printer has quit working.
Don't have the help manual for this computer .

---

### Post by choochoousmc on 2012-07-13
I think I found the problem.
Printer says it's location is 192.168.1.2
Go to admin> printer> properties   It says the same thing.

BUT printer properties in Libre Office say 162.198.1.2

So it is sending to the print queue. But when It can't find a printer at that address is stops.

But I can NOT find a way in Libre Office to change it.

---

### Post by choochoousmc on 2012-07-13
found how to correct. Shut Libre Office down, restart and it made the correction.
If I open printer properties, it says the job is queued and processing.
But then it shuts down. printer status stopped.
So still don't know why it just quit printing

---

### Post by kurt18947 on 2012-07-14
> **choochoousmc said:**
> I think I found the problem.
Printer says it's location is 192.168.1.2
Go to admin> printer> properties   It says the same thing.

BUT printer properties in Libre Office say 162.198.1.2

So it is sending to the print queue. But when It can't find a printer at that address is stops.

But I can NOT find a way in Libre Office to change it.

I'm confused. Libre Office just uses installed system printers, it doesn't make any changes to my knowledge.  You don't have two copies of the same printer installed?  I've had that happen inadvertently.  An incorrect i.p. address would certainly cause problems.

---

### Post by choochoousmc on 2012-07-14
> **kurt18947 said:**
> I'm confused. Libre Office just uses installed system printers, it doesn't make any changes to my knowledge.  You don't have two copies of the same printer installed?  I've had that happen inadvertently.  An incorrect i.p. address would certainly cause problems.

Nope only have the one.
Did my weekly reboot this am.  Now the printer icon appeared in the upper menu bar.
Says I tried to print document 11 hr ago but process has stopped.
Tried a reprint. Still failed even though all the settings appear correct.
A diagnostic came up. Ran it. Still no print, not even a test page now.
The diagnostic report is quite long.
The print control window, says data was successfully transmitted. And is in the queue.
But doesn't actually print. Has new ink cartridges properly installed.
This is aggravating as it just did it.
I wonder if companies are writing a failure bug into their products so they will fail, thus you have to buy new?
will try deleting and re-adding one more time.
what printer does everybody else use?  Best cost on replacement ink?

---

### Post by irv on 2012-07-14
Have you looked here yet: [https://wiki.ubuntu.com/DebuggingPrintingProblems]("https://wiki.ubuntu.com/DebuggingPrintingProblems")

---

### Post by choochoousmc on 2012-07-14
ok. deleted again
re-installed
asked to print test    said yes    test printed fine
opened libre write.
tried to print document.
printer started and  acted like it printed.
no ink on page.
tried to print again now won't activate the printer at all.
ink quality setting is set at BEST

I'm stymied why??

---

### Post by irv on 2012-07-14
> **choochoousmc said:**
> ok. deleted again
re-installed
asked to print test    said yes    test printed fine
opened libre write.
tried to print document.
printer started and  acted like it printed.
no ink on page.
tried to print again now won't activate the printer at all.
ink quality setting is set at BEST

I'm stymied why??
Why don't you try installing 
[ATTACH]221251[/ATTACH] Try to print and if it works, Completely uninstall your office package and then try reinstalling it.

---

### Post by offgridguy on 2012-07-14
I had recent printer issues, had to install the driver from the printer website.  Since you have been
using your printer all along with no problems, it seems unlikely but you could try to reinstall the
driver for your printer.  In my case like yours my printer worked when connected to my computer
on windows 7, but not on my computer operating on ubuntu 12.04, also an acer, model5735.

---

### Post by choochoousmc on 2012-07-15
I have added and deleted the printer at least ten times in the last two weeks.
Nothing works.
The install driver function in Ubuntu fails every time (the proprietary one).
But it has worked all this time on the default driver.
If I do print test page while adding the printer, it prints just fine.
If I try to print a document    or    a web page it fails.
Sometimes it will run the paper through the printer but paper comes out blank
Sometimes it does nothing, even though the print dialog box says data was successfully sent to printer.
The print in progress icon sometimes does not appear in the upper menu bar.
Sometimes it does. Some times you can read the menus in it, sometimes just zeroes.
Sometimes at my bank statement, it prints the banks header (my account number etc)
which is a graphic, but rest of page is blank
Yesterday I copied the document I wanted to print to a USB. Put it in the windows computer. it ran the paper through the printer but came out blank.
Has new ink cartridges and I even put a older black back in still blank.
This has me stymied.
Maybe the printer software in the printer has gotten damaged?
Guess will try a cable connection next.
Is there a place on ubuntu that I can completely delete the printer driver  / cups file and reinstall just that?
I hate the new unity desktop. So don't want to upgrade. Also don't want to buy yet again another printer. But I do need to be able to print!

---

### Post by irv on 2012-07-15
Are you saying you can't print in Windows also, or just the document you created? What did you use to create the document? Try just using a text editor and see if it will print.

Also just a side thing to check is the broken packages in your package manager. Just to make sure that something didn't get broken while doing all the un-installing and re-installing.

---

### Post by choochoousmc on 2012-07-15
> **irv said:**
> Are you saying you can't print in Windows also, or just the document you created? What did you use to create the document? Try just using a text editor and see if it will print.

Also just a side thing to check is the broken packages in your package manager. Just to make sure that something didn't get broken while doing all the un-installing and re-installing.

I typed a document in ubuntu in Libre office. Just one page of text.
Will not print in Ubuntu. Says data sent successfully and Processing.
But it never actually does anything.
Copied file to USB. Went to my  win 7 computer. Used open office. Tried to print to same printer. Ran the paper through but no ink on the paper.

That's what I was asking about damaged printer files, PACKAGES.
How do I check for corrupted ones. 
How to delete them and reinstall just them.

Since the problem is happening in both Windows and Ubuntu, It seems a printer problem.
Printer is on a surge protected battery back up system. 
But still from Ubuntu a print test page during install the printer works fine.
So why does it not work when printing a document???
Thanks

---

### Post by irv on 2012-07-15
What I was suggesting was to go to the package manager and check for broken packages.
[ATTACH]221312[/ATTACH]

---

### Post by choochoousmc on 2012-07-15
> **irv said:**
> What I was suggesting was to go to the package manager and check for broken packages.
[ATTACH]221312[/ATTACH]



ohhh  I didn't know where to go. Will go try that now and see
thanks

---

### Post by choochoousmc on 2012-07-17
well went to synaptics.
Ran a check
33,719 packages listed
1733   installed

zero broken
So i am  still stymied.

Think I will pickup a new external hard drive. Save all my personal stuff.
Then wipe ubuntu, re install.
If that don't work I guess a new printer

Any other suggestions would be appreciated.
Plus input on what all in one printers  others are using.

---

### Post by MckayKnight on 2012-07-17
Have you tried a fresh install of 12.04 LTS or an upgrade?
Newer versions of Ubuntu tend to have upgraded kernels perhaps it contains a driver for your printer.

Nonetheless you could try finding a newer driver for your printer.
When I tried to install my printer for Ubuntu 12.04 LTS the driver wasn't built into the kernel and I had to fetch a driver.

Your Printer manufacturer may contain a Ubuntu driver for your particular printer.

But from then on there was no driver for my Ubuntu version so I had to use a driver suited for Ubuntu 11.04 and it worked just fine with my Ubuntu version.

It pretty much solved my printer problems that I had trouble with at the time.

By the way newer kernels can contain newer drivers, features, bug fixes etc...
Ubuntu 11.04 from what I know isn't supported anymore whereas Ubuntu 12.04 LTS (long-term support release) will be supported for 5 years.

---

### Post by choochoousmc on 2012-07-17
> **MckayKnight said:**
> Have you tried a fresh install of 12.04 LTS or an upgrade?
Newer versions of Ubuntu tend to have upgraded kernels perhaps it contains a driver for your printer.

Nonetheless you could try finding a newer driver for your printer.
When I tried to install my printer for Ubuntu 12.04 LTS the driver wasn't built into the kernel and I had to fetch a driver.

Your Printer manufacturer may contain a Ubuntu driver for your particular printer.

But from then on there was no driver for my Ubuntu version so I had to use a driver suited for Ubuntu 11.04 and it worked just fine with my Ubuntu version.

It pretty much solved my printer problems that I had trouble with at the time.

By the way newer kernels can contain newer drivers, features, bug fixes etc...
Ubuntu 11.04 from what I know isn't supported anymore whereas Ubuntu 12.04 LTS (long-term support release) will be supported for 5 years.

I just stated I may be forced to do a re-install.
However the printer worked fine with the current default setup for the last 1 to 1 1/2 years.
This is something that just happened.
Yesterday I reset the printer via it's control panel to default settings.
Re-installed the printer in Ubuntu 11.04
Used synaptics package manager to update packages and check and repair any broken packages.  It didn't find any broken, but updated 12.
Tried printing the document again.
Ubuntu / Libre Office reports sending the data to the queue and data went successfully.
But the printer did nothing.
But yet if I select print test page when installing, it prints perfectly.
So I am stymied.
why does it print a test page, but won't print a document or a webpage?

New drivers shouldn't matter as it had been working perfectly for over a year!

---

### Post by irv on 2012-07-17
I'm going to be honest with you, I have had issues like this in the past and tried everything I could think of to get them fixed and spent hours trying and getting advice on the forum and in the end did a clean start.

Now I see that you are using 11.04 and I would suggest doing a clean install with 12.04 (which has some nice improvements). This may seem like a drastic move, but it may save you time and headaches in the long run. This is just really my opinion, but it is what I would do.

I just got through fighting a problem and it turn out to be a browser issue, so it was an easy fix. But I was thinking about a reinstall the OS, and all I ended up doing was to reinsall the browser. I hope you find the answer to this problem, but at this point I am not sure what else to tell you. Sorry.

---

### Post by choochoousmc on 2012-07-17
> **irv said:**
> I'm going to be honest with you, I have had issues like this in the past and tried everything I could think of to get them fixed and spent hours trying and getting advice on the forum and in the end did a clean start.

Now I see that you are using 11.04 and I would suggest doing a clean install with 12.04 (which has some nice improvements). This may seem like a drastic move, but it may save you time and headaches in the long run. This is just really my opinion, but it is what I would do.

I just got through fighting a problem and it turn out to be a browser issue, so it was an easy fix. But I was thinking about a reinstall the OS, and all I ended up doing was to reinsall the browser. I hope you find the answer to this problem, but at this point I am not sure what else to tell you. Sorry.

Well first I despise the new unity desktop so will likely stay with 11.04 as long as I can.
I doubt it is the browser itself. But the browser has just been updated and problem still there.
So my question is (no answer expected) Why did it just all of a sudden crash (printer).
Why does it print the test page and not anything else
Now it isn't printing in Windows either.
So it could be a Ubuntu problem or a printer.
Guess I will get a USB external drive. Back all data to it.
remove 11.04 and reinstall. If fixed fine.
If not a different printer.
What a PIA!!

---

### Post by kurt18947 on 2012-07-18
You **do** realize you can use 12.04 and not use Unity, right?  I agree with Irv, a reinstall might be your simplest fix.  As I recall when using 11.04 it was .... imperfect.  And Unity on 11.04 SUCKED!!  I'm still not a Unity fan but Unity on 12.04 is better than Unity on 11.04 in my experience.  Another consideration is that 11.04 support ends this October.  Yes, it will still function but no more bug fixes or security updates.

Do you have any way to install 12.04 without destroying your current setup?  Such as doing a real install to a USB drive, not a live install?  I don't know that you could install your printer to a live USB install and test its functions though I've never tried.  I think formatting a USB drive to ext* and installing you might be able to install your printer and test its function.  Running over a USB connection would be pretty slow but should let you determine if your problems continue on a fresh install without changing your current install.  

I use a utility that enables me to have more than 4 primary partitions and to boot 100+ operating systems, each in its own isolated partition.  That capability is useful in situations such as yours  where I don't want to destroy an existing install but want to try a clean install to see if a problem is fixed by a fresh install, or to check out different distros and new releases.  Speed is not limited like a USB install.

---

### Post by irv on 2012-07-18
> **choochoousmc said:**
> Well first I despise the new unity desktop so will likely stay with 11.04 as long as I can.
I doubt it is the browser itself. But the browser has just been updated and problem still there.
So my question is (no answer expected) Why did it just all of a sudden crash (printer).
Why does it print the test page and not anything else
Now it isn't printing in Windows either.
So it could be a Ubuntu problem or a printer.
Guess I will get a USB external drive. Back all data to it.
remove 11.04 and reinstall. If fixed fine.
If not a different printer.
What a PIA!!
What desktop are you using if you are not using Unity?
You can install any Distro on a USB drive, I have done it many times. Like what was said, use gparted and format it to ext4. Boot with the live CD and do an install and make sure you pick the sdb and not the sda to install on. When the install is done, just boot from the USB and install your printer and see if it will work.
Also I will say again go with the latest version of Ubuntu, In fact if you are going to do testing, why not try 12.10 beta? Just a thought. I just purchased a SSD and I am going to install 12.10 on it and do some beta testing. I have been reading about some of the new feature in 12.10 and I think I am liking them. Things do get better but with that there are also bugs.

EDIT: I forgot to mention. If your printer problem is not the printer, it could very well be the kernel. If the kernel changed this could have been when your problem started. Try an older kernel and see if this will fix your problem.

---

### Post by choochoousmc on 2012-07-19
> **irv said:**
> What desktop are you using if you are not using Unity?
You can install any Distro on a USB drive, I have done it many times. Like what was said, use gparted and format it to ext4. Boot with the live CD and do an install and make sure you pick the sdb and not the sda to install on. When the install is done, just boot from the USB and install your printer and see if it will work.
Also I will say again go with the latest version of Ubuntu, In fact if you are going to do testing, why not try 12.10 beta? Just a thought. I just purchased a SSD and I am going to install 12.10 on it and do some beta testing. I have been reading about some of the new feature in 12.10 and I think I am liking them. Things do get better but with that there are also bugs.

EDIT: I forgot to mention. If your printer problem is not the printer, it could very well be the kernel. If the kernel changed this could have been when your problem started. Try an older kernel and see if this will fix your problem.

The old gnome desktop.
I just don't like the new unity. Maybe after a couple more releases when they have the bugs fixed, have it polished a little more. Fix a few of the issues people have complained of.
Today I hooked a USB cable from Ubuntu to the printer, It went through the motions of printing the document, but page was blank.
I was reading about epson nx 510 / 515 printers needing to have the print heads cleaned if not used regularly.
I was under the impression the print head was in the cartridge. From what I read there is another section to the head in the printer.
So before rushing out and buying a new printer I will see about clening the other part.
But still doesn't explain why it does nothing wirelessly!

---

### Post by kurt18947 on 2012-07-20
> **choochoousmc said:**
> The old gnome desktop.
I just don't like the new unity. Maybe after a couple more releases when they have the bugs fixed, have it polished a little more. Fix a few of the issues people have complained of.
Today I hooked a USB cable from Ubuntu to the printer, It went through the motions of printing the document, but page was blank.
I was reading about epson nx 510 / 515 printers needing to have the print heads cleaned if not used regularly.
I was under the impression the print head was in the cartridge. From what I read there is another section to the head in the printer.
So before rushing out and buying a new printer I will see about clening the other part.
But still doesn't explain why it does nothing wirelessly!

I'm not familiar with the nx 5xx Epsons but had an old Epson photo printer.  Same deal, it had a separate print head, not built into the cartridges.  It needed to do something every couple weeks or the head would plug and it took several cleaning cycles to get all the nozzles working properly.  I sorta prefer the print head in the cartridge but AFAIK only some HPs and maybe Lexmark/Dell are still doing print head in the cartridge and not all models are the same.  For instance I had an HP Photosmart 6 color printer that had separate ink tanks and print head.

---

### Post by choochoousmc on 2012-07-20
> **kurt18947 said:**
> I'm not familiar with the nx 5xx Epsons but had an old Epson photo printer.  Same deal, it had a separate print head, not built into the cartridges.  It needed to do something every couple weeks or the head would plug and it took several cleaning cycles to get all the nozzles working properly.  I sorta prefer the print head in the cartridge but AFAIK only some HPs and maybe Lexmark/Dell are still doing print head in the cartridge and not all models are the same.  For instance I had an HP Photosmart 6 color printer that had separate ink tanks and print head.

This Epson has separate cartridges that plug in. But then goes to a print head as I understand it.
But still it always prints a good test page, so the nozzles can't be plugged.
It just no longer prints wirelssly from Ubuntu. By that I mean, nothing happens, doesn't energize the printer. Using USB it went through print motions, but no ink on page.
windows, it goes through the motions but again no ink on page.
So Why does it print the test page perfectly but won't print a document??

---

### Post by kurt18947 on 2012-07-20
> **choochoousmc said:**
> This Epson has separate cartridges that plug in. But then goes to a print head as I understand it.
But still it always prints a good test page, so the nozzles can't be plugged.
It just no longer prints wirelssly from Ubuntu. By that I mean, nothing happens, doesn't energize the printer. Using USB it went through print motions, but no ink on page.
windows, it goes through the motions but again no ink on page.
So Why does it print the test page perfectly but won't print a document??

I don't have Epson printers, mostly Brother and one 'classic' HP Deskjet.  In each case I was able to assign a static I.P. address to the printer or printer server.  Then go to printer properties and check the 'device URI' window.  The default is something like 

```
usb://something/something/serial#
```I changed the device URI to

```
socket://xxx.xxx.xxx.xxx:9100  
```where x= the i.p address

That has been all that's required for me.

I have no clue why your printer will print a test page but won't print from an application.  My only thought would be to find the .ppd file, open it in a text editor and see if anything sticks out as 'odd'.  It's possible to send a print job to a printer from a terminal but I don't know how to do it.  That might be worth some research, take any applications or desktop environments out of the process.  I'm not sure what connections are supported,  I'd speculate USB might work, wireless networking may not.

---

### Post by choochoousmc on 2012-07-23
> **kurt18947 said:**
> I don't have Epson printers, mostly Brother and one 'classic' HP Deskjet.  In each case I was able to assign a static I.P. address to the printer or printer server.  Then go to printer properties and check the 'device URI' window.  The default is something like 

```
usb://something/something/serial#
```I changed the device URI to

```
socket://xxx.xxx.xxx.xxx:9100  
```where x= the i.p address

That has been all that's required for me.

I have no clue why your printer will print a test page but won't print from an application.  My only thought would be to find the .ppd file, open it in a text editor and see if anything sticks out as 'odd'.  It's possible to send a print job to a printer from a terminal but I don't know how to do it.  That might be worth some research, take any applications or desktop environments out of the process.  I'm not sure what connections are supported,  I'd speculate USB might work, wireless networking may not.

I have no idea either. It just all of a sudden started. It's almost like I got a virus or something.
I connected USB cable. Ubuntu found and installed the default driver. Proprietary ones won't download, something about an insecure certificate. Won't let me download, 
Just tried printing again after both computer and printer off all weekend.
Wirelessly prints the test page right off the bat from Ubuntu.
Will not print the document. It kills the print queue process. Says data was successfully sent to printer then nothing.
Windows 7 ejects a blank page when printing the same document.
So either the printer has two separate print functions
one for the self test and test page, which is working
second one accepts and prints data from applications, which is not working.
Or something in Ubuntu is screwed up
Synaptics says all packages are up to date and in good condition.
I hate to buy another printer needlessly.

---

### Post by choochoousmc on 2012-07-24
Well I bought a NEW Hewlett Packard printer. yesterday.
3522e all in one.
Installed cartridges etc. Printed test page automatically. good.
Tried to install from UBUNTU...... no printer found.
checked the printer  it has not found the router and no way to force it.
No installation manual, nothing about doing USB first.
The CD rom can not be used for Ubuntu. NO manual in plain text form or pdf.
Called HP after no help online.
Tech said he had to transfer me to a tech guy with Linux.
Phone went dead.
So back to square one! Still don't have print.
Using USB printer comes up. But will not print from UBUNTU. Tried to print test page, nothing printer does not operate.
This is driving me crazy!!

---

### Post by kurt18947 on 2012-07-24
With the HP, the most you should have to do is install hplip & hplip-gui from the repositories.  I don't have hplip installed by default so you might have to do that, or just plugging in the HP printer and doing update/upgrade might be enough, I don't know.  Does the HP work with Win 7?  If not I'd suspect some sort of PC or cable issue;  having two printers from different manufacturers misbehave in the same fashion seems highly unlikely.  The common thread would be the PC.

---

### Post by irv on 2012-07-24
> **choochoousmc said:**
> Well I bought a NEW Hewlett Packard printer. yesterday.
3522e all in one.
Installed cartridges etc. Printed test page automatically. good.
Tried to install from UBUNTU...... no printer found.
checked the printer  it has not found the router and no way to force it.
No installation manual, nothing about doing USB first.
The CD rom can not be used for Ubuntu. NO manual in plain text form or pdf.
Called HP after no help online.
Tech said he had to transfer me to a tech guy with Linux.
Phone went dead.
So back to square one! Still don't have print.
Using USB printer comes up. But will not print from UBUNTU. Tried to print test page, nothing printer does not operate.
This is driving me crazy!!
Is this a network printer? or are you using a USB cable connecting to the computer? If this is a Network printer you need to setup the printer to function on the Network first before Ubuntu will see it. I have an older HP, a 4050 with a network card installed. I needed to go into setup and assign an ip address to the printer and then went to printer setup in Ubuntu and set as a network printer and it search the network and found the printer and setup the ip address as it's port.

---

### Post by kurt18947 on 2012-07-24
If it's an consolation, I had my main Brother MFC do sort of what you're seeing.  It'd put out blank pages when printing from Libre Office.  If I pasted a graphic or screencap into L.O. writer, it'd print the image - a bit larger than a postage stamp :razz:.  I uninstalled that printer, ran Bleachbit as root and reinstalled.  The point being Libre Office may have printing issues if the printer driver is a little bit crossways for whatever reason.

---

### Post by choochoousmc on 2012-07-25
> **kurt18947 said:**
> With the HP, the most you should have to do is install hplip & hplip-gui from the repositories.  I don't have hplip installed by default so you might have to do that, or just plugging in the HP printer and doing update/upgrade might be enough, I don't know.  Does the HP work with Win 7?  If not I'd suspect some sort of PC or cable issue;  having two printers from different manufacturers misbehave in the same fashion seems highly unlikely.  The common thread would be the PC.

I have not tried the new printer with win 7 I don't use the win 7 machine for day to day stuff.
Right now the new HP printer is not connecting to the wireless router.
Ubuntu "sees" the new hp printer in the wireless connections applet icon in upper menu bar.  But will not print to it, Even with the usb cable connected it will not print to it.
Wireless and USB cable there is NO print to my Epson printer or the new HP.
so either the printer, router, or computer has gone broke.
driving me crazy!
But the router is working for everything else.

---

### Post by choochoousmc on 2012-07-25
> **kurt18947 said:**
> If it's an consolation, I had my main Brother MFC do sort of what you're seeing.  It'd put out blank pages when printing from Libre Office.  If I pasted a graphic or screencap into L.O. writer, it'd print the image - a bit larger than a postage stamp :razz:.  I uninstalled that printer, ran Bleachbit as root and reinstalled.  The point being Libre Office may have printing issues if the printer driver is a little bit crossways for whatever reason.
I will try that.
All else fails I will reinstall 11.04. If that does not work I may have to upgrade to 12.04  etc.
Since both win7 and ubuntu does it with old and new printer I am stymied.
Only other hardware is the router. But i don't see how that can be. Considering the problem still exists with the USB cable.

---

### Post by irv on 2012-07-25
> **choochoousmc said:**
> I will try that.
All else fails I will reinstall 11.04. If that does not work I may have to upgrade to 12.04  etc.
Since both win7 and ubuntu does it with old and new printer I am stymied.
Only other hardware is the router. But i don't see how that can be. Considering the problem still exists with the USB cable.

From everything I have read it sound like the printer except for printing the test page. Is there a way you could try this printer on another system altogether? That would tell the real story.

I still think you should not install 11.04, but go with 12.04. It is so much better. They improved it over 11.04. I find I like it much better.

---

### Post by choochoousmc on 2012-07-25
> **irv said:**
> Is this a network printer? or are you using a USB cable connecting to the computer? If this is a Network printer you need to setup the printer to function on the Network first before Ubuntu will see it. I have an older HP, a 4050 with a network card installed. I needed to go into setup and assign an ip address to the printer and then went to printer setup in Ubuntu and set as a network printer and it search the network and found the printer and setup the ip address as it's port.

please explain about assigning the ip address.
I can NOT do it on the printer.
I can assign one from printersetup in Ubuntu.
Is that what you mean?
My old epson was 192.168.1.2
since it is deleted and turned off, could I use that one now?

---

### Post by choochoousmc on 2012-07-25
> **irv said:**
> From everything I have read it sound like the printer except for printing the test page. Is there a way you could try this printer on another system altogether? That would tell the real story.

I still think you should not install 11.04, but go with 12.04. It is so much better. They improved it over 11.04. I find I like it much better.

It does not work wirelessly from a win7 system either.
That's why I thought it was a printer issue.
I'm trying not to upgrade my system.
I don't like the unity desktop. But might have no choice.
The new HP refuses to find and connect to the router.

---

### Post by kurt18947 on 2012-07-25
> **choochoousmc said:**
> It does not work wirelessly from a win7 system either.
That's why I thought it was a printer issue.
I'm trying not to upgrade my system.
I don't like the unity desktop. But might have no choice.
The new HP refuses to find and connect to the router.

Bear in mind that you DO NOT have to use Unity with 12.04.   Xubuntu, Lubuntu, Kubuntu, Cinnamon and MATE all come to mind.  These all have their roots in 12.04.  In fact if you're really enamored of gnome 2, a Mint Maya live CD/USB with MATE might be a good choice.  You wouldn't have to mess with your existing install.  My Mint Maya install came with hplip (but no hplip-gui)installed.

---

### Post by choochoousmc on 2012-07-26
Update.
The new HP3522 will NOT find my router.
Checked the router firmware, it is current.
My router is NOT security protected.

Downloaded the hplip software.
says we must temporarily use the USB cable

The printer and Ubuntu are connected.   Cannot print even with USB not even test page
HPLIP says not all printers are supported, but doesn't say which ones are.

HPLIP will not find the printer. 

In UBUNTU in the network icon in upper panel, it sees the printer wireless signal.
HP online says I can connect UBUNTU directly to the printer wirelessly and print that way. Haven't tried. Seems senseless to always disconnect from router and connect to printer. then reverse later. Also cannot print web page unless connected thru router.

Note:   Using UBUNTU 11.04 with netgear wndr3700 router and epson nx510/515 printer
              worked perfectly unti about 4 months ago. The started printing blank pages.
            If I pretended to change cartridges and rechare ink, worked fine. Then that 
            wouldn't work. Finally no print at all. Tried same on win7. It would run paper
            through but no print action.
             Connected printer to Ubuntu via USB, still no print.  Assumed bad printer.
          Bought new HP3522: It does not see the router, follow hp guidelines to setup
          online and with HPLIP software. Still no print.

Looking at  reinstall11.04 first. Then 12.04 if I have too.
How can I save mt bookmarks to USB stick or external Hard drive.
How can I save ALL my Email to a master file and then return to the system after the
reinstall is complete.

Any other ideas why all of a sudden I am not getting print function. Synaptics says no broken packages. I ran anti virus and bleach bit

---

### Post by irv on 2012-07-26
> Looking at reinstall11.04 first. Then 12.04 if I have too.
How can I save mt bookmarks to USB stick or external Hard drive.
How can I save ALL my Email to a master file and then return to the system after the
reinstall is complete.
What are you using for a browser? If it is firefox, copy a hidden folder call .mozlla to your USB. It has all your bookmarks.
What are you using for email. If you use an online email all your emails will be there. Changing OS does not affect them. If you are using something like Thunderbird, then you have to look for a hidden folder in your home directory. It will start with a "."
Hope this helps.
Edit:  
[ATTACH]221837[/ATTACH]

---

### Post by kurt18947 on 2012-07-26
You probably have to use a USB cable to configure the network on the printer.  I don't have an HP printer so don't know how to go about that.  The multi-functions I've messed with use the numeric keypad to enter I.P. addresses etc.  Have you tried a live install yet?  It seems like that would be far less disruptive than ripping out your existing stuff.  In your case current Mint with the MATE desktop seems like a good choice.  MATEseems functionally identical to Gnome 2.   It's also possible to install a fully functional install on a USB key.  Format the key with an ext file system and use the manual install procedure be make sure things go where you intend.  An OS on a USB key is kinda slow but it does work.

---

### Post by choochoousmc on 2012-07-26
> **kurt18947 said:**
> Bear in mind that you DO NOT have to use Unity with 12.04.   Xubuntu, Lubuntu, Kubuntu, Cinnamon and MATE all come to mind.  These all have their roots in 12.04.  In fact if you're really enamored of gnome 2, a Mint Maya live CD/USB with MATE might be a good choice.  You wouldn't have to mess with your existing install.  My Mint Maya install came with hplip (but no hplip-gui)installed.

I may have to contact you later for more info on what you said.
last I heard 11.04 was last version to allow you to choose between unity and gnome during log on.
Unity to me is counterproductive. I need 2 or more programs / windows open simultaneously as I am usually doing more than one task.
In gnome, I could see open windows at bottom of screen. In unity that feature disappeared.
Is there a way to make unity to show at all times which programs are currently being used.
such as in bottom panel, I have Thunderbird, firefox, and libre office running and when appropriate the update manager will appear.

---

### Post by irv on 2012-07-26
Also it should tell you how to setup your printer to function on the network. If you don't have the manual here is a link to [HP online manuals]("http://h10025.www1.hp.com/ewfrf/wc/manualCategory?cc=us&dlc=en&lang=en&lc=en&product=5231946&")

---

### Post by choochoousmc on 2012-07-26
> **irv said:**
> What are you using for a browser? If it is firefox, copy a hidden folder call .mozlla to your USB. It has all your bookmarks.
What are you using for email. If you use an online email all your emails will be there. Changing OS does not affect them. If you are using something like Thunderbird, then you have to look for a hidden folder in your home directory. It will start with a "."
Hope this helps.
Edit:  
[ATTACH]221837[/ATTACH]
Yes I am using firefox. Will look for the .mozilla file
yes I am using thunderbird. I believe all emails I need are on line at my ISP's website.
As I only read. I delete what I don't want but some are needed, so I nhave thunderbird set to leave on server. But some I have moved to another folder so will have to check them.

I found out why HPLIP is not working.
The version in repository is 3.11.xx
                                      But this printer needs   3.12.6
I can download on line, but not sure how to install yet.
But still does not explain why it does not see the router.
or won't print even with the usb cable attached

---

### Post by irv on 2012-07-26
> **choochoousmc said:**
> Yes I am using firefox. Will look for the .mozilla file
yes I am using thunderbird. I believe all emails I need are on line at my ISP's website.
As I only read. I delete what I don't want but some are needed, so I nhave thunderbird set to leave on server. But some I have moved to another folder so will have to check them.

I found out why HPLIP is not working.
The version in repository is 3.11.xx
                                      But this printer needs   3.12.6
I can download on line, but not sure how to install yet.
But still does not explain why it does not see the router.
or won't print even with the usb cable attached
The reason it doesn't see the router is because you need to setup the printer to see it. I looked at the manual. Here is a link to the manual that I was looking at. You need to go into the setup on the printer and give it your network information for your router. [http://h10032.www1.hp.com/ctg/Manual/c03355292.pdf]("http://h10032.www1.hp.com/ctg/Manual/c03355292.pdf")
If you need to update the BIOS in the printer I am sure the manual will tell you how.

---

### Post by kurt18947 on 2012-07-26
> **choochoousmc said:**
> I may have to contact you later for more info on what you said.
last I heard 11.04 was last version to allow you to choose between unity and gnome during log on.
Unity to me is counterproductive. I need 2 or more programs / windows open simultaneously as I am usually doing more than one task.
In gnome, I could see open windows at bottom of screen. In unity that feature disappeared.
Is there a way to make unity to show at all times which programs are currently being used.
such as in bottom panel, I have Thunderbird, firefox, and libre office running and when appropriate the update manager will appear.

Feel free to ask away.  To add the bottom panel look at Tint2, found in the repositories.  Tint2 has a hidden config file, you can find info via a google search.  You can log onto more than Unity if you install Ubuntu.  I think my choices include:

[LIST]
[*]Ubuntu (Unity)
[*]Ubuntu 2D
[*]Gnome (gnome-shell)
[*]Gnome classic
[*]Gnome classic no-effects
[*]Xfce desktop
[*]Cinnamon
[/LIST]
I haven't tried installing MATE on this install, I may do that in the future.  Pick my flavor depending on my mood.:)  There is some 'overlap' of apps compared to a normal install but I find what I have usable.  You have choices, you just have to know how to institute them.

---

### Post by choochoousmc on 2012-07-26
newest update 7/26/2112 10:30 mtn time usa
I just reinstalled the epson as wireless.
test page printed good
tried 1 page document libre writer    fail  ran paper but no ink  INK quality= best
opened up gthumbs 2.13.1 tried print picture, wirelessly.
Plain paper only  Printed just fine.
opened gedit typed one line. tried to print.   ran paper through but no ink on page.

Am now uninstalling libre office, will reboot and reinstall libre.
Ok why will it print a picture, but not text?

In libre and gedit, could hear the print head moving back and forth!

---

### Post by choochoousmc on 2012-07-26
> **kurt18947 said:**
> Feel free to ask away.  To add the bottom panel look at Tint2, found in the repositories.  Tint2 has a hidden config file, you can find info via a google search.  You can log onto more than Unity if you install Ubuntu.  I think my choices include:

[LIST]
[*]Ubuntu (Unity)
[*]Ubuntu 2D
[*]Gnome (gnome-shell)
[*]Gnome classic
[*]Gnome classic no-effects
[*]Xfce desktop
[*]Cinnamon
[/LIST]
I haven't tried installing MATE on this install, I may do that in the future.  Pick my flavor depending on my mood.:)  There is some 'overlap' of apps compared to a normal install but I find what I have usable.  You have choices, you just have to know how to institute them.

ok thanks. Will try to keep track of this thread as I progress. Se my newest update.
Prints pictures, but not text!   ????

---

### Post by irv on 2012-07-26
> **choochoousmc said:**
> newest update 7/26/2112 10:30 mtn time usa
I just reinstalled the epson as wireless.
test page printed good
tried 1 page document libre writer    fail  ran paper but no ink  INK quality= best
opened up gthumbs 2.13.1 tried print picture, wirelessly.
Plain paper only  Printed just fine.
opened gedit typed one line. tried to print.   ran paper through but no ink on page.

Am now uninstalling libre office, will reboot and reinstall libre.
Ok why will it print a picture, but not text?

In libre and gedit, could hear the print head moving back and forth!

Have you tried different fonts? Maybe you have a screen font but not a print font installed. Just a thought.

---

### Post by welshmike on 2012-07-26
> **irv said:**
> Have you looked here yet: [https://wiki.ubuntu.com/DebuggingPrintingProblems]("https://wiki.ubuntu.com/DebuggingPrintingProblems")
Many many thanks. For some reason my HP deskjet D1600 printer was no longer working on 12.04 Unity. I followed the instructions at the link you referred to and the printer is now working.

---

### Post by irv on 2012-07-26
> **welshmike said:**
> Many many thanks. For some reason my HP deskjet D1600 printer was no longer working on 12.04 Unity. I followed the instructions at the link you referred to and the printer is now working.

Mike, I google everything and most of the help I find comes from some Linux person who points me is the right direction, so I am following the same pattern to help others. I think it is catching on. Really, it's what Ubuntu is all about, "People helping People" or humanity to other.

---

### Post by welshmike on 2012-07-27
> **irv said:**
> Mike, I google everything and most of the help I find comes from some Linux person who points me is the right direction, so I am following the same pattern to help others. I think it is catching on. Really, it's what Ubuntu is all about, "People helping People" or humanity to other.
irv, I too have found, as in this case, that posts by posters in these Ubuntu forums are very very helpful in solving any difficulties I have with Ubuntu.
As you can see I am running 12.04 (Unity). When Canonical's direction with Ubuntu became the Unity desktop I decided to stick with Ubuntu because of the Ubuntu Forums help and not run with a Linux distro like Mint that had a Gnome like desktop. 
I do find Unity a bit unhelpful when I want to find out how to do non-mainline things like I used to do on Gnome based 10.04 Ubuntu such as burn an iso to a flash drive.

---

### Post by irv on 2012-07-27
I find Ubutnu with Unity easier and better then Gnome 2.x now that I have been using it for awhile. As far as burning iso to usb I just us Unetbootin. I find setting up printer or any other hardware easy and fast. I learn to use the search and I love lens. It seem like everyday Unity is getting better.
When it first came along, I wasn't sure I liked it and moved away for it but then came back and thought I would give it a fair chance. It grows on you after awhile, I don't think I will ever go back to the old menu system with panels I like the dash,but sometimes I think it would be nice to have it on the bottom and not the left side of the screen.
OH yes, this thread is about printers. Sorry.

---

### Post by choochoousmc on 2012-07-27
> **irv said:**
> Have you tried different fonts? Maybe you have a screen font but not a print font installed. Just a thought.

No I haven't. But again it has always printed everything great.
Instead of doing a complete reinstall. I did an 11.10 upgrade through
update manager. Haven't tried printing text yet.
It did print the test page ok and wirelessly.
Will try later this weekend,.
Had two funerals to attend today.

---

### Post by choochoousmc on 2012-07-28
ok now what????
HPLIP in software center does not support the new HP3522 printer.
HP says the HPLIP version from Ubuntu is too old.
Ubuntu developers need to do a better job of keeping the repositories updated with the newer versions.
So this printer has to go back to the store.
But my original EPSON still will NOT print TEXT.
The print heads move and sound like it is printing but in end it is a blank page.
Why will it print a graphic, but not text?
I only did an 11.04 upgrade. Maybe I have to do a fresh install to clear up an issue.
I reset the epson to factory defaults, even though it had never been changed.
--------------------------------------------------------------------------------------------------------------------------------------
I still don't like the unity desktop. For me it is NOT intuitive. Takes too many mouse clicks to get where you want to go.
1st highlight the side bar, if program not there, click dash, then scroll the icons, then select one, or click a filter on right side. and then scroll icons and click one.
I think the side bar panel, should of been like the old menu system across top.
highlight it. select the the main and that opens up icons on screen then click the one you want.
The search bar what if I can't remember the name or what it starts with. nope this is not intuitive. just my 2cents. But this thread is not about unity.

---

### Post by choochoousmc on 2012-07-28
instead of mounting the printer as wireless via hplip I used the USB cable setup.
HPLIP via online cups says the printer is installed.
Tried to print a document, printer does nothing!

---

### Post by choochoousmc on 2012-07-31
Well I did a complete fresh install. Now using ubuntu 12.04
Am completely up and running. New bookmarks, all data restored to hard drive etc.
Added my original Epson NX515 printer.
During install printed a perfect test page. And quite quickly too.
Opened Libre writer.
Typed: This is a printer test
Sent to printer. Took a minute before print action started.
Ran the paper through just fine.
Can see a VERY light ink mark where the text should start, but that's it.

The HP never did connect to router.

IF I had a corrupted file in the print spooler causing this, it should be gone after a complete fresh install.
So question still remains, WHY does it print graphics and NOT plain text.

Going to open a new thread, recommendations for new printer!
Thanks for the suggestions.

---

### Post by irv on 2012-07-31
After all this, why don't you file a bug report on this printer Not working right with some applications.

---

### Post by choochoousmc on 2012-07-31
> **irv said:**
> After all this, why don't you file a bug report on this printer Not working right with some applications.

How and or where would I do it?

---

### Post by irv on 2012-07-31
Start Here:
[SIZE="3"]**[ReportingBugs]("https://help.ubuntu.com/community/ReportingBugs")**[/SIZE]

---

### Post by choochoousmc on 2012-07-31
ok issue is resolved.
Went to Office depot today. They have a pretty knowledgeable tech.
explained the situation as I have done in this thread.
He was of the opinion that a power outage or surge had damaged either a circuit board or perhaps a software file in the printer.
He said a lot of companies do as I suspected. One setup does the self test and another section handles the text printing. ??????? IDK.
Anyway I got a HP6600 / 6700. Fancier than I wanted but was on sale same price as a cheaper model. And says it will hold up better mechanically (we will see) and prints more pages for less ink.
He said even though it has a software disk for setup, you can force a wireless connection from the control panel.
He was correct. 
I am now up and running again. Printed the graphic test page.
Plus I wrote a one line text document in Libre and it printed that too.
So tomorrow I will try it on a longer text document and see what happens!
Going to mark this solved.
Thanks for the input you provided.
I am now using 12.04 and have shrunk my open windows so the side bar stays visible
Made some adjustments and just trying to get used to it.
Still miss my open windows bar at bottom of screen.

---

### Post by irv on 2012-07-31
> Still miss my open windows bar at bottom of screen.
I miss mine at first be got use to not having it. I find I can just look at the dash and see the little arrow by the open apps and using the Super key +s to switch workspaces.
Glad you found out what the problem was.

---

### Post by kurt18947 on 2012-08-02
I'm glad you were able to resolve your problem.  As for the lack of a 'bottom panel', you might take a look at Tint2, it's in the repositories.  I found the lack of a means to easily switch between open windows and applications in Unity & Gnome-shell irritating.  Tint2 is a big help.  It has a hidden config file to tweak some settings.   For instance, I removed the calendar/clock and made the panel span 99% of the screen width.
[http://code.google.com/p/tint2/](http://code.google.com/p/tint2/)
I found an GUI applet to change configurations.  It worked but didn't seem to save settings upon reboot.  Editing the config file via gedit then saving did remember changes.  The GUI may work now.

---

