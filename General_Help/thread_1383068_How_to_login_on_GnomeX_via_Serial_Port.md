---
title: "How to login on Gnome/X via Serial Port"
date: 2010-01-16
forum: General Help
---

### Post by Steve Roscio on 2010-01-16
Howdy -

I'm writing a point-of-sale application in Perl/Tk, to run on Ubuntu.  For cashier accounts, I plan to just use normal Linux accounts.  Cashier login will be done by scanning a badge with a barcode ID on it.  Our barcode scanners are older serial-port types.  Thus, I'd like to login to the X (Gnome) desktop, yet read the username (and password) via a serial port such as /dev/ttyS0.

Suggestions, please, on how to do this.

Thanx in advance!
- Steve

---

### Post by jamesisin on 2010-01-16
I own a book on Perl/Tk and that's about as far as my knowledge goes.  But from a philosophical point I'd like to make a statement which you may find useful.

It will not be very secure to gain both username and password information from the badge.  This would mean that anyone who happened to be holding the badge was ipso facto that particular employee.  Rather perhaps a system where the username was gained from the badge and authentication took place from a password prompt would be a better model.

Thoughts?

---

### Post by dcstar on 2010-01-16
> **Steve Roscio said:**
> Howdy -

I'm writing a point-of-sale application in Perl/Tk, to run on Ubuntu.  For cashier accounts, I plan to just use normal Linux accounts.  Cashier login will be done by scanning a badge with a barcode ID on it.  Our barcode scanners are older serial-port types.  Thus, I'd like to login to the X (Gnome) desktop, yet read the username (and password) via a serial port such as /dev/ttyS0.

Suggestions, please, on how to do this.


[https://help.ubuntu.com/community/SerialConsoleHowto](https://help.ubuntu.com/community/SerialConsoleHowto)
As far as directing the input to the X system, I don't know.

---

### Post by Steve Roscio on 2010-02-19
Bummer.  I'm going to punt on this one.  I've tried hacking PAM a bit too, no luck.  Maybe if I had more time but time's getting short for this project.  I'll have to switch to USB-based scanners that present themselves as a keyboard device, instead of the old serial scanners.  It's the classic trade-off: time vs money.

---

