---
title: "Newest LibreOffice does not open encrypted files"
date: 2012-02-24
forum: General Help
---

### Post by The Bright Side on 2012-02-24
Hey guys, is anybody else having problems opening their encrypted files since the latest LibreOffice update? Both Calc and Writer reject my passwords and won't open my files anymore. It works in OpenOffice, and it also works in the latest LibreOffice under Windows.

Does anybody know a workaround?

---

### Post by The Cog on 2012-02-24
I know that in the release notes for LO 3.5, they say they changed the way encryption was done. The very latest 3.4 is able to open the new format though, for backward compatibility. What versions of LO are you using?

---

### Post by The Bright Side on 2012-02-25
It's 3.4.5 under Ubuntu 11.10 and 3.5 under Windows (at home on my Win7 partition, and under Windows XP at work).

My files open properly at work and at home under Win7, but 3.4.5 under Ubuntu rejects the passwords. Also, I was surprised just now to see it was still 3.4.5 in Ubuntu - thought the PPA had already been updated. So perhaps it's just a matter of waiting for 3.5 to arrive here.

Thanks!

---

### Post by The Cog on 2012-02-25
I found the reference. This page: 
[http://www.libreoffice.org/download/3-5-new-features-and-fixes/](http://www.libreoffice.org/download/3-5-new-features-and-fixes/)
contains the following text:
> In LibreOffice 3.5, a different, more often used encryption (AES) will be introduced to replace the previously used one (Blowfish).In consequence, files encrypted with LibreOffice 3.5 can not be opened by LibreOffice 3.4.4 and earlier. LibreOffice 3.4.5 enables you to open those files. However, on saving again in LibreOffice 3.4.5, the old encryption will be used. Files with the old encryption of course can be used in LibreOffice 3.5.0
According to that, 3.4.5 should be able to read the new encryption. 

It is possible to install the download from the LibreOffice site if you don't want to wait for the PPA.

---

### Post by The Bright Side on 2012-02-26
Thanks man. I'll work around it for the time being (inconvenience, but not too bad) and wait for the PPA. Curious to see if that fixes it!

---

