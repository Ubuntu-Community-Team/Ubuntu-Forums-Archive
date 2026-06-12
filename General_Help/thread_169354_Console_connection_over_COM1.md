---
title: "Console connection over COM1"
date: 2006-05-02
forum: General Help
---

### Post by Dragonmantank on 2006-05-02
Not sure if this is the right place for this or not, but here goes.

I just got a pair of Sun Ultra Enterprise 2 machines, ones without true VGA connectors. Since these were pulled from a now defunct company, passed around until they got to me, I don't have monitors nor keyboards or mice to go with them. 

From what I understand I can use a serial connection between my main box (Ubuntu) and the Sun machines. I have a DB9F->DB25M cable, but I'm not sure how to view the connection from within Ubuntu. I know in Windows I can use Hyperterminal, but I'm at a loss for what to use under Ubuntu.

---

### Post by [2]BoxingFiend on 2006-05-02
been a while since i've play around with serial stuffs, but you can use kermit to talk to a COM port.  do a google for the requirement baud rates, i'll dig around my manuals to see if you need a special pin out on the dongle

---

### Post by Dragonmantank on 2006-05-03
I've tried using Minicom which has Kermit built in, but still no go. I found a copy of the service manual online ( [http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.sun.com%2Fproducts-n-solutions%2Fhardware%2Fdocs%2Fpdf%2F802-2561-11.pdf&ei=VVxZROXcNKXUqwL3trivBA&sig2=VyD4kWscV_WzUJhTLPRJDg](http://www.google.com/url?sa=t&ct=res&cd=3&url=http%3A%2F%2Fwww.sun.com%2Fproducts-n-solutions%2Fhardware%2Fdocs%2Fpdf%2F802-2561-11.pdf&ei=VVxZROXcNKXUqwL3trivBA&sig2=VyD4kWscV_WzUJhTLPRJDg) ) and it looks like pins 2 and 3 need to be crossed. I'm not sure how to tell this on a pre-made cable.

I've tried this with a 9-9 cable with a 9->25 adator, and a 9->25 cable itself. Minicom just reports as being 'Offline' the entire time when I try either of the serial ports on the Sun machines.

---

### Post by sdamron on 2006-06-17
I am using a cisco serial console cable to connect to the Sun line of servers.  I am connecting to some old Netra's, as well as some V240/V440's.  That seems to be the right cable, now I just need to find a version of minicom that works on Dapper :o|

---

### Post by chili555 on 2006-06-24
The key is a null-modem cable, which you can make with patience and Rat Shak parts or buy for a few dollars on-line.

The minicom that comes with Dapper works fine. sudo apt-get install minicom. Do minicom -s and set the COM port you will be using, probably /dev/ttyS0. You will probably be safe with 9600 bps. Save the configuration.

Some configuration will be needed on the box you want to log in to; I found this helpful: [http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html](http://www.tldp.org/HOWTO/Remote-Serial-Console-HOWTO/index.html)

---

