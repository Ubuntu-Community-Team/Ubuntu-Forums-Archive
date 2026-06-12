---
title: "Printing to Win7 shared printer from Ubuntu 10.10"
date: 2011-04-12
forum: General Help
---

### Post by dburns on 2011-04-12
I'm running Ubuntu 10.10 on my Thinkpad.  I have a shared Lexmark x2650 connected to a Windows 7 64-bit box to which I'm trying to print to over my wireless network via samba.  I know I have the correct drivers installed on my Thinkpad because I can connect physically through USB to the printer and can print fine.  However when I try to print wirelessly it fails. SMB works fine because I can mount shared windows folders on the same box and can see the printer.

By watching the the print queue in the Win7 box I can see that it gets the print job but for some reason won't send it to the printer.  By monitoring /windows/system32/spool/printers, I can see the job spool but then it times out and windows deletes the .spl file.

I have another canon printer shared on a Vista box and can print to it wirelessly with no problem.

Any ideas would be muchly appreciated

---

