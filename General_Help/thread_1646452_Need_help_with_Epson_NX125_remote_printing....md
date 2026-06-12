---
title: "Need help with Epson NX125 remote printing..."
date: 2010-12-15
forum: General Help
---

### Post by alem189 on 2010-12-15
Hello, I have a problem with remote printing from Ubuntu with my Epson NX125. Here are some details:

The remote machine is a Windows XP, which is connected to the printer via USB.
I can print to another printer hosted on that computer, but it prints inconsistently (not a problem with Ubuntu, a problem with the printer).
I can send the job to the printer, and the printing icon says 'job complete', but all that happens is that I hear some whirring from the printer.
I can print fine from within XP.
I am a noob to printing in Linux, and any help would be appreciated.

---

### Post by alem189 on 2010-12-16
bump

---

### Post by alem189 on 2011-01-13
bump

---

### Post by alem189 on 2011-01-14
bump

---

### Post by cchhrriiss121212 on 2011-01-14
Epson printers are supported on linux through Avasys, so you need to get a driver from them:
[http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/](http://avasys.jp/eng/linux_driver/download/lsb/epson-inkjet/escp/)
Your model is listed here about halfway down, download the relevant deb package and install it. Then go to Admin>Printing to add the printer.

---

### Post by alem189 on 2011-02-14
I've installed that, added the printer, and still, nothing is happening. Any more thoughts?

---

### Post by jbiggs12 on 2011-02-14
Under which column was it? if you're adding the printer as a network printer than I'm pretty sure that you'd have to add it under the "Network Printers" column.

---

### Post by alem189 on 2011-02-15
So I reinstalled the printer, and it works! For now at least...  I would like to keep this thread open for a few more days though, in case anything for some reason goes wrong later.

---

### Post by alem189 on 2011-02-20
Yep, it's fixed. Thanks!

---

