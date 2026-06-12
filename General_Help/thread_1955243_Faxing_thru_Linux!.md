---
title: "Faxing thru Linux!"
date: 2012-04-09
forum: General Help
---

### Post by Overtipper on 2012-04-09
Hey all!!

   I have one of those "Questions that might have an obvious answer, but I'm dumber than a mud fence today"... :)

  I have a HP G72 laptop, and a HP Deskjet 2050 AIO printer/Scan/Copier.  I have wireless here at the house, and I was thinking that it would be a great idea to be able to use my combo to fax documents.  My new job requires me to sign my life away on a regular basis, and (legally) they cannot accept an email "signature" <sigh!>

  I set my laptop up for dual boot (7/Ubuntu 11.10), and you can probably guess which one I use more... :)  Being relatively new to Linux.... I haven't got a clue on where to start to see if I can do this or not.  Any suggestions?

---

### Post by hawthornso23 on 2012-04-09
The fax standard is guarded by an obnoxious patent wielded by a vicious troll. Good Luck.

---

### Post by kimda on 2012-04-09
Faxing with Ubuntu (Linux) doesn't work with this printer. Have a look at the following sites. I would advise you to either do this in Windows or maybe look for another solution. 

[http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html](http://hplipopensource.com/hplip-web/models/deskjet_aio/deskjet_2050_j510_series.html)

[https://answers.launchpad.net/hplip/+question/117008](https://answers.launchpad.net/hplip/+question/117008)

---

### Post by Overtipper on 2012-04-10
[SIZE=3]Hi again!

  Thanks for the info....  This sucks. :)  I have two laptops - one is the HP G72, and that one is dual boot.  The other is a NC6440 dual core that I rebuilt.... and now that I have pretty much gotten everything I want as far as software flipped to the Linux side.... if I wanna do this, I have to go back to 7.  Nuts. :)

  I wonder if it would work via Wine?
[/SIZE]

---

### Post by xyzzyman on 2012-04-10
Is it just a page or two that you have to fax at a time?

You have a few options.

1.) Use a free online service like faxzero.com (I've used it a # of times recently)

2.) Set up PBX in a Box in a virtual machine (VirtualBox or VMWare), and install IncrediPBX 3 and IncrediFax, and use a google voice account and fax through that (Yes it works, I've done it sending and receiving)

3.) If you have a functioning modem on one of your systems and a landline, use HylaFax in linux. I haven't set it up personally but I know people that have and it works great.

---

### Post by Benchrest on 2012-04-14
Hope I'm not to far off base here, but the few times I've had a document sent to me to sign and return fax, I have found the other end to accept my printing the document, sign it and then scan it as a jpg file and attach it to an email. When printed on the other end it looks the same.Just requires the persons email address instead of fax number.

---

### Post by xyzzyman on 2012-04-17
Simple Scan will also save as PDF which is even nicer than sending as a JPG, because then you know it'll print out at the right size with minimal effort by the receiving party.

---

### Post by JBeardsley on 2012-07-10
If you need to sign your life away more than two times a day and you don&#8217;t want to buy a fax machine or have a dedicated phone line, an [online fax]("http://www.faxcompare.com/#whatis") service (I included an explanatory link in case someone doesn&#8217;t&#8217; t know what) is a cheap way to send many documents.  Online fax services give you a dedicated fax number and let you receive and send faxes through an online dashboard and your email.  These email-to-fax services are a great option since your clients/employers prefer to receive documents via fax.

---

### Post by HermanAB on 2012-07-10
Install Gimp and SimpleScan. Scan into Gimp, paste scanned signature into it, print to a PDF, email PDF file, done.

---

