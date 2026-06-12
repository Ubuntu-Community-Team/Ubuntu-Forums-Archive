---
title: "Adobe connect featurs don't work for me as a audience"
date: 2010-07-05
forum: General Help
---

### Post by 1geeky on 2010-07-05
Hi,
1. When I contribute in a virtual class presented by Adobe connect pro, (with lucid & firefox 3.6.6) the buttons of adobe connect (e.g play, pause, view advanced options, seeking between different times of class) don't work.
2. Also Persian character seems separated as shown in attached image.

What are solutions? :-k

Thanks in advance ;)

---

### Post by lovinglinux on 2010-07-05
I never used Adobe connect, but with flash this usually happens when you are using the 32bit plugin on a 64bit system.

To fix that you need to edit the npviewer file. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by 1geeky on 2010-07-06
Thanks a lot :)
the controls work now.

1.so why it doesn't install 64-bit version from first? (or how may I install 64-bit at Beginning?)
What does this code do exactly?  :

> export GDK_NATIVE_WINDOWS=1does it convert 32 to 64-bit one ?


2.But about separate characters, I think it caused by lack of proper fonts. how could i find the name of required fonts?

Thanks again

---

### Post by lovinglinux on 2010-07-06
> **1geeky said:**
> 1.so why it doesn't install 64-bit version from first? (or how may I install 64-bit at Beginning?)


The 64bit is no longer supported by Adobe. If you search the forum you will be able to find the direct link and install it manually, but I don't recommend, since it has a critical vulnerability that could allow full remote control of your machine.

> **1geeky said:**
> What does this code do exactly?

I have no idea. I just know it works :)

> **1geeky said:**
> does it convert 32 to 64-bit one ?

No.

---

### Post by 1geeky on 2010-07-06
Thank you for your attention :)

and I'm seeking for the secondary question; other friends :
> 2.But about separate characters, I think it caused by lack of proper  fonts. how could i find the name of required fonts?


---

