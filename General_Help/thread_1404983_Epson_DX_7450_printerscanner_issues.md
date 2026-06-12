---
title: "Epson DX 7450 printer/scanner issues"
date: 2010-02-12
forum: General Help
---

### Post by mpcjm on 2010-02-12
Morning,

I am not sure if this is the right place to post this, but I recently changed from vista to ubuntu, and my printer does not seem to be recognised by ubuntu.


I followed some of the other posts but they are all for previous versions of ubuntu and I cant seem to be able to get them to work.

When I press print I get the following message:  Error while printing

I try accessing the default printer through System>preferences and I get the following message:  CUPS server error - the CUPS scheduler is not running

if anyone has any ideas on hoe to fix this please share

thanking you in advance

I am running Karmic 64bit on a Toshiba L40-16D

---

### Post by Techsnap on 2010-02-12
Did your printer work before? Have you tried:

```
sudo /etc/init.d/cups restart
```

---

### Post by mpcjm on 2010-02-12
Thank you that sorted it

:{)

---

### Post by Techsnap on 2010-02-12
You're Welcome :)

---

### Post by mpcjm on 2010-02-13
After restarting the machine the printer did not work again,  I have to run the code every time, i there any shortcut to doing this, or a work around?

> **Techsnap said:**
> Did your printer work before? Have you tried:

```
sudo /etc/init.d/cups restart
```

---

### Post by Techsnap on 2010-02-14
Install the boot up manager:

```
sudo apt-get install bum
```

And check to make sure the CUPS service is enabled on bootup. CUPS in the Common Unix Printing system required for printing.

---

### Post by mpcjm on 2010-02-14
I ran bum, and found that the cups service is activated for startup,  is there another thing I can do???

Cheers

:{)

---

