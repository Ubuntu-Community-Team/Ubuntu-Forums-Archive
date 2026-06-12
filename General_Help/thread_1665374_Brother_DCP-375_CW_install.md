---
title: "Brother DCP-375 CW install"
date: 2011-01-12
forum: General Help
---

### Post by dracotux on 2011-01-12
Hey everyone,

I'm completely new to Ubuntu, so please don't shoot me the first time I don't understand something :P

I want to install my DCP-375 CW printer from Brother, but I can't get it to work.

I can't find the driver in Symbian Package Manager. Is there a way to install this printer?

Kind Regards,
Dracotux

---

### Post by plucky on 2011-01-12
> **dracotux said:**
> Hey everyone,

I'm completely new to Ubuntu, so please don't shoot me the first time I don't understand something :P

I want to install my DCP-375 CW printer from Brother, but I can't get it to work.

I can't find the driver in Symbian Package Manager. Is there a way to install this printer?

Kind Regards,
Dracotux

Go [Here](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html) and download the LPR and CUPswrapper drivers and follow the install instructions.

Good Luck

---

### Post by dracotux on 2011-01-12
Thnx for the reply, but it's a dead link.......

---

### Post by tophousetim on 2011-01-12
Try again....it's all there

---

### Post by dracotux on 2011-01-12
Could you make some printscreens or so? Or could you mail me the files? I really can't reach that site. Not with Firefox, nor with Google Chrome. Could it be i'm missing plugins or so? Thnx for the efford so far btw.

---

### Post by plucky on 2011-01-13
> **dracotux said:**
> Could you make some printscreens or so? Or could you mail me the files? I really can't reach that site. Not with Firefox, nor with Google Chrome. Could it be i'm missing plugins or so? Thnx for the efford so far btw.

Try from a terminal ```
sudo apt-get install ubuntu-restricted-extras
``` which will install codecs and java etc.Then try again.

Good Luck

---

### Post by dracotux on 2011-01-13
did the install, but site is still unreachable......

---

### Post by dracotux on 2011-01-14
I fixed it using:
sudo dpkg -i --force-architecture dcp375cwcupswrapper-1.1.2-2.i386.deb

I found this tip on a forum. Don't know exactly what I did though...

---

