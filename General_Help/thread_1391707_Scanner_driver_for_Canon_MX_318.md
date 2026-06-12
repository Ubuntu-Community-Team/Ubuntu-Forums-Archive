---
title: "Scanner driver for Canon MX 318"
date: 2010-01-27
forum: General Help
---

### Post by Thanh-BKK on 2010-01-27
Hi.

I urgently need to get this working.... mission-critical, this is the main machine at my office. I have just kicked Windows off and installed trusty Ubuntu, however i can't get the scanner to work!!

Model is Canon (Pixma) MX318 all-in-one (printer/scanner/fax). It PRINTS just fine however sane won't detect a scanner at all and "sudo sane-find-scanner" gives me this:

found USB scanner (vendor=0x04a9 [Canon], product=0x1728 [MX310 series]) at libusb:002:002

What would be the next step to get this hammered into sane so i can scan..? 

And no, "buy a new scanner/printer" is NOT an option...... "back to Windows" it would be then, and THAT i try to prevent at all costs. 

Kind regards......

Thanh

---

### Post by Thanh-BKK on 2010-01-28
Hello.  

After some 10 hours of googling i managed to solve this issue. According to these pages:

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=&bus=usb&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=&bus=usb&v=&p=)

[http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

my printer/scanner is supported in Sane backends version 1.0.20 which was released in May 2009, however the available version in the repository is 1.0.19.

So i downloaded the new version as a .deb file from here:

[http://ftp.debian.org/debian/pool/main/s/sane-backends/](http://ftp.debian.org/debian/pool/main/s/sane-backends/)

(in my case it was the libsane_1.0.20-13_i386.deb) and then tried to install it using Synaptics.

NO! Unsatisfied dependencies. But those are not required to make it work, so i did it with this command:

sudo dpkg -i libsane_1.0.20-13_i386.deb --ignore-depends

and it installed just fine. 

NOW i can scan perfectly with Xsane, Scanner Utility and gscan2pdf.

Now YOU can save yourself all those hours on Google and just do what i did, this supports a whole lot of Canon all-in-one devices.

Best regards......

Thanh

---

### Post by Thanh-BKK on 2010-01-28
Aaaargh.

Now i have a different problem related to this one!! Every time i try to install something with Synaptics, Synaptics complains about the above mentioned package, stating it is "broken". And then it wants to remove it and a whole lot of others along with it!!

And it will NOT let me install ANYTHING before it has removed those!!

And apparently there is no way to tell Synaptics to leave that lone package alone........

So now i can either scan or install, but not both. This kind of sucks.

Thanh

---

### Post by mcbelisle on 2010-01-28
There is a ppa for sane-backends

[https://launchpad.net/~matttbe/+archive/ppa](https://launchpad.net/~matttbe/+archive/ppa)

install that and use that. for the other thing, your computer will prompt you to remove what you need to remove

---

### Post by Thanh-BKK on 2010-01-28
Hi.

Thanks for the reply. Although - how exactly would i do that?? I added that ppa to my sources list and authenticated it, did the sudo apt-get update - and still don't see any new version of sane-backends.

According to that site there are versions for Karmic and Lucid - which won't help me as i am on Jaunty.

Or do you by any chance know HOW to install them from that ppa..??

Best regards.....

Thanh

---

### Post by Thanh-BKK on 2010-01-28
Ok, i'm back.

Now it IS solved - the long and rocky way. Installed all dependencies MANUALLY by downloading each one as a deb file and installing them one-by-one until i finally could hammer that libsane in there without complaints.... and now everything works like charm.

Best regards.....

Thanh

---

