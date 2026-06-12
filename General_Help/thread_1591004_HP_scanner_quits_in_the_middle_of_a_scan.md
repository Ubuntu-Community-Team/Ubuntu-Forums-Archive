---
title: "HP scanner quits in the middle of a scan"
date: 2010-10-08
forum: General Help
---

### Post by 73ckn797 on 2010-10-08
Ubuntu 10.04 AMD Athlon 64 X2 Dual Core 4000+ 6Gib Ram.

HP Officejet J4580 All-in-One scanner quits in the middle of a scan, sometimes after a single page or 2 or 3 pages.  I have removed and reinstalled Hplip and all associated files for xsane. Xsane has to be force closed and then will not start-up and displays an error (see attached screen shot). The printer works perfectly. I can restart the computer and it will do the same thing. The scanner will, almost literally, come to a grinding halt.

Is there a configuration file that might need tweaking? Is there an issue with 10.04? The problem began since installing 10.04 and has really started messing up since one of the last updates. I have searched for any similar issues in the forums and using [http://crunchbang.org/ubuntu-search-engine/](http://crunchbang.org/ubuntu-search-engine/)

I rebooted into Windows XP and the scanner works as designed so I believe it to be a software issue with the HP driver or other necessary dependencies in Ubuntu.

---

### Post by sikander3786 on 2010-10-08
I am using Simple Scan with HP Deskjet F2120 All-in-One and it works pretty smooth.

Instead of drivers, configuration files, I'll put my money on Xsane. Why don't you try some other scanning software for time being and rule out the software possibility.

---

### Post by 73ckn797 on 2010-10-08
Purged xsane and the scanner pulled 2 pages with no problem. I had tried simple scan previously but that was before removing xsane. The only thing I need is auto save with progressive file naming. I scan multiple documents each day and find no preference for auto saving each scanned page.

Hplip also has option to scan but it looks like it is using simple scan.

---

### Post by 73ckn797 on 2010-10-13
Same problem with 10.10. I just might reinstall 9.10. It was working just fine for scanning. If that does not work it may be good bye Ubuntu. I have to have scanning capabilities.

---

### Post by 73ckn797 on 2010-10-14
My solution was to reinstall Ubuntu 9.10.

---

### Post by pcolamar on 2011-01-17
> **73ckn797 said:**
> Purged xsane and the scanner pulled 2 pages with no problem. I had tried simple scan previously but that was before removing xsane. The only thing I need is auto save with progressive file naming. I scan multiple documents each day and find no preference for auto saving each scanned page.

Hplip also has option to scan but it looks like it is using simple scan.

Hi 73ckn797,
  have you solved the autosave problem ?
I had a similar problem yesterday and I noticed that in the upright corner there is  a drop down menu where you can select several option, "SAVE" among them, instead of the default VIEW(xsane v0.996) .
That worked for me.

Regards

Palmer

---

