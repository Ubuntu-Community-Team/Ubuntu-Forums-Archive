---
title: "running IE 6, 7 or 8 under wine"
date: 2010-08-31
forum: General Help
---

### Post by DavidG24 on 2010-08-31
Hi Guys,

was just wondering what packages are required to install IE 6,7 or 8 under wine?

Any help would be greatly appreciated,

David

---

### Post by ilovelinux33467 on 2010-08-31
Have a look at this:

[http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by DavidG24 on 2010-08-31
hey mate,

cheers for that - everything seem to be running well until it went to install the flash component at which time I received an error

The program rundll32.exe has encountered a serious problem and needs to close.  ...

This may be caused by a problem in the program or a deficiency in Wine . ... 

So I'm assuming that this package has to be installed first before I can install IE 6...digging through net now trying to sort this prob out.

Thanks again for your reference, much appreciated.

Regards,

David

---

### Post by Irony on 2010-08-31
From terminal run;
```
winetricks
```
Then find and tick internet explorer then in terminal do;
```
env WINEPREFIX="/home/yourusername/.wine" wine "C:\Program Files\Internet Explorer\iexplore.exe"
```
It should install automatically from microsoft.

Note flash is also in winetricks.

---

### Post by Kranix on 2010-08-31
Ummm...

For what do you need IE?!

---

### Post by Irony on 2010-08-31
> **Kranix said:**
> For what do you need IE?!
Let's see, for one thing the majority of people use IE therefore when testing webpages one needs to ensure compatibility with IE.

Any other stupid questions?

---

### Post by polardude1983 on 2010-08-31
Are you aware of [www.browsershots.org?](www.browsershots.org?)

---

