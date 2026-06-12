---
title: "Can I RDP into Ubuntu Server?"
date: 2009-09-04
forum: General Help
---

### Post by aaronshaf on 2009-09-04
Hear me out, this might sound weird. I'm on Windows 7 and I have some remote instances of Ubuntu Server that I work on. Is there a way to install Ubuntu Desktop on an Ubuntu VPS and then RDP into from Windows?

Thanks for your help!

Aaron

---

### Post by doas777 on 2009-09-04
you can't RDP, but you could use VNC or FreeNX, both of which have windows clients. VNC is not safe over the internet, but FreeNX can be if correctly configured.
[http://www.realvnc.com/](http://www.realvnc.com/)
[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by P4man on 2009-09-04
If you need a GUI, you can use freeNX for that:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

AFAIK, it also works on a headless server.

That said, for a server, you may want just ssh?

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

And for the windows machine, putty:

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

---

### Post by aaronshaf on 2009-09-04
Thanks guys.

I use Putty everyday. But there are some graphical tools in Ubuntu Desktop that would make my job easier.

What do you guys think of xrdp?

---

