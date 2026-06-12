---
title: "vista problem after installing ubuntu 9.10"
date: 2010-02-06
forum: General Help
---

### Post by wildhorse on 2010-02-06
i installed ubuntu a mount ago , since then my vista goes bluescreen almost every week , i have vista business sp2 32bit and ubuntu 9.10 32bit dual boot. details about one of bluescreens is below , every help would be appreciated.

Problem signature:
  Problem Event Name:    BlueScreen
  OS Version:    6.0.6002.2.2.0.256.6
  Locale ID:    1033

Additional information about the problem:
  BCCode:    be
  BCP1:    837020B7
  BCP2:    28EA0860
  BCP3:    8BB63A18
  BCP4:    0000000E
  OS Version:    6_0_6002
  Service Pack:    2_0
  Product:    256_1

Files that help describe the problem:
  C:\Windows\Minidump\Mini020110-01.dmp
  C:\Users\nafiseh\AppData\Local\Temp\WER-50060-0.sysdata.xml
  C:\Users\nafiseh\AppData\Local\Temp\WER8304.tmp.version.txt

Read our privacy statement:
  [http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409](http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409)

---

### Post by howefield on 2010-02-06
What is it about the blue screens that makes you think it is an Ubuntu problem ? (Is this a real dual boot or a Wubi dual boot)

The only interest Ubuntu will have on your Vista install is adding it to the bootloader, so as long as Vista boots, it is then all Vista.

Before installing Ubuntu, did you defragment your drive in preparation for the partitioning.

---

### Post by raven2099 on 2010-02-06
i'm having simalare issues wibut with 8.10
 
i installed from disk from inside windows but a week later ubunto had error's where windows is fine
but now adfter i uninstalled the Ubunto option is still on my boot list and i don't want it ther...

---

### Post by sandyd on 2010-02-06
> **raven2099 said:**
> i'm having simalare issues wibut with 8.10
 
i installed from disk from inside windows but a week later ubunto had error's where windows is fine
but now adfter i uninstalled the Ubunto option is still on my boot list and i don't want it ther...
this is why we prefer for people NOT to use wubi if they can.....

---

### Post by wildhorse on 2010-02-06
> **howefield said:**
> What is it about the blue screens that makes you think it is an Ubuntu problem ? (Is this a real dual boot or a Wubi dual boot)

The only interest Ubuntu will have on your Vista install is adding it to the bootloader, so as long as Vista boots, it is then all Vista.

Before installing Ubuntu, did you defragment your drive in preparation for the partitioning.

cause it started after installing ubuntu , i did not shrink the vista volume , the ubuntu installation wizard did that , and i always do the defragment , i thougth that may be the shrinking process has caused that  . and it is real dual boot.

---

### Post by sandyd on 2010-02-06
> **wildhorse said:**
> i installed ubuntu a mount ago , since then my vista goes bluescreen almost every week , i have vista business sp2 32bit and ubuntu 9.10 32bit dual boot. details about one of bluescreens is below , every help would be appreciated.

Problem signature:
  Problem Event Name:    BlueScreen
  OS Version:    6.0.6002.2.2.0.256.6
  Locale ID:    1033

Additional information about the problem:
  BCCode:    be
  BCP1:    837020B7
  BCP2:    28EA0860
  BCP3:    8BB63A18
  BCP4:    0000000E
  OS Version:    6_0_6002
  Service Pack:    2_0
  Product:    256_1

Files that help describe the problem:
  C:\Windows\Minidump\Mini020110-01.dmp
  C:\Users\nafiseh\AppData\Local\Temp\WER-50060-0.sysdata.xml
  C:\Users\nafiseh\AppData\Local\Temp\WER8304.tmp.version.txt

Read our privacy statement:
  [http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409](http://go.microsoft.com/fwlink/?linkid=50163&clcid=0x0409)
copy down the STOP code (theirs a code that appears on the screen when vista bluescreens...)

your looking for the circled portion

---

### Post by wildhorse on 2010-02-06
> **carlee said:**
> copy down the STOP code (theirs a code that appears on the screen when vista bluescreens...)

your looking for the circled portion
so i have to wait for the next blue screen to happen ? or is the dump files ok?
cause the bluescreen goes very fast and computer restarts then.

---

### Post by sandyd on 2010-02-06
> **wildhorse said:**
> so i have to wait for the next blue screen to happen ? or is the dump files ok?
cause the bluescreen goes very fast and computer restarts then.
[http://www.watchingthenet.com/disable-automatic-restarts-with-blue-screen-of-death.html](http://www.watchingthenet.com/disable-automatic-restarts-with-blue-screen-of-death.html)

---

### Post by wildhorse on 2010-02-06
> **carlee said:**
> [http://www.watchingthenet.com/disable-automatic-restarts-with-blue-screen-of-death.html](http://www.watchingthenet.com/disable-automatic-restarts-with-blue-screen-of-death.html)
thanks , i will try that.:D

---

