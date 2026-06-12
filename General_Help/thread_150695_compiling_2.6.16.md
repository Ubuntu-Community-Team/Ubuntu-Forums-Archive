---
title: "compiling 2.6.16"
date: 2006-03-26
forum: General Help
---

### Post by yohan on 2006-03-26
Im using breezy and im trying to compile kernel version 2.6.16. Partly because of my network card and my graphics card.

Ive tried most guides on this forum and on the wiki and everytime ive tried booting the new kernel it says:
"mounting root file system - OK"
....
Then it just freezes for about 3-5 minutes on:
"waiting for root file system..."
After this wait it posts:
/dev/sda1 not found!
And i enter a shell.

Any ideas? Ive been trying to fix this for days and asking on irc i've given up.

thank you so much!

---

### Post by p47 on 2006-03-26
Hello yohan I've the same probem if you can compiled the new kernel "2.6.16" please tell me I tired too to read much tutorials and i can't if you find a good tutorial please tell me ...

Regards !

---

### Post by yohan on 2006-03-27
Hey!

Sadly enough im glad we're in the same boat! I've been tweaking around but I havnt gotten it to work yet. I think it might have to do with the SATA device drivers. When i select scisi device with gconfig it tells me that it should not be compiled as a module but as a part of the kernel if my root (/) is on a SATA disc...which mine is. By default its compiled as a module but i tried making most things not as a module but i havnt gotten it to work yet. I think it might be good to have the specific SATA controller not compiled as a module and i havnt looked mine up yet. This is just a wild guess tho...

Hope somebody else knows,

Thanks,
Yohan

---

### Post by yohan on 2006-03-27
I fixed it!

After a few hours of searching I finally found a small snippet that says it worked after using yaird instead of mkinitrd. I did the same with this command:
sudo yaird -o /boot/initrd.img-2.6.16-ck1-1.4 2.6.16-ck1-1.4

where 2.6.16-ck1-1.4 is my kernel name.

Ofcourse removing/backing up my old initrd.img beforehand.

I hope it works for you too!

And I hope somebody else finds this usfull, especially the dudes working on implementing this kernel into dapper ?

---

### Post by Mustard on 2006-05-15
/me stumbles across this problem several weeks later...

I'm curious what the above command is doing. :)

---

