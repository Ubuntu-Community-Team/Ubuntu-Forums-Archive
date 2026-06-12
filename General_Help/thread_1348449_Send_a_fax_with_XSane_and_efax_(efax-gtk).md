---
title: "Send a fax with XSane and efax (efax-gtk)"
date: 2009-12-07
forum: General Help
---

### Post by Seb71 on 2009-12-07
It is possible to send a fax using XSane and efax (efax-gtk)?
If the answer is yes, how should XSane be setup to do that? With the setup from the attached screenshot, it does not work (the scaned document it is not sent by fax). 


My setup and configuration:
External fax-modem (US Robotics on one serial port). 
Multifunctional printer/scaner: HP LaserJet M1120 MFP
Ubuntu 8.04 LTS (Hardy Heron)
XSane 0.995
efax-gtk 3.0.16
efax 0.9a

I can scan documents with XSane.
I can send faxes with efax (efax-gtk) from OpenOffice.org Writer (using Print command and selecting Fax as a printer).

---

### Post by Seb71 on 2009-12-08
up

---

### Post by Seb71 on 2009-12-10
Do I have other options? If necessary, I can use other software combination in place of XSane and efax (efax-gtk). Is there a combination that works?

I want to scan a document with HP LaserJet M1120 MFP and then send it by fax using my external fax modem.

---

### Post by Seb71 on 2009-12-11
up

---

### Post by derrick81787 on 2009-12-11
I've never tried to send a fax, but if you can send it from Open Office by printing to the fax modem, you should be able to do the same thing from XSane.  Have you tried scanning an image and then printing to the fax modem?

I understand that this might not be ideal, but it should at least work.  Someone who has actually sent a fax from Ubuntu before might be able to help you a little more.

---

### Post by Seb71 on 2009-12-11
Thank you for your reply.

> **derrick81787 said:**
> Have you tried scanning an image and then printing to the fax modem?

When needed, I insert the scanned document (as a picture/image) into an OpenOffice.org Writer document (.odt) and then print it to the fax modem. As you say, it works like this, but it is less than ideal.

From the XSane interface it looks that it should be able to directly send by fax modem a scanned document. That would be my preferred way of sending by fax modem a scanned document.

---

### Post by Seb71 on 2009-12-17
up

---

### Post by geoffatmk on 2010-05-01
Like you I am trying to get this to work.

I can issue a fax through xsane and it ends up in a queue in ~/faxproject the default directory for xsane faxes.  How to move it from there to the fax (mine is a Brother all in one) I have as yet no idea.

I will keep trying and post here if I find a solution.

---

### Post by mickza on 2010-07-02
Got it working on Fedora 10 - no reason why it shouldn't work on Ubuntu, in the end it's easy (after 2 hours of trawling man pages & the net).

I am assuming the user has reached the stage where, using the xsane save option, they can scan & save a file in postscript format and then use efax-gtk to select and send it.


**In efax-gtk:**

Set "Fax Entry Method" to Socket


**In xsane:** 

Preferences > Setup > Fax

Select the "efax" default and insert **lpr -P fax** in the Command option


**In printer admin:**

create a new printer:

*name:* **fax** (important name agrees with "lpr -P **fax**" in xsane)
*queue:* socket://localhost:9900 (this the efax-gtk default)
*printer type:* generic > postscript

Print test page - if you set it up correctly a efax-gtk window will open asking for the Tel number and whether you want to queue or send now.

The xsane "fax" option should provide the same results.

Enjoy :)

---

