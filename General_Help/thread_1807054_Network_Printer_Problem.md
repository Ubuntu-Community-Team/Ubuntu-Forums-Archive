---
title: "Network Printer Problem"
date: 2011-07-18
forum: General Help
---

### Post by Mar Komus on 2011-07-18
Bottom line: I was able to print to a network printer before. Now I can't. I can print from my Vista partition, but not from 11.04.

Level of Linux experience: Like listening to a conversation between a Brit and an American.

Details:

(1) Hardware
[INDENT]Dual boot on Dell Inspiron 530 (11.04 and Vista)[/INDENT]
[INDENT]iomega print server GPSU21[/INDENT]
[INDENT]hp Office Jet 5610 All-in-One[/INDENT]

(2) Test page: pdf file from a usb drive; other test pages produce same results

Installation of network printer:

I followed what I believe to be standard procedure: Using the Unity interface, I opened up the Printing application. I then clicked "Add". Then "Network Printer", then "Find Network Printer". I typed in the Host (192.168.1.6; static assignment made while in Vista via iomega's software). Then it searches. It fills in its own blanks thus: Under the heading "Devices" > "Network Printer" it says, "JetDirect (192.168.1.6) (192.168.1.6)". In the panel on the right it says, "Host: 192.168.1.6:631/ipp", then, "Queue: ipp". I click "Verify..." and an error message pops up that says, "Inaccessible The print share is not accessible"

If I proceed forward, I can install drivers, but nothing will ever print. Following procedure, I click to print a test page. The job is sent to the queue and then I get this Printer State message: "Stopped - Destination printer does not exist!"

Help? :confused:

---

### Post by Topsiho on 2011-07-18
From what you say I guess the printer is connected to the network by ethernet. I recently installed my printer just that way, and I love it: all my systems are peers on this network for printing.

I don't know whether hplip is needed, as it was already on my systems. But on each computer I only had to do (and you did too):

Using the printing application I selected Add, Networkprinter, waited a little untill the printer was found, selected this and pressed Continue. The procedure after this is quite straightforward, filling in some information, letting it find the correct drivers for your model, and Continuing.

I first proceeded just like you did, and did not get satisfactory results that way.

Most HP printers are extremely easy to set up.

Good luck :)

Topsiho

---

### Post by ajgreeny on 2011-07-18
It could be worth adding the **hplip-gui** if you don't already have it, opening the **hplip toolbox** from your menus, or unity dashboard, I think it's called, then seeing if you can get it to show with the **Setup Device** icon in the toolbar.  It worked faultlessly for me using Lubuntu 11.04 with a wireless HP Photosmart A10 all in one.  Now all machines in the house can print to that with no problems at all.

My printer is not connected to the router with a cable as there is no network socket, but I did use USB to connect it first as I was unsure how to get the wireless to work.  Once I had it working by USB it was a very simple job using the hplip setup device utility, so that now the printer is connected to electricity only by cable, everything else is wireless.

---

