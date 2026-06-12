---
title: "HP Deskjet 3745 + CUPS"
date: 2009-09-10
forum: General Help
---

### Post by prem1er on 2009-09-10
Anyone get this printer working with CUPS. I have the admin page up and running now, but the driver seems to be missing.  Anyone have a link to where I can get it?  Thanks.

---

### Post by prem1er on 2009-09-10
Ok, so I got everything up and running. HP makes a pretty sweet installation file for their package of linux drivers available.  It is a .run file available here..
[URL="http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740"]
http://www.linuxprinting.org/show_printer.cgi?recnum=HP-DeskJet_3740[/URL]

Download directly, or copy this file to your ubuntu box.  Make it executable..

```
sudo chmod +x hplip-3.x.x
```

Run the file..

```
./hplip-3.x.x
```

This will install a series of drivers to your machine in the directory that CUPS reads from.  All you need to do is go back to add a printer in CUPS and the new drivers are populated already. There is a list available on the website of supported printers.  Anyone looking for the HP Deskjet 3745 that I had mentioned earlier needs to use the driver for the 3740.

---

