---
title: "HP Officejet 8500 Pro"
date: 2010-06-16
forum: General Help
---

### Post by c5vetter on 2010-06-16
Not sure if this is the place to post or not, but am really frustrated in trying to figure out how to get the SCAN function to work in this ALL-in-ONE printer!

Note it does print, so do have HPLIP and CUPS working fine between the laptop running Ubuntu 10.04 and the printer connected via USB

How do I setup all the other features of this printer!? Obviously, if it was Windows or MAC OS, you just plug the CD in and you use the configuration files - but, nothing like that for Linux!!!!!!

---

### Post by dino99 on 2010-06-16
menu: apps graphic simple scan

---

### Post by phubert28 on 2010-11-17
xsane does not see MY network-attached HP Officejet 8400 Pro's scanner.

Like c5vetter, printing is setup FINE but I don't see any reference to the Officejet 8500 on the sane project website.

I suppose I could get a USB cable and ALSO attach the printer via USB, tho it doesn't LOOK  as though SANE is setup to see multifunctions!

**

Tried it with a USB cable - no dice.

---

### Post by sites on 2012-06-07
Risen from the grave.  No reason to start a new thread on this.

I have experienced off & on success with this printer via wireless connection.  It always installs and prints, but on some *buntu variants the scanner is detected and works without issue.  On other versions, such as Kubuntu 12.04, the scanner isn't recognized.  I've installed skanlite, xsane, libsane...etc... to no avail.  Needing a little help.

---

### Post by agillator on 2012-06-07
I'll bet you are using Ubuntu's version of HPLIP. Therein lies your problem. I don't know why. So, go to HP and download their HPLIP. Remove the current one. I recommend a purge. Then install HP's version. Everyone I have recommended this to said it fixed their problem. If you need more details, check [I]  [http://ubuntuforums.org/showthread.php?t=1898845](http://ubuntuforums.org/showthread.php?t=1898845), message #9. 
[/I]

---

