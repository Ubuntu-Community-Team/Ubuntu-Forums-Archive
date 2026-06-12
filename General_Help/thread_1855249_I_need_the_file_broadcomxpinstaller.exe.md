---
title: "I need the file broadcomxpinstaller.exe"
date: 2011-10-05
forum: General Help
---

### Post by PaleoNerd on 2011-10-05
I just installed Ubuntu on my macbook pro and need the file **broadcomxpinstaller.exe **to get the wireless card working. This file is on the OS X installation  CD under bootcamp drivers, which I do not have on me. Any help here  would be greatly appreciated.

---

### Post by mikejonesey on 2011-10-05
really?? an exe to get a kernel module working? hmm... I don't think wine can or should be able to edit such things...

maybe i'm wrong...

---

### Post by PaleoNerd on 2011-10-05
I says I need it here:

[https://help.ubuntu.com/community/MacBookPro_Penryn](https://help.ubuntu.com/community/MacBookPro_Penryn)

---

### Post by mikejonesey on 2011-10-05
extracted for drivers... i see.. hmm if not availible from apple for download (i'd be suprised) have u checked sourceforge and the likes?... rather than waiting for an upload?

---

### Post by mikejonesey on 2011-10-05
what is make and model? i'll check apple for you...

---

### Post by mikejonesey on 2011-10-05
broadcominstaller.exe will work the same (same drivers inside), torrenting this one should be eaasyer more availble...

---

### Post by PaleoNerd on 2011-10-05
Mid 2010 13 inch Macbook Pro
Intel Core 2 duo processor

---

### Post by PaleoNerd on 2011-10-05
So I have the drivers installed how they did it in this video:

[http://www.youtube.com/watch?v=TbviIHY8iiM](http://www.youtube.com/watch?v=TbviIHY8iiM)

It says the driver is downloaded and the hardware is present, however it is still showing that the firmware is out of date when I click on the wireless connections tab.

---

### Post by wildmanne39 on 2011-10-06
Hi, I doubt you need ndiswrapper for a broadcom card, that guide was written in 2008.
Please post the results of these commands so we can find out for sure.
```
cat /etc/lsb-release; uname -a
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
clicking on new reply and click # and paste the information between the brackets.
Thank you

---

