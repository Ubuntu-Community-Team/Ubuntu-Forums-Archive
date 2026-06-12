---
title: "problem updating 9.10"
date: 2010-02-26
forum: General Help
---

### Post by woodsyboredom on 2010-02-26
I upgraded to 9.10 in September online using the Update Manager. 

Recently I receives notification of about 53 updates. I tried to install the updates but I keep getting this window when I do:

Please insert the disk labeled:
Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)
in drive /cdrom

Problem is I don't have that disc because I upgraded online. I have two buttons to chhose from. an OK button and a CANCEL button if I click the OK button the window with this message reappears immediately. If I click cancel I get this message:

W: Failed to fetch cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091027)]/pool/main/m/m4/m4_1.4.13-2_i386.deb
  


W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.2-1ubuntu7.2_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/p/pidgin/libpurple0_2.6.2-1ubuntu7.2_i386.deb)
  

I downloaded an iso copy of 9.10 release i386 and burned it onto a cd rom and put it in the CD_ROM Drive but I keep getting the the same response.

Does anyone have an idea what to do next?

Thanks, 

Woodsy Boredom

---

### Post by zvacet on 2010-02-26
System>admin>software sources>uncheck CD-ROM as repository.Reload.If you still have problems with U.S. server on same place as before change server to main.Reload.In terminal 


```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by woodsyboredom on 2010-02-26
YAY!!! that did it! thank you! I love ubuntu.

---

