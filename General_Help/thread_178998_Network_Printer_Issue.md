---
title: "Network Printer Issue"
date: 2006-05-18
forum: General Help
---

### Post by omjaroo on 2006-05-18
Hi,

I have a Brother hl2070n printer. I downloaded the linux deb driver for a cups printer package from brother. I believe I have the printer driver properly installed and the print manager says the printer is "ready". However I can not print a test page (or anything else for that matter). I think the problem is the URI address I have put in the print properties box which is:

[http://localhost:631](http://localhost:631)

When I try to print properties tells me the printer is  paused/stopped/no such printer, etc.

Your help is very much appreciated!

Thanks

Jared

---

### Post by bigken on 2006-05-19
Check this out it might help [http://www.ubuntuforums.org/showthread.php?t=105703;)]("http://www.ubuntuforums.org/showthread.php?t=105703")

---

### Post by omjaroo on 2006-05-19
> **bigken]Check this out it might help [URL="http://www.ubuntuforums.org/showthread.php?t=105703"]http://www.ubuntuforums.org/showthread.php?t=105703 said:**
> 

Hi,
Thanks for the response. I revisited that link. It was the same one I used to load the drivers in the first place. As a result I was able to successfully (I think) to put in the correct printer IP. Which was 192.168.1.1. That is I don't get anymore  error messages. The printer box says it is printing to ipp://192.169.1.1 on port 691. Everything looks as if it should be printing but it is not. 

I tried the printer from another windows computer on the network and it worked fine. I accessed the printer control panel from my firefox browser at 192.168.1.103, logged in and was able to print a test page. So it appears the printer and the network settings are all correct. But for some reason when I try to print a test page from the gnome printer properties box or from any program on my ubuntu machine I get a message saying the print job has been sent and everything looks good. It just doesn't print. 

I have a feeling this is something very simple. Someone suggested going into the html based cups printer control panel but I can find no such thing. I also downloaded and tried to install a cups printer utility but that didn't work for I don't know what reason. 

Your help is very much appreciated

Thanks

Jared

---

### Post by bigken on 2006-05-20
Ok in the printer settings try this;) 
set up as UNIX printer (lpd)
Description: (name of printer)
host 192.168.1.1   (check lcd for static address)
queue (look on printer lcd  display for name )

hope this helps ;)

This is what my says in [http://localhost:631/](http://localhost:631/)
  Description: MFC3820CN
 Location: 
 Make and Model: Brother MFC-3820CN CUPS v1.1
 Printer State: idle, accepting jobs, published. 
 Device URI: lpd://192.168.1.9/BRN_463041

---

### Post by omjaroo on 2006-05-20
Thanks,
Tryed it all. 
I did finally get to the cups manager at local host: 631. No help though.
Going to do a clean install of ubuntu and try again...
Thanks again.

---

### Post by bigken on 2006-05-20
Are you sure that the printer has a static IP address and not set through dhcp

---

### Post by omjaroo on 2006-05-21
Hi,
OK heres the report. Somewhere along the line someone suggested I get the printer product info from when I bought the printer. Thank goodness I kept the manual. I was able to access the printer itself in a browser. I was able to print a test page, so I know the printer was hooked to the network and working. I printed a "print setting report" and saw the printer IP address as 192.168.1.103. But when I tried this in CUPS for an IP address in the properties panel, it didn't work. 

After doing a clean install of ubuntu, which turned out to be a good idea as it cleared up a bunch of other weird happenings, I reloaded the printer drivers very carefully. It was a success. I hooked the printer up locally with a USB cable and it worked fine. 

After a while I remembered someones suggestion to set the printer up as a lpd printer. So after trying all kinds of numbers in the "host" line, I remembered the IP address for the printer and tryed that. Bingo, it worked. 

So I now have a working network printer. Estimated time for installation: 9 hours. Ouch! 

But I am grateful, non-the-less. I have learned a tremendous ammount about linux in a very short time. Trial by fire, I guess it's called. My installation is cleaner and functions fairly well. I have a number of other programs to install and learn but I anticipate I will be able to live and work 100% OS10.4 and XP free! 

Thanks again for all your help and support. 

Jared

---

### Post by bigken on 2006-05-22
Pleased you got it sorted :D when 1st tried to setup mine through a network I
gave up until bobsongs came up with the solution didnt have a printer in linux 
for three months lol

---

