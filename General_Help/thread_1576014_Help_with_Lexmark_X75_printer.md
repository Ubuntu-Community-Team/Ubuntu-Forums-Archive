---
title: "Help with Lexmark X75 printer"
date: 2010-09-16
forum: General Help
---

### Post by AndrewGen on 2010-09-16
I've installed Ubuntu 10.04 on a family members computer and need help with the installation of their Lexmark X75 printer. 
 
Thanks in advance,
Andrew

---

### Post by anglican on 2010-09-17
> **AndrewGen said:**
> I've installed Ubuntu 10.04 on a family members computer and need help with the installation of their Lexmark X75 printer. 
 
Thanks in advance,
Andrew
I haven't got one to try, but according to [www.openprinting.org]("http://www.openprinting.org") this printer works "partially" - what that means you will hopefully find out! To install the driver:
```
1) wget http://home.online.no/%7Eenrio/lxx74-cups-0.8.4.2.tar.gz
2) tar xvfz lxx74-cups-0.8.4.2.tar.gz
3) cd lxx74-cups-0.8.4.2
4) sudo ./lxx74.install
5) sudo service cups restart
```you can then remove the file lxx74-cups-0.8.4.2.tar.gz and the directory lxx74-cups-0.8.4.2 if you want.
To install the printer:
```
1. Point browser to [http://localhost:631/admin](http://localhost:631/admin) (which requires that cupsd is running),
2. click on Add Printer
3. Pick a short name
Click &#8220;Continue&#8221;
4. Scroll down the devices list until you find &#8220;USB Printer 1&#8221;.
If the printer is connected, &#8220;Lexmark All In One&#8221; should appear next to the device. Then click &#8220;Continue&#8221;
5. Select vendor &#8220;LEXMARK&#8221;, and click &#8220;Continue&#8221;
6. Select model/driver &#8220;Lexmark All In One, 1.0 (en)&#8221;, and click &#8220;Continue&#8221;
```Print a test page and report back here what happened;)

H

---

### Post by AndrewGen on 2010-09-19
> **anglican said:**
> I haven't got one to try, but according to [www.openprinting.org]("http://www.openprinting.org/") this printer works "partially" - what that means you will hopefully find out! To install the driver:
```
1) wget http://home.online.no/%7Eenrio/lxx74-cups-0.8.4.2.tar.gz
2) tar xvfz lxx74-cups-0.8.4.2.tar.gz
3) cd lxx74-cups-0.8.4.2
4) sudo ./lxx74.install
5) sudo service cups restart
```you can then remove the file  lxx74-cups-0.8.4.2.tar.gz and the directory lxx74-cups-0.8.4.2 if you  want.
To install the printer:
```
1. Point browser to [http://localhost:631/admin](http://localhost:631/admin) (which requires that cupsd is running),
2. click on Add Printer
3. Pick a short name
Click “Continue”
4. Scroll down the devices list until you find “USB Printer 1”.
If the printer is connected, “Lexmark All In One” should appear next to the device. Then click “Continue”
5. Select vendor “LEXMARK”, and click “Continue”
6. Select model/driver “Lexmark All In One, 1.0 (en)”, and click  “Continue”
```Print a test page and report back here what happened:wink:

H

Thanks.

I'll try it soon and report back.

---

