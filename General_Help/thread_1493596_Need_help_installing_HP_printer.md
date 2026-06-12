---
title: "Need help installing HP printer"
date: 2010-05-26
forum: General Help
---

### Post by jason102 on 2010-05-26
Hi guys,

So I recently just upgraded to 10.04 from 9.10, and lo-and-behold, my printer isn't detected by the Printing tool under System > Administration. Before Ubuntu was able to automatically detect and configure my printer for me, but not this time. 

By using the lsusb command, my printer was correctly listed.

So I did some research, and tried out printconf. However, the tool didn't work - it detected my plugged in printer as well but complained about a file missing - I manually checked the directory in question, and sure enough, even though I have hplip and all the associated driver files installed by default, this directory does not contain "hplip.xml". Please see the printout below:
```
Configuring HP DeskJet 5150 on usb:/dev/usb/lp0 with hplip driver as queue
"deskjet_5150".
Driver file /usr/share/foomatic/db/source/driver/hplip.xml corrupted, missing, or not readable!
Could not run "foomatic-combo-xml"/"foomatic-perl-data"! at /usr/share/perl5/Foomatic/DB.pm line 1078.

 * Reloading Common Unix Printing System: cupsd                          [fail] 
If printconf was unable to install all of your printers, please visit
http://www.linuxprinting.org/ for printer information and support from fellow
users.
```
Anyone have any suggestions for me? Thanks!

---

### Post by giants7 on 2010-05-26
try this in the terminal

sudo service cups start

---

### Post by dino99 on 2010-05-26
****  Driver file /usr/share/foomatic/db/source/driver/hplip.xml corrupted, missing, or not readable!
 ****

be sure that sources.list is clean: no mixed releases

sudo apt-get update
sudo apt-get install -f

remove/purge hplip and hpijs-ppds with synaptic then reinstall them

---

### Post by jason102 on 2010-05-26
It worked! Thanks for the quick replies! I first followed dino99's instructions, restarted the computer, logged back in, and before I did anything else I did what giants7 suggested, and then I checked Printing and it was there! I'm not exactly sure which of your suggestions helped me, but it doesn't matter now - I'm happily printing away!

Thanks again - this was a fast solve!

---

### Post by dino99 on 2010-05-26
system prefs "prefered apps at startup" or so

check/uncheck what you need

---

### Post by linko47 on 2010-11-29
I'm having the exact same problem with Debian Squeeze, but none of the methods here solve the problem.

```
root@slix:/home/user# printconf
Configuring HP DeskJet 3940 on usb:/dev/usb/lp0 with hplip driver as queue "deskjet_3940".
Driver file /usr/share/foomatic/db/source/driver/hplip.xml corrupted, missing, or not readable!
Could not run "foomatic-combo-xml"/"foomatic-perl-data"! at /usr/share/perl5/Foomatic/DB.pm line 1078.

Restarting Common Unix Printing System: cupsd.
If printconf was unable to install all of your printers, please visit http://www.linuxprinting.org/ for printer information and support
from fellow users.

```

Any suggestions?  Thank you!

---

