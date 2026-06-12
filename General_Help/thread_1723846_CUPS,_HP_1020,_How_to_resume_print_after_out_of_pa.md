---
title: "CUPS, HP 1020, How to resume print after out of paper?"
date: 2011-04-07
forum: General Help
---

### Post by Noah_Danwell on 2011-04-07
Hello,  
I have:  
server with Ubuntu Server 10.10 + CUPS + **HP LaserJet 1020  **
and two computers (kubuntu 10.10 and windows 7) connected via LAN to server

How can i resume (continue) printing on this computers, when i start print and have "out of paper" during the printing process?

There are no "resume button" both on the CUPS and my printer. 

p.s. sorry for bad english

---

### Post by Butthead on 2011-04-07
I believe there is a "printer control" tab (last tab when you open it) where you can resume a stopped printing job in the HP Device Manager. :confused:

---

### Post by Noah_Danwell on 2011-04-08
> **Butthead said:**
> I believe there is a "printer control" tab (last tab when you open it) where you can resume a stopped printing job in the HP Device Manager. :confused:
Is that i should doing on the web-page (****:631) of my printer?

---

### Post by Butthead on 2011-04-08
> **Noah_Danwell said:**
> Is that i should doing on the web-page (****:631) of my printer?

??? :confused:

No, if you get a "out of paper" error prompt in Ubuntu, just open the HP device manager and look for the "Printer Control" tab in it.  If you then click on the "Printer Control" tab, there is a button to resume printing in it (at least there is in Kubuntu). :guitar:

---

### Post by Noah_Danwell on 2011-04-09
On the server Ubuntu _Server_ installed (without any DE: KDE, Gnome, etc). Only console. 

So I do not get any errors and do not even know what the command can see the print queue. However, I think that any console command does not work, because even in the CUPS server task is considered successful even if it was interrupted due to lack of paper.

In the Kubuntu in "Print queue window" print task simply disappears, regardless of whether there was a successful print or interrupted due to lack of paper.

-----------------------------------------------------

I read that Linux, working with the printer, first loads the firmware, and then passes it to the job to print the page.
 Apparently CUPS just do not know how to work with this firmware, to see the success or failure has been a print and just defaulted to its success.
 It's all in my view is amateurish.

---

### Post by Noah_Danwell on 2011-04-09
Under the "out of paper" I do not understand the error, but the situation when the paper comes to an end and just did not know how to say it in English ...

---

### Post by Noah_Danwell on 2011-04-10
**SOLVED!**

From the INSTALL file: 
    These printers do not have a "button" when you run out of paper.     

[LIST]
[*] But, there is a GNOME gui in:          Applications -> System Tools -> HPLJ 10xx Replaced Paper It requires tcl, tk, and tix.  Fedora 5 and later:         # yum install tcl tk tix
[*] or, you can simulate this by reloading the paper and doing:          _$ usb_printerid /dev/usb/lp0_
[*]or, you can open the print cartridge door and then close it.
[/LIST]
 
But now i want to find some program, which connects to server and execute this command. For convinience.

---

### Post by linuxuser12345 on 2011-04-10
I have an HP printer myself. When the printer runs out of paper, reload it, and once it is reloaded press the "ok" on the printer if it has one.

---

### Post by Noah_Danwell on 2011-04-10
> **linuxuser12345 said:**
> I have an HP printer myself. When the printer runs out of paper, reload it, and once it is reloaded press the "ok" on the printer if it has one.
The are no any buttons on printer.

---

