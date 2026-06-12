---
title: "Errors when installing 10.10"
date: 2011-05-26
forum: General Help
---

### Post by dustcap on 2011-05-26
After I installed 10.10 there was a huge amount of Error messages come up before the system automatically restarted. Most were like this :
 
Error [1150.843478] end_request: I/O error, dev sro, sector 529005
 
THere were at least 2-3 pages of them with various numbers.
 
Is my disk buggered or my system too small?  I have a Compaq Evo D510 sff.

---

### Post by wildmanne39 on 2011-05-27
> **dustcap said:**
> After I installed 10.10 there was a huge amount of Error messages come up before the system automatically restarted. Most were like this :
 
Error [1150.843478] end_request: I/O error, dev sro, sector 529005
 
THere were at least 2-3 pages of them with various numbers.
 
Is my disk buggered or my system too small?  I have a Compaq Evo D510 sff.
Hi, when it boots there is a lot of stuff that shows up on the screen are you sure it was all errors. Is your system booting and working just fine, if so don't worry about it.

---

### Post by Rubi1200 on 2011-05-27
Hi and welcome to the forums dustcap :-)

From the Maverick release notes:

> 
[LIST]
[*]**I/O error after CD is ejected at end of install.**  In some cases, ejecting the CD at the end of installation will leave errors on the screen such as:
[/LIST]

end_request: I/O error, dev sr0, sector 437628

these  error messages indicate that the system is still trying to access some  files on the CD, and are harmless except that they obscure the message  asking the user to press Enter to reboot.  You can safely remove the CD  from the tray and press Enter at this point to reboot to your new Ubuntu  system. 
[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues]("https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes#Known%20Issues")

As wildmanne39 pointed out, if you can boot normally there is nothing to be concerned about.

---

