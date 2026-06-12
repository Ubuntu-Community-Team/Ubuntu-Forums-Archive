---
title: "Need default configuration for a Libreoffice file"
date: 2011-03-28
forum: General Help
---

### Post by steve161 on 2011-03-28
Hi all:

I would appreciate it if someone could post the default configuration for this particular file:

usr/lib/libreoffice/program/sofficerc

It should be the default on your system if you did not change the splash screen.  

Thanks in advance.

---

### Post by 5149.5 on 2011-03-29
My install is in /opt but here is the contents of that file:

[Bootstrap]
HideEula=1
Logo=1
NativeProgress=true
ProgressBarColor=126,170,23
ProgressFrameColor=207,208,211
ProgressPosition=164,225
ProgressSize=319,10
URE_BOOTSTRAP=${ORIGIN}/fundamentalrc

---

### Post by Krytarik on 2011-03-29
I looked up the respective package, downloaded it from LibreOffice's PPA and the content of those file turned out to be slightly different. ;-)
```
# *DO NOT* CHANGE THIS FILE. IT ONLY TAKES THE SETTINGS FROM
# /etc/libreoffice/sofficerc. CHANGE THAT FILE IF YOU
# REALLY WANT TO CHANGE SOMETHING.
FHS_CONFIG_FILE=file:///etc/libreoffice/sofficerc

[Bootstrap]
HideEula=${$FHS_CONFIG_FILE:Bootstrap:HideEula}
Logo=${$FHS_CONFIG_FILE:Bootstrap:Logo}
NativeProgress=${$FHS_CONFIG_FILE:Bootstrap:NativeProgress}
ProgressBarColor=${$FHS_CONFIG_FILE:Bootstrap:ProgressBarColor}
ProgressFrameColor=${$FHS_CONFIG_FILE:Bootstrap:ProgressFrameColor}
ProgressPosition=${$FHS_CONFIG_FILE:Bootstrap:ProgressPosition}
ProgressSize=${$FHS_CONFIG_FILE:Bootstrap:ProgressSize}
URE_BOOTSTRAP=${ORIGIN}/fundamentalrc
```Greetings.

PS: I started the search before the previous post happened.

---

### Post by 5149.5 on 2011-03-29
> **Krytarik said:**
> I looked up the respective package, downloaded it from LibreOffice's PPA and the content of those file turned out to be slightly different. ;-)

PS: I started the search before the previous post happened.

Your file is probably more accurate. I did my manual install before a package was available.

---

### Post by Krytarik on 2011-03-29
> **5149.5 said:**
> Your file is probably more accurate. I did my manual install before a package was available.
Makes sense then, seems like the external config file has been implemented after you grabbed your copy.

---

### Post by steve161 on 2011-03-29
Thanks for the quick replies.  I downloaded libreoffice from the ppa, and I agree that Krytarik's version should be more accurate, but I think that 5149.5's version is the one I originally had.  Maybe someone else will post as the tie-breaker.

---

### Post by Krytarik on 2011-03-29
Do you have the file "/etc/libreoffice/sofficerc" then, shall I post it as well?

EDIT: Ah, here it is:
```
[Bootstrap]
HideEula=1
Logo=1
NativeProgress=true
ProgressBarColor=221,72,20
ProgressFrameColor=207,208,211
ProgressPosition=164,225
ProgressSize=319,10
```

---

### Post by steve161 on 2011-03-29
I think that is it.  I changed my splash screen and, mistakenly, edited the file in user/lib instead of etc/.  I am getting an occasional hang when opening libreoffice and want to restore the default file in usr/lib.  I'll save the file I have and try the suggestions that were posted here.  Thanks again.

---

### Post by Zookalicious on 2011-05-28
> **Krytarik said:**
> Do you have the file "/etc/libreoffice/sofficerc" then, shall I post it as well?

EDIT: Ah, here it is:
```
[Bootstrap]
HideEula=1
Logo=1
NativeProgress=true
ProgressBarColor=221,72,20
ProgressFrameColor=207,208,211
ProgressPosition=164,225
ProgressSize=319,10
```

You are a gentleman and a scholar Krytarik. I accidentally overwrote this file without backing it up. Thank you!

---

### Post by Krytarik on 2011-05-28
> **Zookalicious said:**
> You are a gentleman and a scholar Krytarik. I accidentally overwrote this file without backing it up. Thank you!
Thanks! ;) Glad that it helped you!

---

