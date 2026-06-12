---
title: "OpenOffice.org Presentation 3.2.0 Keeps Crashing"
date: 2012-03-16
forum: General Help
---

### Post by gopaleen on 2012-03-16
Hi, I've got a problem with Presentation. It crashes while I'm working. It just freezes spontaneously and then I have to manually shut down. It's killing me. I've tried uninstalling and installing again but no luck.

I'm running OpenOffice 3.2.0 on a Lucid 10.04 LTS with an Intel core i3-2310M. Thanks!

---

### Post by ajgreeny on 2012-03-16
> **gopaleen said:**
> Hi, I've got a problem with Presentation. It crashes while I'm working. It just freezes spontaneously and then I have to manually shut down. It's killing me. I've tried uninstalling and installing again but no luck.

I'm running OpenOffice 3.2.0 on a Lucid 10.04 LTS with an Intel core i3-2310M. Thanks!
Try renaming the hidden folder **~/.openoffice.org** in your home, where all your personal OOo configuration is held and see if the application runs OK.  It will make a new folder of that name when you open OOo, and you will then need to make any changes you have made in the configuration again, but that should not take too long.

Alternatively you could try using Libreoffice from the ppa instead with command ```
sudo add-apt-repository ppa:libreoffice/ppa
``` and then refresh the software sources and install libreoffice.  That will remove OOo from your system and install LO in its place.  I have been using it for a while now with no problems, and I think it is faster, has better MS Office compatibility, and it's got to version 3.5.0.

---

### Post by pqwoerituytrueiwoq on 2012-03-16
what package did you reinstall there is a meta package ([FONT=Courier New]openoffice.org[/FONT]) that does nothing
the other day my open office was crashing as soon as you try to open it
reinstalling [FONT=Courier New]openoffice.org-core[/FONT] fixed it for me
i had looked in my log file viewer (since the terminal told me nothing) and found a error message something about segmentation fault in [FONT=Courier New]libsfxlx.so[/FONT] which is in the installed file list of [FONT=Courier New]openoffice.org-core[/FONT] so i reinstalled that package ant it now opens again

if only presentation is crashing take a look at [FONT=Courier New]openoffice.org-impress[/FONT]

of course if it works on your guest account the problem is what ajgreeny said about the [FONT=Courier New]~/.openoffice.org[/FONT] folder

---

### Post by gopaleen on 2012-03-16
Thanks guys. I tried deleting the .openoffice.org folder but presentation was still crashing. Gonna try Libreoffice instead. Thanks!

---

