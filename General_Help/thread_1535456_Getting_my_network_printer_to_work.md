---
title: "Getting my network printer to work?"
date: 2010-07-20
forum: General Help
---

### Post by holycow131415 on 2010-07-20
Well this is probably the biggest reason why I dont switch completely to linux. I do not really know how to set up printers or connect to them. I have an Epson Workforce 600 printer/ scanner that is on the network. Im a noob so please be simple as possible :)

---

### Post by pytheas22 on 2010-07-20
There's a good chance your printer is supported out-of-the-box, so go to System>Administration>Printing, click the button to add a new printer, and follow the instructions on the screen for adding a network printer.  The only thing you should need to know is the IP address of your printer.  If you need more explicit instructions than this, let me know.

If it doesn't look like a driver is available for your device, you may need to refer to [this thread]("http://ubuntuforums.org/showthread.php?t=1015830"), which has pretty straightforward instructions for installing a driver.  But again, I would first see if you can get the printing working without needing to install anything; that thread was written a year and a half ago and Ubuntu may now ship with the drivers for your printer available out-of-the-box.

---

### Post by holycow131415 on 2010-07-22
Thanks! It got it to print a test page :) It saw my printer on the network so i didnt have to know the IP address. Now, to be greedy, how would I be able to use the scanner function of the all in one? The simple scan is not communicating with my printer :(

---

### Post by Fir3chi3f on 2010-07-22
Greed is good, not sure myself but you might take a look at xsane image scanner. You can download it in the Ubuntu Software Center

Quick google search for potential solutions:
[http://lmgtfy.com/?q=xsane+network+scanning](http://lmgtfy.com/?q=xsane+network+scanning)

Good luck!

---

### Post by cgb on 2010-07-22
The xsane Image Scanner should work with your printer.  I used to have the same printer and it worked fine..

---

### Post by pytheas22 on 2010-07-22
+1 for XSane.  SimpleScan has a nicer interface but I've also had issues getting it to connect to my scanner.  Hopefully XSane will just work; if not let us know.

---

### Post by craigslist123 on 2010-07-22
Connecting a printer to a computer and sharing the printer from that computer is the most common solution for sharing a printer because of the ease and price. The primary disadvantage of this is that the computer must always be on in order for the printer to work. Although this solution may not be the best solution for everyone it is usually the easiest and cheapest solution for sharing your printer between all the computers on your network.

   ----------------
  [FONT=&quot][Craigslist Search](http://www.allofcraigslist.com)[/FONT]

---

