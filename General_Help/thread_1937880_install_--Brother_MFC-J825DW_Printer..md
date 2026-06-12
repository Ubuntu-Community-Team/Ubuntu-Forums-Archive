---
title: "install --Brother MFC-J825DW Printer."
date: 2012-03-08
forum: General Help
---

### Post by 4042966262 on 2012-03-08
**cant seem to find driver for Brother MFC-J825DW **
im lost. in[http://localhost:631/](http://localhost:631/) (CUPS) i can add printer. when printer is on i see it.
under find printers it says  Brother MFC-J825DW (Brother MFC-J825DW)
select it..next
Brother_MFC-J825DW

Name: [IMG]chrome://informenter/skin/marker.png[/IMG]
(May contain any printable characters except "/", "#", and space)   Description: [IMG]chrome://informenter/skin/marker.png[/IMG]
(Human-readable description such as "HP LaserJet with Duplexer")   Location: [IMG]chrome://informenter/skin/marker.png[/IMG]
(Human-readable location such as "Lab 1")   Connection: usb://Brother/MFC-J825DW?serial=BROK1F229475   Sharing:  Share This Printer   


now i see 

**Add Printer**

            Name: Brother_MFC-J825DW   Description: Brother MFC-J825DW   Location: 
  Connection: usb://Brother/MFC-J825DW?serial=BROK1F229475   Sharing:  Do Not Share This Printer   Make: Brother    Model:     
  Or Provide a PPD File:    

hmm. now what? looked for a PPD file.. was redirected to long list of printers, found mine. and what do i see? nothing. just names of OS.

**update**~UPDATE~[B]UPDATE
[/B]found the Windows CD and looking inside for a PDD file.. looks like everything is .exe though i found a folder named ''ppdownload''

---

### Post by wallaroo on 2012-03-08
You'll probably have better luck installing the 'deb' packaged drivers from here ...
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J825DW](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-J825DW)

(don't forget to follow the install instructions - very important).

---

### Post by computerfreak4284 on 2012-12-27
I installed the drivers but it will not work as its a network printer. I attempted to re-add the printer as network printer and it found the driver but when I tried to print I got this message. How do I fix it?

---

### Post by computerfreak4284 on 2012-12-28
Got it to work and going to attempt to setup the scanner this weekend and makes sure it works.

---

### Post by robertmbowes on 2013-03-06
How did you get it to work, please?

---

### Post by pdc on 2013-03-07
Brother provide guidance and instructions:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

if you go to section 5b ..

and threads such as this

[http://ubuntuforums.org/showthread.php?t=1921644](http://ubuntuforums.org/showthread.php?t=1921644)

---

### Post by kurt18947 on 2013-03-07
> **robertmbowes said:**
> How did you get it to work, please?

Are you somewhat comfortable with command line usage?  If so, you can take a look at this:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

The trickiest part for me was understanding how to download the script.  Once I got that, it was a matter of one line:

```
sudo bash install.sh

```

I am then prompted for model e.g. MFC-j825DW then some 'do you agree' prompts.  Then do I want to specify a URI (connection, e.g. USB, socket, etc.).  Once I figured it out I can install a Brother printer in less than 2 minutes.  There is no equivalent for scanner function that I'm aware of.

---

