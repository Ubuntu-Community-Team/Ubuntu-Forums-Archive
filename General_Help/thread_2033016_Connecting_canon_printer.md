---
title: "Connecting canon printer"
date: 2012-07-25
forum: General Help
---

### Post by Johnread on 2012-07-25
Has anyone experience of successfully connecting a Canon printer MG3150 to a computer running Ubuntu 11.10

---

### Post by daslinkard on 2012-07-28
first add a PPA:
  ```
sudo add-apt-repository ppa:michael-gruz/canon
``` ```
sudo apt-get update
```   Open software center:


  Search for: "Canon cnijfilter", in list; pick driver for your printer  series and "Canon Scangear", in list; pick driver for your scanner  series.


Both should install pretty quickly and afterwards just go to system settings/printers and add your printer.

---

### Post by Johnread on 2012-07-28
> **daslinkard said:**
> first add a PPA:
  ```
sudo add-apt-repository ppa:michael-gruz/canon
``` ```
sudo apt-get update
```   Open software center:


  Search for: "Canon cnijfilter", in list; pick driver for your printer  series and "Canon Scangear", in list; pick driver for your scanner  series.


Both should install pretty quickly and afterwards just go to system settings/printers and add your printer.
Thank you for your help.  All went well until I reached the search in the software centre when no match could be found for "Canon cnijfilter". Please have you any comments about this ?

---

### Post by Johnread on 2012-07-28
> **daslinkard said:**
> first add a PPA:
  ```
sudo add-apt-repository ppa:michael-gruz/canon
``` ```
sudo apt-get update
```   Open software center:


  Search for: "Canon cnijfilter", in list; pick driver for your printer  series and "Canon Scangear", in list; pick driver for your scanner  series.


Both should install pretty quickly and afterwards just go to system settings/printers and add your printer.
Please ignore my previous message, it was a simple matter of using capital letters for both initial letters.  But having got to the list of drivers and scanners, my printer was not listed.  I tried the common programme for iP series which did not work so then tried the driver and scanner driver for MG5100 series but these drivers were not recognized either.  Thus I am at a standstill.  Have you any other comments ?  Regards John Read

---

### Post by daslinkard on 2012-07-28
At this point in time what happens when you connect the printer up to the PC? What happens when you go to system settings and try to add the printer?

---

### Post by Johnread on 2012-07-30
> **daslinkard said:**
> At this point in time what happens when you connect the printer up to the PC? What happens when you go to system settings and try to add the printer?
I am sorry for the delay in responding to your last message.  The answer to your query is that when I connect the printer to the PC it emits some mechanical noise but no paper is drawn in.  When a file is sent to the printer the printer properties panel shows activity in processing the file but when that has been completed the printer does not respond. A check of the printer queue shows no file waiting to be printed.  I hope this will give you a lead to the solution for I am at a loss.   Regards John Read.

---

### Post by Johnread on 2012-10-11
Your last post certainly got the printer running and responding to the computer, for which I thank you.  However although the printer now prints in response to the computer the output is only in Black and White.  Even when I attempt to print in colour I only get a black and white output.  There is nothing wrong with the colour cartridge for in photo-copying mode colours are correctly reproduced.  Also I find in the printer properties the "printer features common" only allows black to be chosen there being no other options available.

I hope that you can offer a solution to this problem.  Regards John Read

---

### Post by pdc on 2012-10-11
If you can copy and paste this command

> sudo dpkg -l | grep cnijfilter*

into a terminal;

and copy and paste back what you get: *many find it easier to use the Edit copy from the top line menu in a terminal*..

you should surely have the Canon 3100 series driver installed;

for my MG3160 I get 

> ii  cnijfilter-common                             3.60-1                                  IJ Printer Driver for Linux.
ii  cnijfilter-mg3100series                       3.60-1                                  IJ Printer Driver for Linux.


......I can print B&W and colour..

---

