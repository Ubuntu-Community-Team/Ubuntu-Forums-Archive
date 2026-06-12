---
title: "Remote printing from AIX to Ubuntu 10.10 with LPR"
date: 2012-01-01
forum: General Help
---

### Post by ptx on 2012-01-01
Dear all,
My setup as follows.
LPD client AIX 5.3 server
LPD Server Ubuntu 10.10 workstation (Epson LX 300+ printer is attached locally)

While sending print job from AIX to Ubuntu, am getting an error. In cups  error log,( Error message is “+IPP  client-error-document-format-not-supported+”).
 **Steps I followed**

**In AIX Server:**
I created a remote Printer queue in AIX with system V as type of spooler on remote server.

**In Ubuntu workstation:** 

Enabled LPD support (reference: [http://computertechnos.blogspot.com/2008/08/sharing-printers-in-ubuntu.html](http://computertechnos.blogspot.com/2008/08/sharing-printers-in-ubuntu.html))

Note: 
The printer is working with redhat LPD Server. Issue is reporting only  on Ubuntu PC's. I hope this is the recommended method to connect remote  Linux printer to AIX Server, Please correct me if I am wrong. 



I am able to get print out from windows and redhat linux Pc's error reported on Ubuntu 10.10 Pc.

Any help/guidance/suggestions would be most helpful.

---

