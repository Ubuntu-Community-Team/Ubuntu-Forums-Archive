---
title: "HELP! USB printer no longer works"
date: 2011-12-01
forum: General Help
---

### Post by pc.maint on 2011-12-01
I think I must have tweaked something wrong... My EPSON R300 no longer works on this machine (spec below). It works on other machines (all Ubuntu 10.04 32bit) and other things work in usb port.

It does not appear on **lsusb** and **tail -f /var/log/syslog** gives the following when I plug the printer in.

[ 1310.549906] usb 2-1.1: new high speed USB device using ehci_hcd and address 9
[ 1310.639816] usb 2-1.1: device descriptor read/64, error -71
[ 1310.839648] usb 2-1.1: device descriptor read/64, error -71
[ 1311.041429] usb 2-1.1: new high speed USB device using ehci_hcd and address 10
[ 1311.138083] usb 2-1.1: device descriptor read/64, error -71
[ 1311.341635] usb 2-1.1: device descriptor read/64, error -71
[ 1311.537695] usb 2-1.1: new high speed USB device using ehci_hcd and address 11
[ 1311.959563] usb 2-1.1: device not accepting address 11, error -71
[ 1312.039577] usb 2-1.1: new high speed USB device using ehci_hcd and address 12
[ 1312.456530] usb 2-1.1: device not accepting address 12, error -71
[ 1312.456681] hub 2-1:1.0: unable to enumerate USB device on port 1

If anyone has any ideas what I may have screwed up, please let me know. Thanks.



Ubuntu 10.04 64bit
Kernel 2.6.32-35-generic
GNOME 2.30.2
Core i7-2600K
GIGABYTE GA-Z68XP-UD3P

---

### Post by pc.maint on 2011-12-08
Still no joy :-(

I guess no one else has any ideas...

I can only think it must be a problem with 64 bit OS as all 32 bit systems are working OK.

---

### Post by KaitlinM on 2011-12-08
> 
I can only think it must be a problem with 64 bit OS as all 32 bit systems are working OK.

That would be my guess, but you said it used to work on your 64bit. So is this a new problem, then? Have you checked the CUPS for another driver?

---

### Post by pc.maint on 2012-01-05
I think that this machine may have had 32-bit installed when printer was working... Not found any new drivers yet.

I have side-stepped the problem by using different printer (Samsung CLP-325) on this machine and use Epson on machine with 32-bit installed. Not a proper solution I know, but it gets me up and running.

Thanks for the response.


}:-)>

---

