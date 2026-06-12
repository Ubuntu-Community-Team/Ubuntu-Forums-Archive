---
title: "windows 7 and ubuntu 10.04 boot?"
date: 2010-12-06
forum: General Help
---

### Post by abhilashm86 on 2010-12-06
There was windows 7 Home Basic pre installed onto Hcl Desktop at my Office, then i installed ubuntu 10.04 to it, everything was ok untill i restarted:( 

When i select windows 7 from dual boot, it takes me back to dual boot grub page:( 

So i did inserted Windows 7 cd and restored windows by this 
```
bootrec.exe /fixboot
``` . Now only windows 7 is working and booting. 

I want ubuntu 10.04 on the dual boot, how and what is exact method of recovering ubuntu without harming windows 7? 

Is it with ubuntu 10/04 cd?? If i do live cd and restore grub, will windows 7 work?? I haven't given any details of hd0 and root, i'll manage, just tell the procedure.

---

### Post by lindsay7 on 2010-12-06
see this

[http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html](http://www.webupd8.org/2009/12/how-to-recover-grub2-linux.html)

---

### Post by abhilashm86 on 2010-12-07
I as able to retrieve ubuntu 10.04 back successfully, thanks:p 

But when i went to ubuntu 10.04 and installed updates, disaster awaited!! on reboot my linux was not booting??

Initframs was popping up after grub2 menu and half a day i searched for help, no use. Finally i got a solution from initframs. 
take a [look at this]("http://computergyan.wordpress.com/2009/12/31/solving-the-busybox-black-screen-problem-in-grub2ubuntu9-10/")

---

