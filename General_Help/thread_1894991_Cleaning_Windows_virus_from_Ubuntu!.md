---
title: "Cleaning Windows virus from Ubuntu?!?"
date: 2011-12-13
forum: General Help
---

### Post by selfx on 2011-12-13
Hi there!
I'm looking for help for the following problem:
On my laptop got Windows XP and Ubuntu 10.04.3 installed on different partitions.
Recently I've catch "metropolitain police ukash virus" that locks my Windows 
immediately after logging in and unfortunately can't start in safe mod with command prompt, to clean the registry.
Is it possible to fix this problem from Ubuntu?!?
Already install "BitDefender Antivirus Scanner for Unices" on Ubuntu, but didn't help.
Thanks

---

### Post by qyot27 on 2011-12-13
> **selfx said:**
> Hi there!
I'm looking for help for the following problem:
On my laptop got Windows XP and Ubuntu 10.04.3 installed on different partitions.
Recently I've catch "metropolitain police ukash virus" that locks my Windows 
immediately after logging in and unfortunately can't start in safe mod with command prompt, to clean the registry.
Is it possible to fix this problem from Ubuntu?!?
Already install "BitDefender Antivirus Scanner for Unices" on Ubuntu, but didn't help.
Thanks
Delete the contents of C:\Documents and Settings\Username\Local Settings\Temp

Scan with Avast for Linux

---

### Post by Mark Phelps on 2011-12-14
IF you've got a CD/DVD device in your PC, you should consider going to the Kaspersky site, downloading and burning the free Kasperky Rescue CD image, booting from that, and having that clean Windows.

Avira also provides a free AV download disk.

These are Windows apps, but ironically, the CD boots from Linux to do the scanning -- thus preventing Windows malware from running.

---

### Post by haqking on 2011-12-14
> **Mark Phelps said:**
> IF you've got a CD/DVD device in your PC, you should consider going to the Kaspersky site, downloading and burning the free Kasperky Rescue CD image, booting from that, and having that clean Windows.

Avira also provides a free AV download disk.

These are Windows apps, but ironically, the CD boots from Linux to do the scanning -- thus preventing Windows malware from running.

+1

[http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable/](http://rescuedisk.kaspersky-labs.com/rescuedisk/updatable/)

---

### Post by northd_tech on 2011-12-14
> **qyot27 said:**
> Delete the contents of C:\Documents and Settings\Username\Local Settings\Temp

Scan with Avast for Linux

selfx can find a link to Avast 1.4.0 for Linux (and the necessary Ubuntu systems fix) here:  

[http://ubuntuforums.org/showthread.php?t=1867564](http://ubuntuforums.org/showthread.php?t=1867564)   

[http://forum.avast.com/index.php?topic=45237.0](http://forum.avast.com/index.php?topic=45237.0)

---

