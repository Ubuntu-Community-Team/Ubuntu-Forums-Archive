---
title: "medion e1210; webcam not working after clean install"
date: 2009-11-16
forum: General Help
---

### Post by fatattack on 2009-11-16
hi there, im quite new to ubuntu, i really like it but have no idea how to fix minor things like this....

so i had the live version on a usb stick, im talkin ubuntu 9.10 netbook remix, for my medion e1210.... everything worked perfectly while running from the usb.

after i installed to my hard drive, the webcam does not work anymore, it gives the webcam not found error in cheese.

i havent changed anything, not updated anything, nothing, just after installing to hard drive it stopped working.

whats up with that? can anyone help me? please!
 cheers

---

### Post by Jefferythewind on 2009-11-18
I have a MSI wind with the same problem.  Need some help.

---

### Post by likebikes on 2009-12-12
ok ihave a medion E1210 runing ubuntu netbook remix 9.10. This is the download from Ubuntu site NOT a modified Ubuntu 9.10 then remixed afterwards. Everything works USB and internal cam. This is what i followed.

first, run system update

then go here:

[http://ubuntuforums.org/showthread.php?t=1330356](http://ubuntuforums.org/showthread.php?t=1330356)

scroll down to the bit where it talks about 'blacklist uvcvideo' and applying that in /etc/modules. I did this and bingo everything works!!! despite what is said about killing off cam...it dosen't

hope it helps

---

