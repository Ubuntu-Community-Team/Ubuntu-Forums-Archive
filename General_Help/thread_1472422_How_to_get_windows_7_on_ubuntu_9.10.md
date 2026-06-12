---
title: "How to get windows 7 on ubuntu 9.10?"
date: 2010-05-04
forum: General Help
---

### Post by mak.ripon on 2010-05-04
I reinstalled ubuntu grub 2.
Now windows 7 is gone.
How to get back windows 7 now?

---

### Post by eriktheblu on 2010-05-04
How about:```
sudo update-grub
```

---

### Post by spayman on 2010-05-04
[B]that's a famous known bug on win 7
install or reinstall another OS on the same partition :
causes it's .... just disepears !
I think u need to poot up from the cd (the win one)
then choose , (fix my system) it takes like 15sec 
there u go , Your Ruindows is back x)[/B]

---

### Post by dino99 on 2010-05-04
sudo grub-mkconfig && update-grub

note: grub2 must be installed on the ubuntu mbr partition ( take care of other distro bootloader)

---

### Post by x C0MMAND0 x on 2010-05-04
I believe what Sprayman is trying to say is you can put in a Windows 7 CD and repair your MBR (Master boot record), but this will make Windows 7 your default OS and depending on how it is setup make Ubuntu not easy to boot into.  I would use a [tutorial such as this]("http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7") to set grub2 as your default boot loader.

---

### Post by x C0MMAND0 x on 2010-05-04
You can also try using startup manager to fix your grub configuration and get Windows 7 back.

```
sudo apt-get install startupmanager
```

---

### Post by Maheriano on 2010-05-04
```
sudo apt-get install fail
```

---

### Post by dino99 on 2010-05-04
> **Maheriano said:**
> ```
sudo apt-get install fail
```

install fail

no such package into synaptic  :(

---

### Post by Maheriano on 2010-05-04
> **dino99 said:**
> install fail

no such package into synaptic  :(
haha, best reply ever!
You're right, Synaptic does not have fail. The main reason I use Ubuntu.

---

