---
title: "Help with Networked Brother MFC-7440N printer"
date: 2010-10-26
forum: General Help
---

### Post by joshcrack on 2010-10-26
finally i've solved it after a little more of searching around... and got my test page printed... I am going to write down the step for future reference.

Assuming You have Ubuntu 10.10 32bit... and MFC-7440N connected on your network....

First go to System > Administration > Printing

[IMG]http://d.imagehost.org/0925/Menu_002.png[/IMG]

Then click Add

[IMG]http://d.imagehost.org/0568/Selection_009.png[/IMG]

Then drop down Network Printer and Wait ... Your printer should show up "Brother MFC-7440N". If it shows up then well and good... 

[IMG]http://d.imagehost.org/0592/Selection_004.png[/IMG]



Lets start with the 1st step.

Download the LPR driver "deb format" for MFC-7440N 
&
Download cupswrapper driver "deb format" for MFC-7440N from

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7440N](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-7440N)

First install the LPR driver... It should say "brmfc7440nlpr-2.0.2-1.i386.deb". In ubuntu 10.10 you can install it by just double clicking it.

Now follow the following steps to install your cupswrapper driver.
Assuming it is saved to your Downloads folder... Go to terminal

First make a directory "model" in usr/share/cups

```
sudo mkdir /usr/share/cups/model
```

Next navigate to your folder with the cupswrapper driver

```
cd Downloads
```

Now execute the file

```
sudo dpkg -i --force-architecture cupswrapperMFC7440N-2.0.2-1.i386.deb
```

After it is done ```
exit
```

Now go to System > Administration > Printing

Then click Add

Then drop down Network Printer and Wait ... Your printer should show up "Brother MFC-7440N".

Click on it once and wait. When its selected click "Forward"

It should say searching for drivers

[IMG]http://d.imagehost.org/0749/Selection_005.png[/IMG]

now choose "Provide PPD file"

[IMG]http://b.imagehost.org/0627/New_Printer_010.png[/IMG]

then navigate to usr/share/cups/model
You should see the "MFC7440N.ppd" file in there.
Select and click "Open"

[IMG]http://d.imagehost.org/0240/Select_A_File_011.png[/IMG]

Then Click "Forward"

Then just watch and dont forget to :guitar: on. Print a test page to verify.... :)

Enjoy

---

### Post by carl.davis on 2010-10-26
Hello,

If your printer has an IP, try adding it by clicking "AppSocket/HP JetDirect" and then type the IP in rather than the printers discovered via a network scan.

---

### Post by joshcrack on 2010-10-27
thank you for the reply... 

when I enter the ip address... it still says searching for drivers and takes me to the screen asking me what driver to use; but my printer is not in the list.

---

### Post by joshcrack on 2010-10-27
Check the first post

---

### Post by fdmille on 2010-12-04
Did not work for me until I typed in the IP address of the printer in the Host: field under Select Device > Network Printer > AppSocket/HP JetDirect

Now it works!

---

### Post by joshcrack on 2010-12-15
glad that it worked for you.

---

### Post by jfbooth on 2011-02-04
Thank you everyone for this.  From this thread, I got my mfc-7440n working again.  I had to use the IP address though .. but it prints and scans again.  Thank you.

---

### Post by Linux_Inside on 2011-08-13
you can also use nmap and look at the result of the OS detection...
maybe you can see :
[FONT=Courier New][SIZE=1]
[/SIZE][/FONT][INDENT][FONT=Courier New][SIZE=1]OS details: HP LaserJet (1020-, 2010-, 2600-, 2800-, 3050-, or 3390-series) or Brother (HL-5250DN, MFC-7840N, or MFC-8860DN) printer[/SIZE][/FONT]
[/INDENT]MFC-8860DN works perfectly well for me !...

---

### Post by .35Whelen on 2011-11-18
Josh,
I spent an hour playing with this printer's drivers before I came upon this well done, quick tut.
 Thanks! I am up and running.

---

### Post by jimw on 2012-01-01
I've just spent three fruitless hours trying to install my Brother mfc7440n on my Ubuntu Lynx.  I first installed the drivers from the Brother help centre, and found the printer,  At that point, the forward button had it search for drivers.  After a long time, it came up with a list of drivers, but 7440 wasn't there; they recommended 7226, which I tried, but it wouldnt even print a test page.

It's clear I missed out something, but I have no idea what.  Can anyone help me out?

JimW

---

### Post by jfbooth on 2012-01-16
and I can't get past SEARCHING FOR DRIVERS.  [http://localhost:631](http://localhost:631) 'finds' the printer but then:

Add Printer Brother_MFC-7440N Error

Unable to get list of printer drivers:

---

