---
title: "[please help] how to connect to wireless"
date: 2009-10-27
forum: General Help
---

### Post by exchangeboss on 2009-10-27
i want connect to wireless i have tp link tl wn620g 


but i dont know how to connect with it 


so please help 



lsusb result 


> exchangeboss@coder-desktop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0cf3:0002 Atheros Communications, Inc. AR5523 (no firmware)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by exchangeboss on 2009-10-27
up

---

### Post by exchangeboss on 2009-10-27
jjjjjjjjj

---

### Post by carml on 2009-10-27
Have you made a search on google to know if your card is compatible with Gnu/Linux? If it isn't compatible,as far as I know, you'll have to download the driver for Windows of your card.
Make a search and then post here the result :)

---

### Post by exchangeboss on 2009-10-27
i make a lot of search my friend but i found the way to take the driver from windows and do it with ndiswrapper

so ndiswrapper -l result

> exchangeboss@coder-desktop:~$ ndiswrapper -l
athfmwdl : driver installed
net5523 : driver installed


---

### Post by exchangeboss on 2009-10-28
up

---

### Post by phillw on 2009-10-28
> **exchangeboss said:**
> i make a lot of search my friend but i found the way to take the driver from windows and do it with ndiswrapper

so ndiswrapper -l result


Hi,

If you give a brief run-down of what you have, what you have done & the output of your ndis list over on [http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)  That area is for networking & wireless.

If you type in your card into the search on that forum, it will also show posts regarding your card.

Hope that helps,

Regards,

Phill.

---

### Post by splosh5 on 2009-10-28
Im useing the belkin wireless g adaptor and all i had to do was plug and play but with windows i would have to install all the drivers and stuff.

---

### Post by carml on 2009-10-28
> **exchangeboss said:**
> i make a lot of search my friend but i found the way to take the driver from windows and do it with ndiswrapper

so ndiswrapper -l result

I would drive you to that,tha's why I asked you if you looked for the drivers ;)

---

