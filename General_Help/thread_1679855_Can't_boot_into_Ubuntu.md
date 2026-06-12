---
title: "Can't boot into Ubuntu"
date: 2011-02-01
forum: General Help
---

### Post by RzTks on 2011-02-01
So I'm new to Ubuntu, and I'm OK with computers. But after installing Ubuntu from Wubi (From the .iso file) and I turn off my laptop, it doesn't show up in my Partition loader. It only shows Windows7 and thats it. Can anyone help me with this problem? Heres my laptop specs: 
W7 Ultimate 
Intel Core2 Duo P8400 @ 2.26GHz 
4094 MB RAM 
NVIDIA GeForce 9600M GS 
ST9320320AS Seagate 320GB 2.5" SATA 3.0Gb/s Notebook Hard Drive 
Can someone please help me? I've used Ubuntu before and I do enjoy it more than Windows.

---

### Post by MooPi on 2011-02-01
Is Ubuntu listed in your installed apps under Windows ?

---

### Post by Rubi1200 on 2011-02-01
Hi and welcome to the forums RzTks :-)

> But after installing Ubuntu from Wubi (From the .iso file) and I turn off my laptop, it doesn't show up in my Partition loaderDid you complete the installation?

After it is finished in Windows you need to restart for the installation to complete otherwise it will fail.

For more information, see here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20install%20Ubuntu?)

---

### Post by RzTks on 2011-02-01
Yes Ubuntu is listed under the installed apps, and yes I do complete the installation by restarting.

---

### Post by bcbc on 2011-02-01
You have to restart and boot into Ubuntu to complete the installation. Boot Windows, go to the Startup and Recovery settings and check that there is an entry for Ubuntu there - make sure the timeout is not zero. Make it 10 or more.

If the problem was the timeout, then boot again, select Ubuntu and let it install. Then boot into Ubuntu again and lock packages grub-pc and grub-common before running any updates. See [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for details.

If the problem is there is no entry for Ubuntu - then you'll have to create it manually or try reinstalling.

---

