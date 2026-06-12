---
title: "How To: LibreOffice Language Pack Installation"
date: 2010-10-18
forum: General Help
---

### Post by scouser73 on 2010-10-18
This is for x86 only.

1 - Visit [http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/](http://download.documentfoundation.org/libreoffice/testing/3.3.0-beta2/deb/x86/)

2 - Find the Language pack for your locale and download

3 - Save to your desktop

4 - **Right click** and select **Extract Here**

5 - Rename the extracted folder to **libreoffice**

6 - Open Terminal and copy & paste the following commands:

> cd Desktop

> sudo dpkg -i libreoffice/DEBS/*.deb

You have now installed the LibreOffice Language Pack for your locale.

---

### Post by slartidan on 2012-10-21
Alternative way of installing open office language packs:
[LIST=1]
[*]Open Ubuntu Software Center
[*]Enter "LibreOffice german" or similar in search box (upper right)
[*]Select "Office productivity suite - German language package" or similar from list
[*]Click on "Install" in the selected row
[*]Restart LibreOffice
[*]Choose language in tools->options...->language settings->languages
[/LIST]

---

