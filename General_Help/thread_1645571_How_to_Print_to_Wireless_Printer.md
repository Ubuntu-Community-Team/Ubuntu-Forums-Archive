---
title: "How to Print to Wireless Printer"
date: 2010-12-14
forum: General Help
---

### Post by borgward on 2010-12-14
Trying to print from my laptop to friends wireless printer. I see his printer "7600 Series" in Network - File Browser. How do I print to his printer. I have text document. I click on "Print", but only "Print to file comes up"

I did System -> Printing -> Help -> Troubleshoot

Got: CUPS Service Stopped
The CUPS printer spooler does not appear to be running. To correct this choose

system -> Administration -> Services

There is not "Services there"

What to do? Ubuntu 10.04 LTS

---

### Post by cipherboy_loc on 2010-12-14
Open up a terminal (Applications -> Accessories -> Terminal) and run:

```
sudo service cups start
```

You will be prompted for a password, and then cups will start.


Cipherboy

---

### Post by Casyl50 on 2010-12-14
I went also to coffee shop....they promo free printing..but when I print it would not process. It says need to connect the printer, and then we do it again, again and again...still not working. Do my laptop is not compatible with their printer. Why their printer could not recei:KSved.

---

### Post by cipherboy_loc on 2010-12-15
It sounds like you didn't have the right cups drivers installed. What was the make/model of the printer? Was it something major, like an HP Officejet, or some smaller, lesser known brand?


Cipherboy

---

### Post by AlanR8 on 2010-12-15
Just bought a wireless HP all in one printer for my wife. (Christmas present). 

It was easier to set up in Linux that it was on her iMac! Needed the CD to install drivers on the Mac, just went to add a new printer in Ubuntu, asked it to search the network, it found the printer straight away, made sure it was NOT an Internet printer and clicked next. The driver list came up with a recommendation to accept the default selection...click and job done.

---

### Post by Mark Phelps on 2010-12-15
Similar positive experience with an HP 8500A wireless printer and Ubuntu 10.10.. CUPS found it after a network search, chose the driver from the list ... prints without problems.

---

### Post by borgward on 2010-12-15
I did:

sudo apt-get install --reinstall cups

After I print, I get message Document printed. Document has been sent to Lexmark 7000 for printing.but the printer does not print. Nothing comes out. It does print from a Mac laptop though.

---

### Post by AlanR8 on 2010-12-16
Hate to say it but it could be the choice of printer. You're normally safe with HP, not sure about Lexmark.

---

### Post by borgward on 2010-12-16
choice of printer?

How is that, no Linux driver for it? How would I find if Lexmark 7000 is supported by Ubuntu?

---

### Post by efflandt on 2010-12-16
Is it an inkjet printer?  Lexmark laser printers are no problem because they support common HP PCL and postscript printer languages (I have a Lexmark C543dn color laser printer that works great).

But Lexmark inkjet printers can be more problematic, because they may require some sort of additional driver.  I have an old Lexmark inkjet printer from many years ago that was a brain dead raster only Windows printer (you could not just send plain text to it, the driver had to send it each line of dots).

---

### Post by borgward on 2010-12-19
Will there be a problem if I try using my laptop at multiple places, each having a different wireless printer w/each needing a different driver?

---

