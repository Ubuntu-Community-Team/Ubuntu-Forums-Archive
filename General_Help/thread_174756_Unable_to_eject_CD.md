---
title: "Unable to eject CD"
date: 2006-05-12
forum: General Help
---

### Post by GabrielWolff on 2006-05-12
Hey, I burnt a CD in k3b and right after that put in again to check if everything was burnt alright. 

It is.

And now it's stuck:
When trying to eject the CD I get the following error:
```
Unable to eject media
unmount: /media/cdrom0: device is busy
unmount: /media/cdrom0: device is busy
eject: unmount of '/media/cdrom0' failed
```

But I can't think of any program that might use the CD right now.
Where should I look for a such?

Thanks

Gabriel

---

### Post by dg_w on 2006-05-12
Umm good one, like you say normaly something accessing the volume ..

Tries, logging out, 
Ctrl+Alt+F2 login and type eject 
Should eject .
Login back in from the GDM at
CTRL+Alt+F7

:)

---

### Post by GabrielWolff on 2006-05-12
[QUOTE=dg_w]Umm good one, like you say normaly something accessing the volume ..

Tries, logging out, 
Ctrl+Alt+F2 login and type eject 
Should eject .
Login back in from the GDM at
CTRL+Alt+F7

:)[/QUOTE]

Didn't work. I shut down the computer and ejected the CD.

Any good idea for next time? ;) 

G

---

### Post by ZylGadis on 2006-05-12
Take a look at "man umount" in a terminal, and especially the -l option.

---

### Post by bluevoodoo1 on 2006-05-12
ZylGadis has it. Try...

```
sudo umount /dev/hdX
```

where hdX is the location of your drive.

---

### Post by hardXcore on 2006-05-12
there is a small hole you stick a paperclip in on your cd drive that will eject it

---

### Post by Ramses de Norre on 2006-05-12
```
sudo fuser -u /dev/hdc
```
will show which processes are using it so you can kill them if needed. Change to the correct device.

---

### Post by Googler on 2006-05-12
i got the same problem before
just try this , it will work
```
umount /dev/cdrom
```

---

