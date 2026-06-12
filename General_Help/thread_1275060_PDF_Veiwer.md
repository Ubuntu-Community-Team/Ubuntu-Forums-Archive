---
title: "PDF Veiwer"
date: 2009-09-25
forum: General Help
---

### Post by cbaxtermusic on 2009-09-25
Hi all im kind of in a jam with PDF veiwers, im currently reading up on scripting and programing as well as other PDF formated documents. these files happen to be pretty lengthy and when i close them out i would hope to be directed to the same reading positions, is there an way to do that or is that feature available in any of the PDF veiwers out there? pleeeeeeeeeasssssseeee heeeeeeeelllllpppppp!!!!!!!!!!!!!!!!!

---

### Post by MelDJ on 2009-09-25
kpdf will do that by default. you can get it from add/remove

---

### Post by mthalis on 2009-09-25
Try this
[http://ubuntuguide.net/install-adobe-reader-on-ubuntu-904](http://ubuntuguide.net/install-adobe-reader-on-ubuntu-904)

---

### Post by NightwishFan on 2009-09-25
The default viewer in Ubuntu Desktop, Evince does that. As well as Okular from KDE I am sure.

---

### Post by TrakerJon on 2009-09-25
> **cbaxtermusic said:**
> Hi all im kind of in a jam with PDF veiwers, im currently reading up on scripting and programing as well as other PDF formated documents. these files happen to be pretty lengthy and when i close them out i would hope to be directed to the same reading positions, is there an way to do that or is that feature available in any of the PDF veiwers out there? pleeeeeeeeeasssssseeee heeeeeeeelllllpppppp!!!!!!!!!!!!!!!!!


Start by going to System > select Administration > select Software Sources > Check the all the boxes under the Ubuntu Software, Thrird-Party Software and Updates tabs > Close and Reload

Do the following from a terminal window:

**sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list**

**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**

**sudo apt-get install acroread acroread-fonts**

You now have Acrobat Reader, enjoy!

---

### Post by credobyte on 2009-09-25
> **TrakerJon said:**
> Start by going to System > select Administration > select Software Sources > Check the first four boxes under the Ubuntu Software and Updates tabs > Close and Reload

Do the following from a terminal window:

**sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list**

**sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update**

**sudo apt-get install acroread acroread-fonts**

You now have Acrobat Reader, enjoy!

And for 32bit version, enable Partner repository ( Mediabuntu offers only 64bit version ).

---

