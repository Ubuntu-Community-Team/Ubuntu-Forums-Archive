---
title: "UBUNTU 11.10 OKI MB260 printer installation not printing"
date: 2012-03-27
forum: General Help
---

### Post by rmarduk on 2012-03-27
Hi after upgrading from Ubuntu 11.04 to 11.10 the system have founded and installed my OKI MB260
printer but I can't print !

I don't know what to do please help me.




The printer is connected throught USB.


 lsb_release -a; uname -a; lsusb


 Gives:


 No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
Linux staros-PRIMERGY-TX100-S1 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c312 Logitech, Inc. DeLuxe 250 Keyboard
Bus 007 Device 002: ID 06bc:01d5 Oki Data Corp.
Bus 008 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse




 Each printing gives error log:


 Returning IPP client-error-document-format-not-supported for Print-Job (ipp://localhost:631/printers/MB260) from localhost


 And when I go to the the [http://localhost:631/printers/MB260](http://localhost:631/printers/MB260) site i click print test page I get:


 Unsupported format "application/vnd.cups-banner".





 Thank you in advance.

---

### Post by Ms. Daisy on 2012-03-27
Check out this thread, looks like someone had the same problem as you.

[http://ubuntuforums.org/showthread.php?t=1914131](http://ubuntuforums.org/showthread.php?t=1914131)

---

### Post by rmarduk on 2012-03-28
I don't understand this:

"So if anyone else has Oki MB260, you need the MB200 linux drivers. Once  installed, do not pick the recommended one, choose the one underneath  and it will work."

That person from the link above wrote that and when I instal the drivers I have only one to choose from:

Laser Pro LL2 PCL 1.0 

and nothing else. " Once  installed," so I understand I have to instal this driver but that what is this:

"do not pick the recommended one, choose the one underneath"

?

I'm strugling with this printer for few days I don't have a idea what is wrong.

---

### Post by Ms. Daisy on 2012-03-28
Looks like you got it solved in the other thread.  

Glad you got it working.

---

