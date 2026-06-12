---
title: "Wireless Printing on Canon MP560"
date: 2011-03-13
forum: General Help
---

### Post by pseudosmart on 2011-03-13
I found instructions on how to install the drivers for my Canon MP560 to get the printer working when connected with the USB cord. But I still can't seem to use the scanner or print wirelessly to the printer. Not really sure where to start. I'd appreciate any suggestions anybody has. Thanks in advance for your help.

---

### Post by Foxheadz on 2011-03-13
[http://ubuntuforums.org/showthread.php?t=1264928](http://ubuntuforums.org/showthread.php?t=1264928) check out the last post on the first page of that thread.

---

### Post by pseudosmart on 2011-03-13
Thanks for the link, that's actually where I found the instructions for installing the drivers to get it to print over usb connection. But it still isn't recognized as a network printer.

---

### Post by Foxheadz on 2011-03-13
well i got it to work using [these]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100236502.html") for just printing and [these]("http://support-asia.canon-asia.com/contents/ASIA/EN/0100237802.html") for scanning.

---

### Post by pseudosmart on 2011-03-13
Thanks again. I got the printer printing and scanning, but only when connected through USB. Is it working wirelessly for you?

---

### Post by Foxheadz on 2011-03-14
yeah odd, what happens when you go to add a wireless printer?

---

### Post by pseudosmart on 2011-03-14
well, when I click on add printer, and look under network printers, the canon mp560 just isn't listed there. Which I don't understand, because I installed the drivers for it, and it prints and scans fine when connect through USB.

---

### Post by Foxheadz on 2011-03-14
1. is there a little rotating circle at the bottom, 2. are you 100% sure your on the same network/it's connected to the network and 3. maybe try restarting your computer.

---

### Post by pseudosmart on 2011-03-14
To answer your questions:

1. There's no rotating circle at the bottom.
2. I'm sure I'm connected to the same network, you have to choose the network directly on the printer, and put in the password.
3. I'll try restarting and let you know what happens. 

Thanks again.

---

### Post by pseudosmart on 2011-03-14
Well, restarting didn't seem to do the trick. All I see listed under Network Printer is
Find Network Printer
AppSocket/HP JetDirect
Internet Printing Protocol
LPD/LPR Host or Printer
Windows Printer via SAMBA

I would try to find my Network Printer by its IP address in the box where it says hostname, but I don't know how to find out what my printer's IP address is. Do you know how I could find it? I tried looking in my router's admin page, but couldn't find it there. And I looked in the CUPS admin page, but couldn't find it there either. I just don't understand why it's not seeing, because I was able to print wirelsesly in Windows 7? Thanks again for your help.

---

### Post by pseudosmart on 2011-03-14
Also, when I check the printer properties of the installed canon mp560, I have Shared selected, but to the right of that it says 'Not published, See server settings'.

---

### Post by Foxheadz on 2011-03-14
ok try this. First delete forms of mp560 that you have made wireless or usb. Then quit the printer application. Once it's closed reopen it. Wait for a few minutes and then see if it's their.

---

### Post by pseudosmart on 2011-03-14
Thanks for the suggestion. I tried deleting the printer, closing the Printing application. Then I waited a few minutes, reopened, but it's still not listed under network printers. Next to Find Network Printer, there is a box called Host. Do you know how I could find the address to put in there and maybe it would find it that way? Thanks again.

---

### Post by Foxheadz on 2011-03-14
Well I mean open it then wait a few minutes. I tried deleting it and then re adding it but discovered that it wasn't showing up. Being the easily distracted person i am i started to watch tv and when i looked back it was on.

---

### Post by pseudosmart on 2011-03-14
Okay, I opened the New Printer window, and waited several minutes, but it's still not showing up. Any other suggestions? I really appreciate your help.

---

### Post by Foxheadz on 2011-03-14
Hmm well i can't seem to reproduce your error so i can't really find a way to fix it. You sure you installed the common printing drivers before the mp560 specific ones?

---

### Post by pseudosmart on 2011-03-14
I did install the common driver first. But I had to use ‘sudo dpkg -i –force-architecture [package.deb]’ to install the drivers, because I guess they were designed for 32-bit and my system is 64-bit. I'm starting to wonder if maybe that's why it's not working wirelessly. Do you think that might be why?

---

### Post by Foxheadz on 2011-03-14
Possibly, i have a 32 bit system so it explains why it works on mine but not yours.

---

