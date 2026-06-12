---
title: "Karmic 9.10 and printing to XP shared printer"
date: 2010-02-17
forum: General Help
---

### Post by chrisbraddock on 2010-02-17
Need help to troubleshoot printing please!

I have a brand new **Canon MF4350d** printer/copier/fax/scanner installed and shared on XP that I can't get working on Ubuntu! 

XP prints test pages fine.  Ubuntu sees the XP shared printer, it sends print jobs, and **the XP machine even receives the print jobs** (I can see them "spooling" in the XP print manager) but then nothing happens.  The job leaves Ubuntu showing 150k but then shows 50 bytes when received in XP before disappearing from the queue.

How I got to where I am...

There was no native driver in Ubuntu for the printer, so I downloaded [Canon linux drivers source]("http://support-sg.canon-asia.com/P/search?model=imageCLASS+MF4380dn%2FMF4370dn%2FMF4350d%2FMF4320d&menu=download&filter=0&tagname=ca_os&ca_os=Linux") and compiled (including make install) based on some other threads I've found such as [this one]("http://ubuntuforums.org/showthread.php?t=1051284&page=2").

Compiling left me with PPD files that seem to be specific to the MF4350, although their names show MF4350**z** not MF4350**d**.  I'm not sure why there were three different files with slightly different names (CNCUPSMF4350Z**J**.ppd, CNCUPSMF4350Z**K**.ppd, and CNCUPSMF4350Z**S**.ppd).

I added the printer manually using the Ubuntu printer browser setup (Samba) and selected the .PPD files manually.  I've tried all three different .PPD files to no avail.

I've toggled bi-directional comm. and tried different print drivers on XP.  Nothing's worked yet.

Please help!

---

### Post by chrisbraddock on 2010-02-17
Also updating to the latest printer firmware hasn't helped.

Anyone?  General Ubuntu printing troubleshooting techniques?  There's got to be logs, debugging info, etc. I can get at?

---

### Post by chrisbraddock on 2010-02-20
Yeah!  Got this working.

First I took the network share out of the equation and plugged the printer right in to Ubuntu.  It was NOT recognized upon USB plugin nor when searching for printers using Ubuntu printer UI.

So, I figured the drivers I compiled might not be valid as I had thought.  I tried recompiling and was now seeing an error.  Time for plan B.

I downloaded the .rpm drivers from the link above and used Alien to convert them to .debs.  **These .debs installed** (the official .debs provided by Canon had earlier given me dependency issues I could not resolve).

Now I was able to print locally and the next step was to test the XP Samba share.  Bingo.

Hope this helps someone else.

---

### Post by ridgeland on 2010-03-03
Hi chrisbraddock
Thanks for sharing.
I bought my Mom a MF4350d to use with Ubuntu 9.04.  I had a hard time getting it to print.  With a 64-bit install I never got it to work.  I installed Ubuntu 9.04 32 bit and it works fine as a printer now.
But Xsane always says No Devices Available - no scanner.
Do you have it working as a scanner?  Any hints?
No one here uses or cares about the fax features.

---

### Post by chrisbraddock on 2010-03-04
Hmm, sorry.  I have it hooked up as a shared printer from XP (not direct USB connection to Ubuntu) so I don't think there is any scanning capability that way. :)

If I get a chance I will give scanning a shot with direct connection and post back results.

---

### Post by ridgeland on 2010-03-04
I've got some leads I'm chasing.  No time to toy with it now.
I'll try ideas from:
[https://answers.launchpad.net/ubuntu/+question/79913](https://answers.launchpad.net/ubuntu/+question/79913)
Basically it's get some written but not released sane drivers, compile sane and xsane should see the scanner.

I'll post findings.

---

### Post by salsavirdi on 2010-03-09
Hi,
I just got a Canon imageclass MF4320D. I found a file on canon's europe site that gives instructions and drivers for linux. It includes a cups package and a UFRII package. In the list of supported printers it mentions the i-SENSYS MF4320D, and I'm not sure if there's any difference between the two names.

[http://de.software.canon-europe.com/software/0037431.asp?model=](http://de.software.canon-europe.com/software/0037431.asp?model=)

I haven't tried it myself but will let you guys know if it works.

---

### Post by oldefoxx on 2010-03-09
From awhile back, I learned that scanner support for Linux has been slow coming.  Most of what can be found seems to relate to older models of scanners that have largely gone away.  Venders do not seem inclined to create drivers specific to Linux, and there is no real standard like ndis to help.  What does help some times is recognizing that scanners can run in families, and what works for a scanner in the same family may work with yours.

Other than that, my scanner which is USB connected, shows up as a device in Ubuntu, and I can enable it in VirtualBox for a client, and if that client has the right software installed, it can then make use of the scanner.  That works.  This setup can also solve some other connectivity and interoperability issues.

---

### Post by ridgeland on 2010-03-11
I've got the printer and scanner working fine.  Since this thread's title is not the place for the details I started a new thread
Canon MF4350d - Printer Scanner setup  [CLICK HERE]("http://ubuntuforums.org/showthread.php?t=1427330")
There I list all the steps.  I liked Mom's MF4350d enough that I bought a second one for my wife and me.

---

