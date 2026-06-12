---
title: "Brother HL-2170W on Ubuntu 9.10 Desktop - Installation"
date: 2010-01-25
forum: General Help
---

### Post by _dino_ on 2010-01-25
Hi All,
Can anyone give me step by step instructions on how to install Brother HL-2170W wireless printer on Ubuntu 9.10 Destop.
Much Appreciated,
Dino

---

### Post by Ginsu543 on 2010-01-25
Are you trying to install it wirelessly or through the usb port? Either way, you can do it by going to System --> Administration --> Printing. Then click on the "New" button (or you can use the menu option Server --> New --> Printer). Ubuntu will search your system for available printers. If you have the HL-2170W connected through the usb port, then you should see it listed under devices. If you click on it, it should say in the Description: "A printer connected to a USB port." If you want to connect to the HL-2170W wirelessly, then click on the "Network Printer" button. It should just show up (mine does). Either way, click to select and then click "Forward". The program will then take you through the process of loading the appropriate drivers for it (there are several options, but simply sticking to the recommended one should be fine). Once that process is finished, you should be ready to go! :)

---

### Post by _dino_ on 2010-01-25
I am trying to install it wirelessly.  I tried to select Network Printer -> Find Network Printer (as well as the other buttons) but it would not find my printer.  However, I found a useful HOWTO here to install lpd and cups drivers and I did it and my printer got added but it is added as Device URI=usb:/dev/usb/lp0.  I believe this is the problem since my printer is not connected through a wire.  So, how do I fix this?
Much appreciated
_dino_

---

### Post by garvinrick4 on 2010-01-25
That printer and driver were in printer configuration in GUI with install of 9.10 a lot of Brother HL printers are there?

---

### Post by garvinrick4 on 2010-01-25
Are you running Windows also, did you have to run a cat 5 from printer to router to install?

---

### Post by mykrob on 2010-01-25
I have that printer. WHen hooked up with USB, it just works, however, the printer does not have a control panel built in and requires Windows or Mac based software to configure it for use with a wireless network. I used Windows XP in VirtualBox to configure it, the printer configuration in Ubuntu was able to see it on the wireless network and connected just as easily as it did via USB. Its a great printer, just sucks that you have to use windows to configure the network...

---

### Post by _dino_ on 2010-01-25
Nope, It is not in there, I checked that first and multiple times

---

### Post by _dino_ on 2010-01-25
HI Garvinrick4,
I am novice to all this but to explain, ... when I installed it on windows and initially did it through the wire as the manual suggests, that is nedded to do only on initial installation even thouh you do wireless install.  Then I disconnected wire and it worked fine wirelessly as well.  The problem is with my Ubuntu 9.10 Desktop.  There is no manual on how to install it so I followed one of HOWTOs on this site.  Everthing installed just fine (lpr and cups), but the printer wont print.
I suspect because in Printer Properties, it says that device URI is something like "usb/usr...." but the printer is not connected through usb.  I dont know how to fix that though.

---

### Post by _dino_ on 2010-01-25
I am sure many have that printer and that it is great but the question is rather on how to install it.
Thanks

---

### Post by garvinrick4 on 2010-01-25
> **_dino_ said:**
> I am sure many have that printer and that it is great but the question is rather on how to install it.
Thanks

[http://solutions.brother.com/linux/sol/printer/linux/cups_network.html](http://solutions.brother.com/linux/sol/printer/linux/cups_network.html)


Here is a link for bother printers. I believe Mydrob in earlier post is good one to
ask if this does not work for you.

---

### Post by mykrob on 2010-01-26
Without having to install any additional pacakges, and assuming the printer is already setup on your wireless network and also the Ubuntu computer is on the same network, whether it is wired or wireless, it should be as simple as

System-->Administration-->Printing-->New

Again, provided the printer is actually on the same network, it should be found automatically. Under "Select Device", go to Network Printer and select your auto-detected printer, then verify the model number.

Is your printer even showing up under network printer?

---

### Post by _dino_ on 2010-01-30
> **mykrob said:**
> Without having to install any additional pacakges, and assuming the printer is already setup on your wireless network and also the Ubuntu computer is on the same network, whether it is wired or wireless, it should be as simple as
 
System-->Administration-->Printing-->New
 
Again, provided the printer is actually on the same network, it should be found automatically. Under "Select Device", go to Network Printer and select your auto-detected printer, then verify the model number.
 
Is your printer even showing up under network printer?
 
Yes, it is showing.  Printer has been set; however, it will not print.  When I hower over printer icon, it says "Printer may not be connected".  I notice other people are having same issue.

---

### Post by cmfeeney on 2010-02-04
Sorry, no answer here; just another example. I have same printer wireless conncetion worked fine from Macs and XP. It shows up in the print administrator, and everything looks good...but test page won't print. It just sits in the queue and eventaully times out. I do get an error msg when troubleshooting, which says that the printer isn't "enabled". Go to printer's properties (or is it policies?)tab  to enable, but it won't stay enabled... I check the box and it unchecks in a few seconds. I'm running 9.10 from a LIVECD, as I wanted to verify things like printing, network, etc BEFORE bothering to actually install another OS. I thought maybe that was the issue. So far, not very promising.

---

### Post by plucky on 2010-02-04
> **cmfeeney said:**
> Sorry, no answer here; just another example. I have same printer wireless conncetion worked fine from Macs and XP. It shows up in the print administrator, and everything looks good...but test page won't print. It just sits in the queue and eventaully times out. I do get an error msg when troubleshooting, which says that the printer isn't "enabled". Go to printer's properties (or is it policies?)tab  to enable, but it won't stay enabled... I check the box and it unchecks in a few seconds. I'm running 9.10 from a LIVECD, as I wanted to verify things like printing, network, etc BEFORE bothering to actually install another OS. I thought maybe that was the issue. So far, not very promising.

For that printer you have to download the drivers from the [Brother Linux Driver website](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and install them before the printer will work.The install instructions are also on the website.

Probably not a good idea with the Live CD as it will all disappear when the system is shutdown.

---

### Post by ethanay on 2010-02-04
> **mykrob said:**
>  Its a great printer, just sucks that you have to use windows to configure the network...

It is a great printer, and you can set up the network without Windows.  I just did:  simply hook it up to your router via network cable.  Find the IP address (use your router's interface or install and run ```
nmap 192.168.x.*
``` where "x" is specific to your network (usually 0, 1, or 2).

Enter the printer's IP address into your browser to access the network interface, where you can configure additional advanced options.  Set up the network, disconnect the network cable, and enjoy wireless printing :)

---

### Post by soyatti on 2011-03-19
> **cmfeeney said:**
> Sorry, no answer here; just another example. I have same printer wireless conncetion worked fine from Macs and XP. It shows up in the print administrator, and everything looks good...but test page won't print. It just sits in the queue and eventaully times out. I do get an error msg when troubleshooting, which says that the printer isn't "enabled". Go to printer's properties (or is it policies?)tab  to enable, but it won't stay enabled... I check the box and it unchecks in a few seconds. I'm running 9.10 from a LIVECD, as I wanted to verify things like printing, network, etc BEFORE bothering to actually install another OS. I thought maybe that was the issue. So far, not very promising.

i had exactly the same problem and fixed w/o drivers installation.
in properties of my brother (hl-2170w) it's host after printer creation was 'BRN008077E19242'. i've replaced it with printer's IP address (mine is permanently on 192.168.1.201) and it just worked :)

---

