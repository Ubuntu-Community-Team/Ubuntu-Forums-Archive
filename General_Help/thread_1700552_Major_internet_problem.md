---
title: "Major internet problem"
date: 2011-03-05
forum: General Help
---

### Post by Spyderkid on 2011-03-05
My wireless internet USB was working fine with the driver that i made, [link to how i made the driver]("http://http://ubuntuforums.org/showthread.php?t=1671814"). but i did an update recently which rendered it usuless (or at least i thinks its the update), I recompiled the driver.... nothing. disabled and re-enabled it... nothing. it shows up if i run *lsusb *and if i take out the dongle only wired networks are shown when you click on the network manager icon. if i insert the dongle the grey heading of wireless networks shows up, with no networks underneath it. the internet works from otgher computers. even my ipod, so i know that its not the wireless box and its not outn of range either.
 
 
 
 
My chipset is RTL8192SU
 
its a belkin wireless dongle.
 
 
 
*Thanks!*

---

### Post by grahammechanical on 2011-03-05
Does Enable Wireless have a tick mark against it? Right click the icon.

Regards.

---

### Post by Spyderkid on 2011-03-05
it's all enabled.

---

### Post by gandaran on 2011-03-05
> **Spyderkid said:**
> My wireless internet USB was working fine with the driver that i made, [link to how i made the driver]("http://http://ubuntuforums.org/showthread.php?t=1671814"). but i did an update recently which rendered it usuless (or at least i thinks its the update), I recompiled the driver.... nothing. disabled and re-enabled it... nothing. it shows up if i run *lsusb *and if i take out the dongle only wired networks are shown when you click on the network manager icon. if i insert the dongle the grey heading of wireless networks shows up, with no networks underneath it. the internet works from otgher computers. even my ipod, so i know that its not the wireless box and its not outn of range either.
 
 
 
 
My chipset is RTL8192SU
 
its a belkin wireless dongle.
 
 
 
*Thanks!*
theres no need to install any driver for this wireless dongle, [see this]("http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/") how to get it working.

---

### Post by dougalkerr on 2011-03-05
Have you knocked off the wireless card switch? I have done this more than once but, it takes me by surprise when I have done it. I automatically think there is a problem when there isn't.

---

### Post by Spyderkid on 2011-03-05
no the dongle is fine.

---

### Post by Spyderkid on 2011-03-05
> **gandaran said:**
> theres no need to install any driver for this wireless dongle, [see this]("http://www.omgubuntu.co.uk/2011/01/realtek-rtl8192su-ubuntu-driver-fix/") how to get it working.
 
for my certain model i do the place where i found it was [here]("http://samiux.blogspot.com/2010/05/howto-realtek-8192su-usb-dongle.html") but ill give what you suggested a go aswell.

---

### Post by Spyderkid on 2011-03-05
apparently there is no such directory /libfirmware/ RTL8192SU and cannot create it.

---

### Post by gandaran on 2011-03-05
> **Spyderkid said:**
> apparently there is no such directory /libfirmware/ RTL8192SU and cannot create it.
this will create it
```
sudo cp /lib/firmware/RTL8192SE/* /lib/firmware/RTL8192SU
```

note, this is for 10.10 only, I think in 11.04 it will work out of the box.

---

### Post by Spyderkid on 2011-03-05
sorry miss-spelt it did work fine.
 
HOWEVER
 
it searches for my network i point it towards it and it tries to connect however it can't :S.
its got the correct password.
 
the wireless icon just flashes up and down and then after 3 mins asks me for the password again even though its right....
 
*ideas?*

---

### Post by gandaran on 2011-03-05
> **Spyderkid said:**
> sorry miss-spelt it did work fine.
 
HOWEVER
 
it searches for my network i point it towards it and it tries to connect however it can't :S.
its got the correct password.
 
the wireless icon just flashes up and down and then after 3 mins asks me for the password again even though its right....
 
*ideas?*
maybe you need the appropriate firmware in that new folder, there was a new linux- firmware update recently so that must have installed something new.
[check this bug]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg2620217.html"), theres a link to download the firmware and copy it to /lib/firmware RTL8192SU, I'm not sure if this firmware will work for you, it did for me but it was a deferent RTL chip, backup first before installing the new firmware.

---

### Post by Spyderkid on 2011-03-05
Will the old driver i made be upsetting it?
I've dissabled it anyway...
 
ill try what you suggested.

---

### Post by Spyderkid on 2011-03-05
the link you posted sounds exactly the same to my problem.

---

### Post by gandaran on 2011-03-05
> **Spyderkid said:**
> the link you posted sounds exactly the same to my problem.
yep, I also had exactly the same problem but with RTL8188SU chip, that link fixed it with RTL8192SU firmware, hope it works for you.

---

### Post by Spyderkid on 2011-03-05
I am now proud to say I'm posting this using wireless on Ubuntu (a.k.a. it worked :D)

---

### Post by Spyderkid on 2011-03-06
the old driver gave me almost double the speed of this driver.

---

