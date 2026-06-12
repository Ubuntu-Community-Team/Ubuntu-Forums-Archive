---
title: "Getting Printer Information"
date: 2010-03-18
forum: General Help
---

### Post by s0babail on 2010-03-18
I have installed an HP LaserJet 4250 using the hp 4250 postscript driver.  The printing works but when I click on File->Print on any application (Open Office or Document Viewer), the message "Getting printer information" is beside the printer name and the print button is disabled.  After 5 or so seconds, the print button becomes enabled and I can print.  This happens every time but did not when I first installed the printer.  I would prefer to determine the cause rather than delete and re-install the printer.  My skill level with Linux is not the greatest because I am coming from Windows.

---

### Post by Youresorock on 2010-05-14
The 4250 I use at work does the same thing.  The color 4600 right next to it doesn't.

---

### Post by xiphosurus on 2010-06-02
This is a bug documented at [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/475845](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/475845)

The workaround proposed in the link above is:

For now you may disable cups to listen on "/var/run/cups/cups.sock" by commenting the line including it in cupsd.conf and leave only "Listen localhost:631" line.

Worked for me. Don't remember if a restart was required so if it happens still after applying the workaround, perform a reboot.

---

### Post by hojjat on 2011-03-18
Since the cups.sock file is owned by root user and root group, how can I edit it? I keep receiving permission error, even after trying sudo -i or sudo gedit.

---

### Post by walt.smith1960 on 2011-03-18
> **hojjat said:**
> Since the cups.sock file is owned by root user and root group, how can I edit it? I keep receiving permission error, even after trying sudo -i or sudo gedit.

I just tried to edit this file from an administrator's account and could do so.  You might try gksu gedit.  Graphical progs are supposed to be launched with gksu or gksudo(not sure of the difference) instead of just sudo.  I've seen the behavior mentioned but mine only displays for a second or two so I don't worry about it.

---

### Post by hojjat on 2011-04-07
I tried something different which solved my problem, so I thought I should post it here:

During the process of adding the network printer, Ubuntu suggested several drivers that I could use and I used to pick the first one ("HP LaserJet 4200 Series Postscript"); I removed the printer and added it again, but used the second suggested driver ("HP LasetJet 4200 hpijs pcl3, 3.10.2") and since then, I've never encountered that delay on the print dialog any more.

---

### Post by geira on 2011-07-21
> **hojjat said:**
> Since the cups.sock file is owned by root user and root group, how can I edit it? I keep receiving permission error, even after trying sudo -i or sudo gedit.

You're not supposed to edit it. As it says above, you must edit **[FONT="Courier New"]/etc/cups/cupsd.conf[/FONT]** and remove the line containing the cups.sock text.

---

### Post by joneshenrys on 2011-07-25
I had an email asking about the current print mode. If anyone has further improved the code that does not involve the use of commands in the API, please send me the details. Lines out is the code that fills my printer DataWindow dialog box that displays the details of the printer to the user. You will need to modify these to work with your own application.

---

