---
title: "Ubuntu detects my wireless printer but not the scanner (they're both the same device)"
date: 2012-04-12
forum: General Help
---

### Post by Mycotheologist on 2012-04-12
EDIT: I solved the problem. If you have the same problem, go to the bottom, I added a link to a thread which gives step by step instructions on how to fix it. BTW I often see thread with [SOLVED] in the title. How do you mark a thread as solved? 

I have a HP Photosmart wireless printer + scanner. I recently installed Ubuntu 11.10 and I can print pages over the network with it but when I try to scan something, it says there is no scanner connected. The Simple Scan program says "No scanners available. Please connect a scanner."
[IMG]http://img849.imageshack.us/img849/7818/screenshotat20120412130.png[/IMG]
and XSane says "no devices available":
[IMG]http://img407.imageshack.us/img407/1899/screenshotat20120412131.png[/IMG]
The printer/scanner is definitely turned on and connected to the network right now, I can scan it with nmap and like I said, I can print with it. Is there a way to manually point the the Simple Scan (I prefer that to XSane) to the scanners IP? I recently switched to Ubuntu 11.10 from 11.04 and I never had any trouble with scanning on 11.04. Any idea what the problem might be and how to fix it?


UPDATE: I found a command for pointing to the printer, which is hp-scan -d <device URI>. To find the scanners URI, heres what I did:
> laptop@laptop:~$ hp-makeuri 192.168.1.25

HP Linux Imaging and Printing System (ver. 3.11.7)
Device URI Creation Utility ver. 5.0

CUPS URI: hp:/net/Photosmart_B110_series?ip=192.168.1.25
SANE URI: hpaio:/net/Photosmart_B110_series?ip=192.168.1.25

Done.
so I ran hp-scan and heres what happened:
> laptop@laptop:~$ hp-scan -d hpaio:/net/Photosmart_B110_series?ip=192.168.1.25

HP Linux Imaging and Printing System (ver. 3.11.7)
Scan Utility ver. 2.2

error: Invalid device URI: hpaio:/net/Photosmart_B110_series?ip=192.168.1.25
error: No device selected/specified or that supports this functionality.
I tried the command using the CUPS URI too but got the same error message.

UPDATE2: I tried the xsane command instead:
> laptop@laptop:~$ xsane hpaio:/net/Photosmart_B110_series?ip=192.168.1.25and it worked. It works for Simple Scan too:
> laptop@laptop:~$ simple-scan hpaio:/net/Photosmart_B110_series?ip=192.168.1.25so I suppose I can just edit the menu items so that they run gnome-terminal with those commands instead.

_** SOLVED:**_
I found this thread: [http://ubuntuforums.org/showthread.php?t=1313978](http://ubuntuforums.org/showthread.php?t=1313978) and found out that I don't need to make the menu items run the terminal, I just need to put the URI after the command so for example, I right click on Applications, go into Graphics and right click on Simple Scan to edit its properties and then just change the command simple-scan to simple-scan "hpaio:/net/Photosmart_B110_series?ip=192.168.1.25".

---

### Post by wyliecoyoteuk on 2012-04-12
Click on the " thread tools" link at the top of your thread, and select "mark thread as [solved]

---

