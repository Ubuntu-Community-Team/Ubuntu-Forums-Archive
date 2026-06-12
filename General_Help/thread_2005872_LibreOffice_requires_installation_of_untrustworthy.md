---
title: "LibreOffice requires installation of untrustworthy packages ?!"
date: 2012-06-18
forum: General Help
---

### Post by Ali_Barba on 2012-06-18
Hi guys,   I just wanted to add LibreOffice to my fresh **Ubuntu Studio 12.04 LTS** installation, using the Software center, but when I click install and enter my password, a message pops up which tells me that LibreOffice required the installation of untrustworthy packages, details as follows:      


> ca-certificates-java default-jre default-jre-headless hunspell-de-at hunspell-de-ch hunspell-de-de hunspell-en-ca hyphen-de hyphen-en-us icedtea-6-jre-cacao icedtea-6-jre-jamvm icedtea-netx icedtea-netx-common java-common libatk-wrapper-java libatk-wrapper-java-jni libcmis-0.2-0 libexttextcat-data libexttextcat0 libhsqldb-java libhyphen0 libmythes-1.2-0 libnss3-1d libreoffice libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-filter-mobiledev libreoffice-gnome libreoffice-gtk libreoffice-help-de libreoffice-help-en-gb libreoffice-help-en-us libreoffice-impress libreoffice-java-common libreoffice-l10n-de libreoffice-l10n-en-gb libreoffice-l10n-en-za libreoffice-math libreoffice-style-human libreoffice-style-tango libreoffice-writer libservlet2.5-java libstlport4.6ldbl libwps-0.2-2 libxerces2-java libxml-commons-external-java libxml-commons-resolver1.1-java myspell-en-au myspell-en-gb myspell-en-za mythes-de mythes-de-ch mythes-en-au mythes-en-us openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib openoffice.org-hyphenation python-uno ttf-dejavu tzdata-java uno-libs3 ure xfonts-mathml

---

### Post by Ali_Barba on 2012-06-18
So, what do you think of it ? I thought LibreOffice was one of the most widely used and trusted applications out there, so that seems very freaky to me.

---

### Post by kurt18947 on 2012-06-18
If you did a 'normal' 12.04 install, Libre Office should already be there, no need to install anything.

---

### Post by vasa1 on 2012-06-18
> **kurt18947 said:**
> If you did a 'normal' 12.04 install, Libre Office should already be there, no need to install anything.

Exactly. Something odd's going on!

---

### Post by Ali_Barba on 2012-06-18
> **vasa1 said:**
> Exactly. Something odd's going on!

Nothing odd there, it's Ubuntu Studio 12.04 LTS.  :) 

But the odd thing is that LibreOffice's packages are obviously judged as insecure or not trustworthy ... so what should I think of that ?

---

### Post by vasa1 on 2012-06-18
> **Ali_Barba said:**
> Nothing odd there, it's **Ubuntu Studio 12.04 LTS**.  :) ...
Why don't you edit your first post and include that information?

---

### Post by Ali_Barba on 2012-06-18
> **vasa1 said:**
> Why don't you edit your first post and include that information?

Done.

---

### Post by vasa1 on 2012-06-18
> **Ali_Barba said:**
> Nothing odd there, it's Ubuntu Studio 12.04 LTS.  :) 

But the odd thing is that LibreOffice's packages are obviously judged as insecure or not trustworthy ... so what should I think of that ?
My feeling is that there's a problem with Ubuntu Studio's Software Center. They just haven't taken LibreOffice into account.
I suggest you ask the mods, via the **Report Abuse** button, to move this thread to the Ubuntu Studio section ([http://ubuntuforums.org/forumdisplay.php?f=335](http://ubuntuforums.org/forumdisplay.php?f=335)) so that the right people get to see it.

---

### Post by vasa1 on 2012-06-18
Another thing is to see what happens when you try to install LibreOffice via Synaptic if you have Synaptic installed.

---

### Post by Ali_Barba on 2012-06-18
> **vasa1 said:**
> Another thing is to see what happens when you try to install LibreOffice via Synaptic if you have Synaptic installed.


Yes, I do have Synaptic installed. Just checked it out -- I get a similar warning there, it says that the software publisher could not be verified and that it was possibly malicious.  :|

I noticed that synaptic also offers OpenOffice - is that still current ? I thought OpenOffice had been succeeded by LibreOffice ? But the Software Center does not offer OpenOffice.

---

### Post by vasa1 on 2012-06-18
> **Ali_Barba said:**
> Yes, I do have Synaptic installed. Just checked it out -- I get a similar warning there, it says that the software publisher could not be verified and that it was possibly malicious.  :|

I noticed that synaptic also offers OpenOffice - is that still current ? I thought OpenOffice had been succeeded by LibreOffice ? But the Software Center does not offer OpenOffice.

I think the people at Ubuntu Studio will have to do some explaining (or a whole lot of people are using malicious software)!

Re. the second point, that has been going on for a while. OpenOffice is listed but, in reality, it's LibreOffice. I understand that the powers that be are aware of this.

If you want OpenOffice, now with the Apache prefix, you may have to get it "direct": [http://www.openoffice.org/download/index.html](http://www.openoffice.org/download/index.html)

---

