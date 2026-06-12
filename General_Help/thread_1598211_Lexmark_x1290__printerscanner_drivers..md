---
title: "Lexmark x1290  printer/scanner drivers."
date: 2010-10-16
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-10-16
Where can i locate this? i have installed cups and the daemon is running, also the device is showing up with dmesg, i just cannot print.

all i can find on the web are seriously out of date posts or broken links.




i have also checked: [http://www.openprinting.org/printers](http://www.openprinting.org/printers) but it doesn't even list the x1290 anymore.

i am running Lucid, Kernel: 2.6.32-25



EDIT: on further digging i found this [http://support.lexmark.com/index?page=content&id=OS4&locale=en&userlocale=EN_UK](http://support.lexmark.com/index?page=content&id=OS4&locale=en&userlocale=EN_UK) but, the x1290 drivers are not listed.
also here are the windows drivers [http://support.lexmark.com/index?locale=en&segment=SUPPORT&userlocale=EN_UK&question=x1290&productCode=LEXMARK_X1290&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X1290&searchid=1287236384600#2](http://support.lexmark.com/index?locale=en&segment=SUPPORT&userlocale=EN_UK&question=x1290&productCode=LEXMARK_X1290&page=answers&detectedProductFacet=CMS-CATEGORY_REF.LEXMARK.PRODUCTS.ALLINONE.LEXMARK_X1290&searchid=1287236384600#2)  is there anyway to get them working under linux?


thanks.

---

### Post by NiGhtMarEs0nWax on 2010-10-16
apparently the z600 drivers work for the x1290 and other models.

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/LexmarkPrinters)

libstdc++5 is also required and can be installed alongside libstdc++6 afaik.
also, if you don't have the printer configuration app installed in your administration menu, you need to install 'system-config-printer-gnome,' install libstdc++5 then the drivers; then proceed.

i haven't tested it fully, but for what i have tried, it seemed to work ok.  Just though i'd post a fix.

---

