---
title: "Problem with ati amd proprietary fglrx graphics driver"
date: 2010-10-03
forum: General Help
---

### Post by ultimatebuster on 2010-10-03
I installed Ubuntu 10.10 via wubi, installed the ati amd proprietary fglrx graphics driver as prompted, and lost GUI.

Under command line, I tried to do startx, however I got fatal server error: no screens found

Now I reinstalled Ubuntu, and I'm not sure if I should install that again.

Also I have a switchable graphics (ati hd5650 and intel 4500, not too sure about the intel one's model number), can i activate that?

Also I'm having problems with CPU temperatures. CPU temperature is almost always at 77C. Under windows that number is usually only around 50, if not 40 when idling or browsing.

---

### Post by instantepiphany on 2010-10-05
Do you by any chance have a hp dv6?? I do, and it has the 5650, and the intel. I have the same problem as you. Just don't install the drivers, it is using the intel by default and for some reason asking you to install drivers for the ati... Just leave it, its not important for web browsing, watching movies etc.

---

### Post by frank.s on 2010-10-05
I've had the exact same problem, but I found out that you can simply write 

```
sudo apt-get remove fglrx
```

This worked for me. If it doesn't work, then try

```
sudo apt-get remove xorg-driver-fglrx
```

and restart.

There's (fortunately) no need to do a complete Ubuntu reinstall :cool:

---

### Post by ultimatebuster on 2010-10-10
Mine is a Lenovo Y460. Also another problem is the two finger scrolling. Doesn't work for me even with gsynapics.

and does that mean there's no driver for ati? Only intel?

---

### Post by ultimatebuster on 2010-10-11
*sigh*
This probably means i have to go back to win again.

---

### Post by alphacrucis2 on 2010-10-11
> **ultimatebuster said:**
> *sigh*
This probably means i have to go back to win again.


After installing the ATI blob always do this as a matter of course before restarting:


```
sudo aticonfig --initial -f
```

---

### Post by httpitis on 2010-10-18
I know this does not solve the problem with switchable graphics but to get the proprietary drivers working, change bios setting "Graphic Mode" from "Switchable" to "Discreet".

I have verified that the proprietary AT drivers to work (instead of getting a black screen) in Ubuntu 10.10 on a Acer TimelineX 3820TG.

Eagerly awaiting a solution to the problem with switchable graphics.

---

### Post by ultimatebuster on 2010-10-18
Yeah I don't want to set to discrete as I want that switchable capability under windows when I do use it.

---

### Post by TBABill on 2010-10-18
Why go back to Windows when you can just go back to 10.04? Or did fglrx not work there for you either?

---

### Post by sendblink23 on 2010-10-18
> **ultimatebuster said:**
> Yeah I don't want to set to discrete as I want that switchable capability under windows when I do use it.

Why would you switch on windows to Intel GFX? Isn't that ATI way better than it?

---

### Post by redmorning on 2010-10-31
> **httpitis said:**
> I know this does not solve the problem with switchable graphics but to get the proprietary drivers working, change bios setting "Graphic Mode" from "Switchable" to "Discreet".

I have verified that the proprietary AT drivers to work (instead of getting a black screen) in Ubuntu 10.10 on a Acer TimelineX 3820TG.

Eagerly awaiting a solution to the problem with switchable graphics.

hi,

i have a acer 3820 tg and l had that problem too when i first install the "ati/amd proprietary fglrx graphic driver". know my questions;
-With intel i have max 90 minutes battery life but in windows i have more than 5 hours. I think it is related to graphic card. If i change my "switchable graphic card" option from the bios and install amd/ati than how long battery life will i have? because one of the reason that i choose this pc was its battery life (@ httpitis)
-Does this action really works or can i loose my login again?
-What will be the differences if i use ati everytime in place of intel?

Thanks.

---

### Post by redmorning on 2010-11-11
i found the solution,
Thanks to f4lkon.

[http://ubuntuforums.org/showthread.php?t=1613547]("http://ubuntuforums.org/showthread.php?t=1613547")

cheers!

---

