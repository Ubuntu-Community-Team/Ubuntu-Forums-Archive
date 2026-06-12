---
title: "Which antivirus i should use for my system?"
date: 2010-02-14
forum: General Help
---

### Post by karthick87 on 2010-02-14
Which antivirus i should use for my system?I am using clamav but i think this is not the right one,coz it was not not detecting any viruses..

---

### Post by spiky001 on 2010-02-14
hi do you now you have viruses then, it,s not very likely in linux?

---

### Post by ironclaw on 2010-02-14
> **getyourkarthick said:**
> Which antivirus i should use for my system?I am using clamav but i think this is not the right one,coz it was not not detecting any viruses..
You might want to take a look at [this]("http://ubuntuforums.org/showthread.php?t=510812") excellent post on Ubuntu security by bodhi.zazen.

Relevant section:
> Reasons **AGAINST** antivirus on Ubuntu:
[LIST=1]
[*]They scan primarily for Windows viruses.
[*]There is a high rate of false positives.
[*]Isolation/inoculation is poor.
[*]And currently there are no known active Linux viruses (so there is essentially nothing to detect).
[/LIST]

Reasons **FOR** antivirus on Ubuntu:
[LIST]
[*]You are running a file or mail server with Windows clients.
[*]You wish to scan files before transferring them, by email, flash drive, etc., to a Windows machine.
[/LIST]
If you're asking for a linux based antivirus client to scan a Windows partition - [AVG]("http://free.avg.com/us-en/download?prd=afl") has a good text based and free antivirus program for Linux. I prefer using it to clamav.

---

### Post by karthick87 on 2010-02-14
I used to scan USB drives using clamav but it doesnot detect any viruses..When i plug the same USB drives in windows and scan it using the Norton Antivirus it detects some viruses..So is there any efficient antivirus program in Linux to scan Windows Partition and USB drives..???

---

### Post by MrNatewood on 2010-02-14
If you are looking for a professional anti-virus like norton for linux i would recommend Nod32:
[http://www.eset.com/products/linux.php](http://www.eset.com/products/linux.php)

If you are looking for something free(as in beer) there is AVG free edition:
[http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.deb](http://download.avgfree.com/filedir/inst/avg85flx-r732-a3168.i386.deb)
and Avast:
[http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb](http://files.avast.com/files/linux/avast4workstation_1.3.0-2_i386.deb)

If you are looking for an open-source AV than you probably can't get a better one than ClamAV which you already have.

As mentioned above, this would only be useful to find windows viruses, as there are currently no active linux viruses.

---

