---
title: "How do I network a printer"
date: 2009-12-21
forum: General Help
---

### Post by qplazm on 2009-12-21
Hi.. all I am new to ubuntu..

I have two Pc and a printer.. but i would like to network the printer.. how can I do that..

This is my status.. 

I have installed the printer on one system..in the following manner..
system/administrator/printer.
and the printer was detected automatically.. ie hp laser jet 1200 and it is printing the documents without any problem.. 

but for the other computer I did 
system/administrator/printer/

then I gave network printer.. and gave the host number it is giving a message 
that no printer is found in that address..

please help..

---

### Post by plucky on 2009-12-21
> **qplazm said:**
> Hi.. all I am new to ubuntu..

I have two Pc and a printer.. but i would like to network the printer.. how can I do that..

This is my status.. 

I have installed the printer on one system..in the following manner..
system/administrator/printer.
and the printer was detected automatically.. ie hp laser jet 1200 and it is printing the documents without any problem.. 

but for the other computer I did 
system/administrator/printer/

then I gave network printer.. and gave the host number it is giving a message 
that no printer is found in that address..

please help..

You need to share the printer.

On the system with the printer attached,go to **System > Administration > Printing > Server Settings** and tick the box that says "Publish shared printers connected to this system".

And then on the other system go to the same location and tick the box that says "Show printers shared by other systems". and then see if you can add the printer.

Good Luck

---

### Post by qplazm on 2009-12-21
WOW... thanks it worked...hats of to you ...:)

---

### Post by StuartN on 2009-12-21
You can also buy very cheap ethernet / wireless printer servers, so that you do not need an attached computer running all the time. A printer server can save its own cost in energy savings and convenience.

---

