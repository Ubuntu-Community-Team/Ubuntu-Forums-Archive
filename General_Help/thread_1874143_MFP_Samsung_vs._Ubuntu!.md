---
title: "MFP Samsung vs. Ubuntu!"
date: 2011-11-02
forum: General Help
---

### Post by 127276 on 2011-11-02
Hello brothers!
Today I bought a Samsung SCX-3205
Climbed to the official website to look for drivers
[http://www.samsung.com/uk/support/detail/supportPrdDetail.do?prd_mdl_cd=SCX-3205%2FSEE&srchword=%3Cb%3ESCX%3C%2Fb%3E-%3Cb%3E3205%3C%2Fb%3E](http://www.samsung.com/uk/support/detail/supportPrdDetail.do?prd_mdl_cd=SCX-3205%2FSEE&srchword=%3Cb%3ESCX%3C%2Fb%3E-%3Cb%3E3205%3C%2Fb%3E)
For a printer is
For the scanner - there is no

Google has used to solve the problem
found [http://www.bchemnet.com/suldr/scanning.html](http://www.bchemnet.com/suldr/scanning.html) - does not work! there is no model SCX-3205

I was very angry and began to think what to do - 8:00 Google has scanned and tried and tried and tried!

I got the idea to try to download the driver for your scanner from any other laser MFP Samsung.
I went to a page with the MFPs and began to open each one, looking for drivers for the scanner [http://www.samsung.com/uk/consumer/print-solutions/print-solutions/mono-multi-function-products/?gnb=Y](http://www.samsung.com/uk/consumer/print-solutions/print-solutions/mono-multi-function-products/?gnb=Y)

See what the 4ell is going on !!!!!! 1

For each device has a driver for the scanner and for windows and apple, but only for the Linux driver for the printer and two lousy program's print!

I called the call center samsung and asked them about drivers for the scanner.
I was told that the samsung does not support Linux and Linux problems torment yourself!

In connection with the situation I have 3 questions.
I would be grateful if you let me answer them.

1) Is there a scanner driver for SCX-3205?
2) If the driver is not, in any community can turn to their writing? After all, no one at Samsung MFP are no drivers for the scanner ...
3) Maybe there are more such victims from Samsung? Let us arrange a flashmob and Samsung will give a kick to the Internet, because he ignores us! what do you think?](*,)

---

### Post by gsmanners on 2011-11-02
Hello, and welcome to the Ubuntu Forums. :D

Linux in general doesn't need special drivers. Sometimes, you see weird hardware issues like video cards that need drivers, but they are an unusual case. For scanners and printers, they generally either work or they don't. I usually check out Linux Hardware sites first before shopping.

You seem to have similar hardware to that reported here:

[http://linuxhcl.com/browse/product?id=7442](http://linuxhcl.com/browse/product?id=7442)
[http://linuxhcl.com/browse/product?id=7382](http://linuxhcl.com/browse/product?id=7382)

Seems to be hit and miss. Good luck.

---

### Post by WorMzy on 2011-11-02
SANE handles scanner drivers.

[http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=]("http://www.sane-project.org/cgi-bin/driver.pl?manu=samsung&model=&bus=any&v=&p=")

I don't see any mention of the model in question. You may be out of luck.

---

### Post by kapouer on 2012-01-22
Scanning with scx3205 is just a matter of configuring SANE :
in /etc/sane.d/xerox_mfp.conf :
Either use tcp through ethernet/wifi connection :
# tcp printer.localdomain 9400
tcp 192.168.0.88 9400

Or usb :
usb 0x04e8 0x3441

Note that scanning through tcp is *slow*, while usb is *fast*.

You might have to restart saned or simply reboot.

---

