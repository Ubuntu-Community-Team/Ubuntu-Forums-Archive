---
title: "Huge printing delay"
date: 2012-09-29
forum: General Help
---

### Post by RobertoHanus on 2012-09-29
**Huge printing delay** 
I have a HP-430 Notebook PC. I have intalled Ubuntu 12.04. 
 
I have a Brother MFC-J6710DW printer working using CUPS.
 
When I try to print a sigle page the printer prints inmediately. But when I increase the number of pages to print it delays more to start. When I send a job, for example, of 50 pages it delays about 5 minutes to start to print the first page. When I send a job, for ejample, of 100 pages it takes 10 minutes to start printing the first page.
 
This behavior is the same if I print using Gimp to print several copys of a image or when I try to print several copies of a web page Using Firefox. 
 
What I see is that the problem is independent of the program used to print or if the job is to print a PDF file or an image.
 
Please Help. This problem is worring me a lot.
 
 
**Re: Huge printing delay** 
tell us which printer driver you have installed
 
If you copy and paste this command
 
Quote:
sudo dpkg -l | grep Brother 
.....*the vertical line is the pipe command, using Shift\ on the keyboard*..
 
into a terminal; hit the enter key and copy and paste the result back
 
.........from here.........
 
[http://welcome.solutions.brother.com...ml#MFC-J6710DW]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J6710DW")
 
........this is the link to the Brother linux site
 
__________________________________________________ _________
 
what does the CUPS page show?
 
if you paste this 
 
[http://localhost:631/printers/](http://localhost:631/printers/)
 
into a browser window............
 
 
**Re: Huge printing delay** 
1) tell us which printer driver you have installed
 
ii brscan4 0.4.1-1 Brother Scanner Driver
ii mfcj6710dwcupswrapper 1.1.1-1 Brother CUPS Inkjet Printer Definitions
ii mfcj6710dwlpr 1.1.1-1 Brother lpr Inkjet Printer Definitions
ii printer-driver-ptouch 1.3-3 printer driver Brother P-touch label printers
 
 
2) what does the CUPS page show?
 
&#9660; Queue Name &#9660; Description Location Make and Model Status
MFCJ6710DW MFCJ6710DW Brother Brother MFC-J6710DW CUPS Idle
 
Please help. Thanks.

---

### Post by daslinkard on 2012-09-30
In looking at the [reviews]("http://reviews.brother-usa.com/6607/mfcj6710dw/reviews.htm?page=5&sort=reviewTextLength&dir=asc") for the printer....I don't think it is anything with Ubuntu as much as it is an issue with the printer.

---

### Post by pdc on 2012-10-01
> he printer does a very good job.
***However, some jobs take just forever***.

........as daslinkard so aptly points out.........

[http://reviews.brother-usa.com/6607/mfcj6710dw/reviews.htm?page=5&sort=reviewTextLength&dir=asc](http://reviews.brother-usa.com/6607/mfcj6710dw/reviews.htm?page=5&sort=reviewTextLength&dir=asc)

---

### Post by daslinkard on 2012-10-01
> **pdc said:**
> ........as daslinkard so aptly points out.........

[http://reviews.brother-usa.com/6607/mfcj6710dw/reviews.htm?page=5&sort=reviewTextLength&dir=asc](http://reviews.brother-usa.com/6607/mfcj6710dw/reviews.htm?page=5&sort=reviewTextLength&dir=asc)

This is some good info to know about this printer as I have a lot of customers come to me asking about the capabilities that it has to offer.  If it seriously takes 5 minutes to print a larger job, I might look like an idiot for giving it high reviews.  Just saying....that or I might just look like an idiot anyway? ;)

---

