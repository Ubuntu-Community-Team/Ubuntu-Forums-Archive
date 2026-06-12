---
title: "Ugly Fonts in Java Apps"
date: 2010-07-27
forum: General Help
---

### Post by pinguino99 on 2010-07-27
Hi all,
I moved from 8.10 to 10.04.
I noticed that now Java apps  (SAP GUI, for example) have ugly fonts. In 8.10 it was ok.
It seems an antialias thing, but i am not sure.
Of course i installed the sun-java6-fonts packages, but still fonts are not clean and clear. Look at the attachments.
Thanks to all
Ernesto

---

### Post by lykeion on 2010-07-27
Have you tried this:
_[http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java](http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java)_

---

### Post by pinguino99 on 2010-07-27
> **lykeion said:**
> Have you tried this:
_[http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java](http://hedayatvk.wordpress.com/2010/02/26/antialiasing-and-java)_

Yes, thanks a lot, i already tried adding 
export _JAVA_OPTIONS="-Dawt.useSystemAAFontSettings=on"
but did not change.
Maybe it's an issue-specific of the application (SAP GUI)
anyway it's strange that in ubuntu 8.10 it worked.
Maybe java needs more fonts, i don't know.
Thanks anyway
Regards

---

