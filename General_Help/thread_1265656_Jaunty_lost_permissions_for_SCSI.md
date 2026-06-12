---
title: "Jaunty lost permissions for SCSI"
date: 2009-09-13
forum: General Help
---

### Post by momist on 2009-09-13
Can someone please help me out here?

I've recently upgraded to Jaunty 9.04 and have found and cured several issues myself, but I can't find the cure for this one.  I run Ubuntu on a 386 AMD based machine, and connect my SCSI Epson GT7000 scanner through a PCI SCSI adapter card.  I've managed to get the scanner working OK, but I have to issue the command
```
sudo chmod 777 /dev/sg3 
```
after every reboot.  I'm looking for the "correct" way to make the permissions stick.  I've discovered that Jaunty now has two udev/rules.d directories, one in /etc/ and another in /lib/ but neither of these now has a permissions file in them, as previous releases used to.  

So what is the right way to assign permanent permission to access a SCSI device, which may or may not be switched on at boot time?

Thanks for any help offered.

Ian

---

### Post by momist on 2009-09-20
I found the solution here:
[http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html](http://jhansonxi.blogspot.com/2009/08/writing-udev-rules-to-get-scsi-scanner.html)

My 45-scsi-scanner.rules reads as follows:```
# permissions for EPSON GT-7000  SCSI scanner
SUBSYSTEM=="scsi_generic", ATTRS{vendor}=="EPSON  ",ATTRS{model}=="SCANNER GT-7000  ", NAME="%k", SYMLINK="scanner%n", MODE="0660", GROUP="scanner" 
```

And make sure you are a member of the "scanner" group.

---

