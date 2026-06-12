---
title: "Converting .RPM to .DEB"
date: 2012-05-15
forum: General Help
---

### Post by Welly Wu on 2012-05-15
Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation MLC NAND FLASH X25-M 160 GB SSD running Ubuntu 12.04 64 bit Long Term Support. I also have a Tripp Lite AVR 120 VAC 8 AC outlet UPS with a USB 2.0 port. Tripp Lite has software downloads available for GNU/Linux which they call their Power Alert Local: [http://www.tripplite.com/en/support/downloads/index.cfm?txtArchive=0&txtLang=&txtOS=](http://www.tripplite.com/en/support/downloads/index.cfm?txtArchive=0&txtLang=&txtOS=). Unfortunately, they only offer .RPM files for Red Hat Fedora 8 and OpenSUSE 11. I am wondering if it is possible to convert a .RPM file to a .DEB file so that I can install it. Will I be able to use Tripp Lite's Power Alert Local software application on Ubuntu 12.04 64 bit LTS?

Please let me know if I should do this or not. Thank you.

---

### Post by mcduck on 2012-05-15
The "alien" tool will convert between .rpm and .deb packages, although there's no guarantee that the result will actually install without problems as different Linux distributions have more differences between them than just the package format. And you'll also have to manually track what dependencies the package has and install them first.

Anyway, if you are willing to give it a try, this command should do the trick:
```

alien packagename
```

---

### Post by Welly Wu on 2012-05-15
[http://ubuntuforums.org/showthread.php?t=1729232&highlight=convert+rpm+deb](http://ubuntuforums.org/showthread.php?t=1729232&highlight=convert+rpm+deb)

I just tried using the alien command and it does not work because I use Ubuntu 12.04 64 bit LTS. These .RPM files are 32 bit.

---

### Post by wilee-nilee on 2012-05-15
I would just be sure to check if what you're converting may already be available in a repo for Ubuntu. I see people coming on here on occasion and the IRC that are trying to do a conversion or asking about it on a specific app, that have not looked, and was available.

---

### Post by Welly Wu on 2012-05-15
I checked the Ubuntu Software Center. They don't have anything designed for my specific Tripp Lite AVR 120 VAC 8 AC outlet UPS because it is a newer model that uses USB 2.0.

---

### Post by Mark Phelps on 2012-05-15
I've personally used alien to convert rpms to debs (for the same reason), and in all the cases I tried, either the resulting debs did not work, or as already mentioned, I encountered dependency problems that prevented getting everything installed.

At best, alien only works some of the time.

---

### Post by bodhi.zazen on 2012-05-15
You are better off installing from source rather then converting a rpm.

If you can not find the source, best to extract the rpm (a rpm is an archive much like a .tar or .zip) , examine the contents, and install manually (cp ... ).

---

