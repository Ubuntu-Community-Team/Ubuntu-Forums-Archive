---
title: "X-Windows Version ?"
date: 2009-07-18
forum: General Help
---

### Post by BramWillemsen on 2009-07-18
Hi all,

I am trying to get some support with a broken ati fglrx driver. I am filling in an ATI contact form and they ask for my "X-Windows Version". I did 'Xorg -version' and it returns version 1.6.0 for the x-server. I need to fill in something like 7.0, 7.1, 7.2, 7.3, 7.4 etc for the x-windows version. How can i find out which version i have? I am using jaunty.

Thanks a lot,

Bram

---

### Post by PixelLord on 2009-07-18
Try checking the installed version details through synaptic. I think 1.6 is 7.4. I may be off though.

---

### Post by BramWillemsen on 2009-07-18
Thanks, synaptic shows its 7.4. I didnt think of using synaptic to check

---

### Post by collinp on 2009-07-18
If you dont have immediate access to Synaptic, you can also run:
```
sudo X -version
```which will display the version of the X server and other related information.

---

### Post by PixelLord on 2009-07-18
Thanks for the assist Hellow. I knew there was an cl query but wasnt sure of the syntax.

---

