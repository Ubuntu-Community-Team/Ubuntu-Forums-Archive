---
title: "how to force unmount iso"
date: 2009-08-31
forum: General Help
---

### Post by wirate on 2009-08-31
how to unmount an iso image when a process is using it?

**Just if someone wants the reason...**
I have a game in two iso images i intend to run in wine. i mount the first image and run the setup.exe. after some time it prompts me to insert the next cd. when I use ```
umount
``` it tells me device is busy. the installer is using it. i cant mount the second image to a different mnt point; the installer wont detect it. and when i end the process... u know what :)

---

### Post by Kristofer Van Orton on 2009-08-31
how are you mounting the images? using Gmount?
tell me if im wrong but im pretty sure Gmount has the ability to mount multiple disks at once which would probably solve your problem

like i said i could be wrong im kind of a noob

---

### Post by ciprian.topala on 2009-08-31
Try using umount -f as it forces unmounting the image.
And from my previous experiences Gmount handles pretty well this kind of situation when you have to mount several images for a game install.

---

### Post by wojox on 2009-08-31
Run:

```
top
```

Find the pid of the iso and kill it.

---

### Post by wirate on 2009-09-01
**gmount**
no it cant unmount an image when its being used by some process. no error but its just still there.

**umount -f**
same error. device is busy

**top**
i suppose its equivalent to the system monitor's processes tab. when i kill the process the installer stops responding. that is expected i guess

---

