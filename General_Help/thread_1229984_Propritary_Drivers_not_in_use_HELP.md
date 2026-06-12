---
title: "Propritary Drivers not in use HELP"
date: 2009-08-02
forum: General Help
---

### Post by zarroc33 on 2009-08-02
Hello,
I've installed Jaunty and it has come to my attention that my graphics drivers are not in use. Here is my $ lspci -nn | grep VGA:

> 01:05.0 VGA compatible controller [0300]: ATI Technologies Inc RS780MC [Radeon HD 3100 Graphics] [1002:9613]

I really want to enable desktop effects and everything, but I realize it's only eye candy...

Please use step by step instructions, and I'm running on a Toshiba Satellite l305d-s5934.

Thanks

---

### Post by gamblor01 on 2009-08-02
This is described in gory detail on the wiki:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)


Try to follow that and see if it works for you.  If not, please post where you get stuck.


**EDIT:** Here are the specific instructions for Jaunty:


> 
**Instructions for Ubuntu 9.04 (Jaunty)**

 Enable the accelerated ATI graphics driver in the 'Hardware Drivers' (System->Hardware drivers), then do: 
```

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko
```
Log out and log in. 


---

### Post by zarroc33 on 2009-08-02
Hi,
Thank you, but the problem is that I can't enable the drivers as the first instruction that you posted says... So to follow the instructions you sent, I need instructions for those instructions.

Sorry for any confusion.

---

