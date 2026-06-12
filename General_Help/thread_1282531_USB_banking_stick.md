---
title: "USB banking stick"
date: 2009-10-04
forum: General Help
---

### Post by borobudur on 2009-10-04
Hi, 
I'm using a USB stick to do online banking. With Ubuntu 8.04 it worked just fine but since I upgraded to 8.10 I get the message that 

MidUpdate Error: locale '' can not be set

Any idea what that locale is?

---

### Post by cariboo on 2009-10-04
Locale is where you are located, eg: time zone and character set. For more info, open a terminal and type:

```
man locale
```

You may be able to edit /etc/default/locale, to set it to the correct character set.

---

### Post by borobudur on 2009-10-05
The difference is that I changed from german to english. Now there is the variable LANGUAGE missing. I added it but that did help. 

I also checked the permissions. These are the same like in the old system.

The midupdate is a program on the usb stick. This program wants to do something with locale, but it can't.

---

### Post by borobudur on 2009-10-10
Works again! I had to install the necessary languages.
Thanks!

---

