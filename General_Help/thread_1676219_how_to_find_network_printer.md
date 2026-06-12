---
title: "how to find network printer?"
date: 2011-01-26
forum: General Help
---

### Post by raymondvillain on 2011-01-26
I am using Ubuntu 10.10 (64 bit) on a desktop that is part of a small home network.  The server has a laser printer on its parallel port.  I want to use the printer connected to the server.

If I go to System>Administration>Printing and click on "add printer" a box opens with choices, one of which is to find a network printer.

What do I enter in the box that asks for the Host location?

If I enter the name of the server, or its IP address, and click the "Find" button, it goes to work and says "searching", then comes back and says "printer not found at that address".

What is the correct way to enter the location of the network Host and its printer? 

The server is running Ubuntu 10.10 server edition.

---

### Post by gordintoronto on 2011-01-26
I click on Network Printer and wait a minute or so, and my printer appears. I do not attempt to tell it where the printer is. (I've installed multiple versions of Ubuntu on multiple computers since buying a Brother network laser, which I have attached to my router by Ethernet, and it always works for me.)

---

### Post by vidtek on 2011-01-26
The key is "parallel port" interface.

The server to which the printer is connected must share the printer.  

Depending on whatever O.S. the server is running there will be an option to share the printer those settings will tell you the exact share name so ubuntu will see it.

Tony.

---

