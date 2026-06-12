---
title: "Print Output Not Printing"
date: 2011-04-25
forum: General Help
---

### Post by jcobban on 2011-04-25
When I try to print from OO.org the output is simply disappearing.  That is **nothing** appears in the print queue viewed using the GUI: System/Printing/select printer/ctl-F.  When I look at properties from this dialog it shows "stopped or powered off".  

From the command line:

>sudo lpstat -a
Deskjet-F4500-series accepting requests since Tue 19 Apr 2011 11:27:26 AM EDT
lpq
Deskjet-F4500-series is not ready
Rank    Owner   Job     File(s)                         Total Size
1st     jcobban 150     BusinessCards                   18498560 bytes
2nd     jcobban 151     BusinessCards                   6169600 bytes
3rd     jcobban 152     BusinessCards                   6169600 bytes

There is nothing in /var/adm/lp/log

The printer **is** powered on and plugged into a USB port.  I have powered the printer off and back on again.  What else do I have to do to make the printer "ready" to Ubuntu?  Why do the print jobs show up in lpq but not in the GUI?  I can print to this printer from Windows XP when I plug it into that system.

---

### Post by ajgreeny on 2011-04-25
Check that you have **hplip** and **hplip-gui** installed and try printing again.  That may do it and allow your printer to work.

---

