---
title: "Canon Pixma MP490 Help with drivers"
date: 2009-10-23
forum: General Help
---

### Post by Amstell on 2009-10-23
My girlfriend just got an iMac and it came with a free printer.  Due to the size of our small *** apartment, the only place it will fit is in my room next to my linux box.  Ubuntu 9.10 loads up the printer and searches for drivers, but doesn't find any.  There is no MP490 listed in the drivers and Canon doesn't appear to have any available for linux on their website.

Does anyone have any suggestions as to what I could do next.  I've tried the Generic Drivers along with the Canon Pixma 240? and 500 series, but they don't work either.

Thanks for anything you can provide and give help with.

---

### Post by djyoung4 on 2009-11-01
I got the same problem.  i was thinking of getting the drivers through wine and see if it will work that way.  any other ideas

---

### Post by Ballyboard on 2009-11-28
Many Canon drivers are available from Canon Thailand. I don't know why Canon doesn't make them available in the US. Try MP490 series IJ Printer Driver Ver. 3.20 for Linux (debian Packagearchive) at [http://support-th.canon-asia.com/contents/TH/EN/0100236302.html](http://support-th.canon-asia.com/contents/TH/EN/0100236302.html). Install the two packages then go to printing in the administration menu and add a new printer... Hope this helps.

---

### Post by Ballyboard on 2009-11-28
Also, the scanner driver MP490 series ScanGear MP Ver. 1.40 for Linux (debian Packagearchive) needs to be installed as well from [http://support-th.canon-asia.com/contents/TH/EN/0100237602.html](http://support-th.canon-asia.com/contents/TH/EN/0100237602.html).  You can also get the Guide MP490 series ScanGear MP Ver. 1.40 for Linux (Operation guide) from [http://support-th.canon-asia.com/contents/TH/EN/0300278501.html](http://support-th.canon-asia.com/contents/TH/EN/0300278501.html).  I have not tried using the scanner through Gimp - I use 'scangearmp' from a terminal. Nice interface and works great.  Happy scanning...

---

### Post by ventolt on 2009-12-22
The printer works just fine but the scanner doesn't. When I press scan to PC on the printer, it says it's preparing, preparing until it says to set up the page to scan. When I type *scangearmp* in terminal, it says that it can't find supported scanner, it's unplugged or turned off.

Anyone knows what may be causing the problem? I'm using Ubuntu 9.10. Maybe there should be something else installed? OS found the printer as I plugged it in (after I installed the IJ printer driver) and added it to my printers list. It didn't say anything about the scanner, but I thought it shouldn't be shown as it's a multi-functional printer.

---

### Post by mailtodtm on 2010-01-05
I'm having a problem getting my mp490 to do anything. I downloaded these:
[http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html)
[http://support-th.canon-asia.com/contents/TH/EN/0100237602.html](http://support-th.canon-asia.com/contents/TH/EN/0100237602.html)

3.02 and 1.40 but they did not work.

In ran the install file through the terminal. The 1.40 looked like it worked but the 3.02 could not find the printer.

Any help would be greatly appreciated.

David

---

### Post by scook4242 on 2010-01-14
Ballyboard'ss approach worked flawlessly for me.  Which is saying something considering I am new to Linux as of 2 days ago.

---

### Post by jorleycom on 2010-01-29
I just wanted to add that Ballyboard's solution worked for me too. I am very new to Linux  even I could get both the printer and scanner to work.

THANKS.

---

### Post by mailtodtm on 2010-01-31
I'm using 9.10 on a brand new machine (different from my first post) and i still cant get the printer to work. This is from the terminal:


==================================================

Canon Inkjet Printer Driver Ver.3.20-1 for Linux
Copyright CANON INC. 2001-2009
All Rights Reserved.

==================================================
Execution command = sudo dpkg -iG /home/david/Downloads/cnijfilter-mp490series-3.20-1-i386-deb/packages/cnijfilter-common_3.20-1_i386.deb
(Reading database ... 138456 files and directories currently installed.)
Preparing to replace cnijfilter-common 3.20-1 (using .../cnijfilter-common_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-common ...
Setting up cnijfilter-common (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Execution command = sudo dpkg -iG /home/david/Downloads/cnijfilter-mp490series-3.20-1-i386-deb/packages/cnijfilter-mp490series_3.20-1_i386.deb
(Reading database ... 138456 files and directories currently installed.)
Preparing to replace cnijfilter-mp490series 3.20-1 (using .../cnijfilter-mp490series_3.20-1_i386.deb) ...
Unpacking replacement cnijfilter-mp490series ...
Setting up cnijfilter-mp490series (3.20-1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

## Driver packages installed. ##

#=========================================================#
#  Register Printer
#=========================================================#
Next, register the printer to the computer.
Connect the printer, and then turn on the power.
To use the printer on the network, connect the printer to the network.
When the printer is ready, press the Enter key.
> 

Searching for printers...


#=========================================================#
#  Select Printer
#=========================================================#
Select the printer.
If the printer you want to use is not listed, select Update [0] to search again.
To cancel the process, enter [Q].
-----------------------------------------------------------
 0) Update
-----------------------------------------------------------
Could not detect the target printer.
-----------------------------------------------------------
(Currently selected:[0](Update) )
Enter the value. [0]

---

### Post by mailtodtm on 2010-01-31
WORKS!!! 

Not sure why but... 

Thanks guys!

---

### Post by theaskanison on 2010-02-13
So what did you guys do?
I followed the instructions above (installed packages for printer and scanner). Added new printer (from the device list the MP490) was listed as USB connected printer. Then the system looked for the driver and took me to a list where I selected maker (canon) but in the next step this printer was not listed. So what do I do next?
I'll appreciate any help
Thx

---

### Post by theaskanison on 2010-02-13
...So I re-booted and then it worked!:popcorn:
Now to try the scanner...

---

### Post by theaskanison on 2010-02-13
Can someone tell me how to test the scanner? I try Scanlite and Xsane and neither one of them found the printer.
Thx

---

### Post by mkymonkey on 2010-02-13
I want to add that [Ballyboard]("http://ubuntuforums.org/member.php?u=966416") post helped out a lot with mine. After a quick install and restart everything worked like a charm. I'm running Ubuntu Karmic on an HP Mini.:KS

---

### Post by -jay- on 2010-03-09
does this also work for 64bit also ? im having a problem trying to install drivers

---

### Post by patslap on 2010-05-01
Me too - I'm using 10.04 64-bit and can;t install the two deb packages as theya re i386 architecture and won;t install. Any ideas anyone?

---

### Post by Heathicus on 2010-05-22
The printer works great thanks to Ballyboard's instructions.  But I can't get the scanner to work.  The scangearmp-common_1.40-1_i386 seemed to install just fine, but when I try to install the scangearmp-mp490series_1.40-1_i386 package, I get [COLOR=Red]**[COLOR=Black]"[/COLOR]Error: Dependency is not satisfiable: scangearmp-common (>= 1.40)[COLOR=Black]"[/COLOR]**[/COLOR].  

Any ideas?

EDIT: Nevermind.  I'm an idiot newbie that doesn't know how to install a package!  Or at least I didn't know.  Now I know.  And knowing is half the battle.

But, I still can't scan.  I tried XSane both through Gimp and directly from the Applications menu.  I also tried Simple Scan, but both say there are no scanners available.

EDIT 2: Neither XSane nor Simple Scan will find the scanner, but running "scangearmp" from the terminal, just as Ballyboard said, works just fine.

---

### Post by yo_johan on 2010-05-26
**MP490 Printer Lucid 64-bit**

> **patslap said:**
> Me too - I'm using 10.04 64-bit and can;t install the two deb packages as theya re i386 architecture and won;t install. Any ideas anyone?

{Try this at your own risk, otherwise wait for Canon to build the right driver}

I downloaded the i386 packages and installed them in my 10.04 64-bit Lucid install according to [this link]("http://ubuntuforums.org/showthread.php?t=1261666").

In a terminal type (of course change "pathtoyourdownload" to the directory your download is in):

```
cd /pathtoyourdownload/cnijfilter-mp490series-3.20-1-i386-deb/packages
```then

```
sudo dpkg -i --force-architecture cnijfilter-common_3.20-1_i386.deb
```and then

```
sudo dpkg -i --force-architecture cnijfilter-mp490series_3.20-1_i386.deb
```then I ran update manager (and got some replacement 64bit libraries), plugged in my mp490 and my printer works very well.

I don't know if this kind of forcing another architecture has any side-effects. But it works for me, no problems so far.

---

### Post by yo_johan on 2010-05-26
**MP490 Scanner**
I tried the method of my previous post on the scanner drivers too. But the scanner part of the MP490 did not work for me this way.
 
This worked for me:
The method of the "Canon Pixma Linux blog"
[http://mp610.blogspot.com/2008_04_01_archive.html](http://mp610.blogspot.com/2008_04_01_archive.html) : [FONT=Arial][Give  your scanner a new fresh SANE installation ...]("http://mp610.blogspot.com/2008/04/give-your-scanner-new-freshly-sane.html")[/FONT]

works very well on my 10.04 64-bit (as well as on my previous 9.10 32-bit).

So now the whole multifunction is working! Success with your try! :popcorn:

---

### Post by danlhall3 on 2010-06-22
installed driver cnijfilter-mp490series-3.20-1-i386-deb.tar.gz . Didn't work.Above .tar.gz does not seem to install files in driver. Have to do it manually Clicked "change" box next to "generic text printer" Waited until it asked me to install PPD file. Found it in /usr/share/ppd. Selected it and printer works great. Have not tried it yet on my 486 notebook. Driver says only for 386. Will try and let you know if it works.......This is my first post.....Let me know if it is ok.

---

### Post by danlhall3 on 2010-06-22
download cnijfilter-mp490series-3.20-1-i386-deb.tar.gz from canon.thailand. run install.sh. then go to printers in admin. click on mp490 properties. it will show generic text printer. click on change, then click on ppd. find it in /usr/share/ppd. click on it and open it. select "use new ppd", NOT copy old settings. printer should work fine. WARNING: the ppd file is not automatically applied to driver files. you MUST insert it manually as I said above.

---

### Post by callowschoolboy on 2010-06-25
I'm trying to get my Pixma MX340 to work on Ubuntu 10.04, I looked at those thai and new zealand sites and couldn't find anything that matched my model, same when I plugged the printer in and looked in the database of drivers.  Can anyone point me to the driver for a Canon Pixma MX340?

---

### Post by pdubin on 2010-11-07
Worked for me as well - THANK YOU!

---

### Post by xjamespx on 2011-01-11
The link that Bally posted isnt there anymore- but after a quick google search this is the one i used.

[http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html)

Download the link at the bottom.
Open the tar.gz and you'll see a folder named "packages"
Open that up and install those two packages. 
Go to SYSTEM>ADMIN>PRINTING
Then from the new window go >SERVER>NEW>PRINTER
From this window you should see CANNON MP490 and hit FORWARD 
The printer will now show up and you can test print a page to verify everything works fine.

Again, credit to BallyBoard for the lifesaving post. 
THANKS      =D>

---

### Post by FloydPink on 2011-01-18
> **xjamespx said:**
> The link that Bally posted isnt there anymore- but after a quick google search this is the one i used.

[http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html](http://support-nz.canon.co.nz/contents/NZ/EN/0100236302.html)

Download the link at the bottom.
Open the tar.gz and you'll see a folder named "packages"
Open that up and install those two packages. 
Go to SYSTEM>ADMIN>PRINTING
Then from the new window go >SERVER>NEW>PRINTER
From this window you should see CANNON MP490 and hit FORWARD 
The printer will now show up and you can test print a page to verify everything works fine.

Again, credit to BallyBoard for the lifesaving post. 
THANKS      =D>This really helped. Thank you...

---

### Post by Sims12345 on 2011-01-20
I'm running a 64bit version, are there any drivers that work for an x64 system?

Thanks

---

