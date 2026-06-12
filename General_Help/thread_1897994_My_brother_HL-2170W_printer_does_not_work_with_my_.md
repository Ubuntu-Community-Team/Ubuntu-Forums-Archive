---
title: "My brother HL-2170W printer does not work with my ubuntu computer"
date: 2011-12-20
forum: General Help
---

### Post by tc101 on 2011-12-20
My brother HL-2170W printer does not work with my ubuntu 10.04 computer.  It works fine with my win 7 computer so the problem is not the printer. 

The computer recognizes the printer, it just doesn't print.  Print jobs just sit in the print que and say processing.

---

### Post by kurt18947 on 2011-12-20
Hi

I suspect you're printer is newer and is not in the foomatic database.  Here are the Brother Linux drivers:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)
You'll want to look through the "before you install" section.  It looks worse than it is because both .rpm & .deb stuff are in the same file.  I printed the whole thing out (on another printer) and crossed out what doesn't apply.  If you're running 32 bit Ubuntu, you can ignore the command line stuff & just right-click the downloaded .deb file then install via Software Center or Gdebi (my preference).  64 bit OSs require the use of the command line.  Here's a hint/cheat for using the command line to install.  I cd to the directory where the downloaded .deb file is.  Type 'dir'.  You'll get a listing of the files in that directory including the brother .deb file.  You can then type 'dpkg  -i  --force-all (or copy paste) then select the .deb file name and copy/paste that.  Copy/paste eliminates typing errors.  If you don't know this,   Linux directories & file names are case sensitive unlike Windows.  If your file is in your 'Downloads' directory and you type 'cd downloads', you'll get a 'directory not found' message.  Type 'cd Downloads' and it'll work.

Try your new printer out on a mult-page document.  If it's slow after the first page, you can look for a CUPS driver that works for your machine vs. the brscript driver which is default.  I have an older Brother MFD which is real slow on 2nd and subsequent pages.  When using the CUPS driver it prints at its rated speed.  If the speed is fine using the brscript driver, use that.  Good luck with your new machine,  Brother's Linux support is better than most manufacturers.

---

### Post by tc101 on 2011-12-20
How do I know if I have 32 bit or 64 bit ubuntu?

I got the printer in 2009, before 10.04 came out.  Does that effect what you told me?

---

### Post by kurt18947 on 2011-12-21
> **tc101 said:**
> How do I know if I have 32 bit or 64 bit ubuntu?

I got the printer in 2009, before 10.04 came out.  Does that effect what you told me?

To tell whether 32 or 64 bit, open a terminal and type 'uname -a'.  If you see something like this: ```
x86_64 x86_64 x86_64 GNU/Linux
```you have 64 bit.  I think 32 bit would say something about 'i386' but I'm not sure and don't have a 32 bit install to check.

I'm sort of surprised your machine doesn't 'just work'.  Here's a link to Brother's drivers for your machine:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)

What connection are you using?  I've had Brother printers install a USB connection when it was actually a network connection.  I haven't used Gnome 2 for a while so I'm working from memory.  System -> Administration -> Printing.  Right-click the printer's icon and left-click 'properties'.  Device URI should show either 'USB://.........' for a USB connection or some network address.  I did have problems with a network connected machine like you're having and changed two things that improved reliability for me.

[LIST=1]
[*]Assign a static I.P. to the printer
[*]In the 'Device URI' window I put this "socket://xxx.xxx.xxx.xxx" where x=i.p. address.
[/LIST]
I would look at the connection before installing Brother's drivers.  If you do decide to install Brother's drivers, I'd un-install what you have now first so whatever is causing problems now doesn't carry over.

---

### Post by neoookami on 2011-12-21
Ubuntu's version of CUPS autodetects the printer fine, but it doesn't seem to work well for printing the way it does. Change the location to the printer's IP address and it should work fine. (This is what I had to do with mine. In general a great printer~)

---

### Post by tc101 on 2011-12-21
The printer works for some things, like simple text from gedit, but if I try to print from open office or google maps it hangs.

I think I have 32 bit.  Terminal shows

tom@tom-desktop:~$ uname -a
Linux tom-desktop 2.6.32-37-generic-pae #81-Ubuntu SMP Fri Dec 2 22:24:22 UTC 2011 i686 GNU/Linux

Device URI shows

usb://Brother/HL-2170W%20series

>    1. Assign a static I.P. to the printer
   2. In the 'Device URI' window I put this "socket://xxx.xxx.xxx.xxx" where x=i.p. address.


Do you still think I should try this?


> I would look at the connection before installing Brother's drivers. If you do decide to install Brother's drivers, I'd un-install what you have now first so whatever is causing problems now doesn't carry over.


I spent 30 minutes on the brother site and I am still not sure which drivers to install.

---

### Post by kurt18947 on 2011-12-22
> **tc101 said:**
> The printer works for some things, like simple text from gedit, but if I try to print from open office or google maps it hangs.

I think I have 32 bit.  Terminal shows

tom@tom-desktop:~$ uname -a
Linux tom-desktop 2.6.32-37-generic-pae #81-Ubuntu SMP Fri Dec 2 22:24:22 UTC 2011 i686 GNU/Linux

[COLOR=Blue]You do have a 32 bit system.  The PAE kernel is installed when you have more RAM than a 32 bit system can normally use, e.g. more than 3 GB.[/COLOR]

Device URI shows

usb://Brother/HL-2170W%20series



Do you still think I should try this?

[COLOR=Blue]I presume your printer is connected to your PC via a USB cable.  If so, I'd guess your URI is correct.  My issue came from the printer info showing a USB connection installed when there was no USB cable present, only a wireless network connection.[/COLOR] [COLOR=Blue]The fact that you can print *anything* would seem to indicate that you have the correct type connection.  I've not run into your situation where you can print simple files but not others.  It's almost like your printer thinks it doesn't have enough onboard RAM to print more complex graphics or something.[/COLOR]




I spent 30 minutes on the brother site and I am still not sure which drivers to install.

[COLOR=Blue]This link should let you download the lpr driver:[/COLOR]
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb&lang=English_lpr](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/brhl2170wlpr-2.0.2-1.i386.deb&lang=English_lpr)

[COLOR=Blue]This link should let you download the CUPSwrapper driver:
[COLOR=Black]http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb&lang=English_gpl

[COLOR=Blue]Installing CUPSwrapper requires installing the lpr driver first as shown in the CUPSwrapper installation directions:

[COLOR=Black]http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html
[/COLOR]

[COLOR=Black][COLOR=Blue]Step 2 appears to only apply to 64 bit Debian/Ubuntu systems[/COLOR] [COLOR=Blue]so I don't think step 2 applies to you.  If you want to avoid the terminal commands posted, you could download both .deb files then use Gdebi to install them.  If memory serves, Gdebi is installed by default in 10.04.  I would remove the existing printer installation before installing the .deb packages from Brother.  If you do choose to use the terminal commands, don't put the parentheses around the file name, just type the file name.

This may be relevant for you.  If the directory already exists, you'll get a message to that effect.  From the Brother FAQs
[/COLOR][/COLOR][/COLOR][/COLOR][/COLOR]```
**I'm using Ubuntu 8.04 or greater.  I have installed the drivers, but I am still unable to print.** 


Ubuntu 8.04 or greater does not have /usr/share/cups/model directory where our driver create a ppd file.
Please follow the instruction below when the installation failed with the message.
(Superuse authorization will be required)

1. Uninstall the cupswrapper driver.
Command : dpkg  -P  (driver name)

2. Create /usr/share/cups/model directory
Command : mkdir  /usr/share/cups/model

3. Install the cupswrapper driver
Command : dpkg  -i  --force-all (driver file name)

```
[COLOR=Blue]Let us know how you get along, please.

EDIT: I'm not sure why some address don't show up as clickable links. You should be able to copy and paste the addresses into a browser address bar.


[/COLOR]

---

### Post by xyzzyman on 2011-12-22
I have the same printer (Which I've loved by the way) but it's been boxed from moving. I've been meaning to unpack it so this is a good reason. The printer supports PCL6 if it comes down to it. I haven't had to go buy toner yet so who knows how much I'll really love it down the road.

---

### Post by tc101 on 2011-12-24
I did the two steps suggested below,  rebooted, and nothing has changed.   What next?

> This link should let you download the lpr driver:
[http://www.brother.com/cgi-bin/agree...ng=English_lpr](http://www.brother.com/cgi-bin/agree...ng=English_lpr)

This link should let you download the CUPSwrapper driver:
[http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperHL2170W-2.0.2-1.i386.deb&lang=English_gpl)


---

### Post by tc101 on 2011-12-24
I tried to print a PDF doc.  It hung.  I looked in printer Queue and and it said processing.  5 minutes later it printed.

---

### Post by tc101 on 2011-12-24
I see now that it is working, just very slowly.  I tried to print a map from google maps.  I just let it sit to see what would happen.  It finally printed about a half hour later.

Any ideas how to fix this?  The same printer prints these things almost instantaneously on a windows machine.

---

### Post by kurt18947 on 2011-12-25
> **tc101 said:**
> I see now that it is working, just very slowly.  I tried to print a map from google maps.  I just let it sit to see what would happen.  It finally printed about a half hour later.

Any ideas how to fix this?  The same printer prints these things almost instantaneously on a windows machine.

I'm not sure if my fix will work for you or not.  I had something similar but I was getting about 1.5 -2 pages/min., not 30 min./page.  I found a CUPS package in Synaptic that included my model printer. The package name is "brother-cups-wrapper-laser".  I installed that then changed the printer driver being used from Brscript3 to "brother(model)for CUPS. I looked and the package I used includes support for HL2070N but not 2170W.  I assume you installed the CUPSwrapper driver but I had to install the above mentioned package in addition in order to get print speed comparable to Windows.  I don't know if installing a package that includes support for somewhat similar models would help you or not.

You might also try emailing Brother.  Brother does not provide phone support for Linux but they do provide email support.  Here's a link that includes an email button
[http://www.brother-usa.com/askus/faqs.aspx?Topic=hardware&Model=1265&ProductGroup=1&R3ModelID=hl2170W#.Tvaw4cBxOJM](http://www.brother-usa.com/askus/faqs.aspx?Topic=hardware&Model=1265&ProductGroup=1&R3ModelID=hl2170W#.Tvaw4cBxOJM).  You may have to go through a registration process then fill out a form.  I did this and it took about a week I think.  Brother Japan provides Linux support, the people in Tennessee do not help with Linux.  I'm sorry that getting your printer to work has been such a trial for you.

---

### Post by tc101 on 2011-12-25
Thanks for your help Kurt.  I may just buy another printer.

---

### Post by xyzzyman on 2011-12-26
Just unboxed mine. Not sure if it's because it's been sitting in the cold but the smell of ozone after powering it up brings back old memories. :) Hopefully have something for you in a bit. If I can't get it going easily with the regular drivers I'll see about getting it set up with regular PCL6 which is why it's included so incompatabilities aren't a worry.

EDIT: I read it as 11.04 not 10.04. At the very least this does work with 11.10 automatically. Just printed a picture heavy PDF and a google maps from chrome. USB then did it over the network. I'll throw 10.04 in a virtual machine and see what I can do.

---

### Post by xyzzyman on 2011-12-26
[https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/570027](https://bugs.launchpad.net/ubuntu/+source/foomatic-db/+bug/570027)

The fix in it was correct, the printer works best in PCL-5e mode.

Can you run a:

```
dpkg -s foomatic-db
```

And tell us what version it reports? It's probably 20100216-0ubuntu3 from february 2010, and it wasn't fixed until august 2010 and hasn't been backported to the LTS 10.04 that you're using.

It should be pretty safe to apply the Maveric 10.10 file to your system. In a command prompt do:

```

wget http://launchpadlibrarian.net/57144104/foomatic-db_20100915-0ubuntu4_all.deb
sudo dpkg -i foomatic-db_20100915-0ubuntu4_all.deb

```

Then delete the printer and let it redetect.

---

### Post by goodbye-windows(tm) on 2011-12-31
I have the same Brother printer. I never downloaded a driver and it works first time, every time.

Mine is networked, so it runs wireless.

I have an old pentium 4 desktop I built back in 2006, 1.5 GB ram. I run xubuntu.

For me to install the printer, I simply go to Applications Munu>System>Printing. Click on the large green 'plus' symbol and select 'networked printer'. The Brother HL-2170W printer will be listed there, click on the 'forward' arrow, and you're done. The computer connects to the printer using the wireless and after a few seconds the Brother Icon appears with a green check mark, showing it is installed.

I did use an old wndows laptop with an ethernet cable in order to set the printer up on the router, but after that, it's very easy to install the printer to work with xubuntu.

I am presently looking to install the smae printer on my daughters new computer (64 bit Dell 15r laptop running unity....but having no success so far. Sure wish she was running xubuntu::>

Regards,

Art

---

