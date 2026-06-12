---
title: "Pendrive Image? Casper-rw?"
date: 2010-03-29
forum: General Help
---

### Post by schwabdale on 2010-03-29
I made a persistent install of Ubuntu on a flash drive. I made changes to that installation. 
The software (Unetboontin) sets this all up. I think it partitions it for you. 

How do I image that flash drive to another flash drive?

---

### Post by Dayofswords on 2010-03-29
just to be clear, you want to copy an entire flash drive, to another, correct?

---

### Post by schwabdale on 2010-03-29
That is correct. 
I have imaged Windows machines using Driveimagexml, Ghost, ect. 
Normally I do this from UBCD. 

I think this drive has some hidden partitions, like swap space. 

I want to carry all of the information I put there persistently to another Flash drive, just as I would with something like Ghost (Disk to Disk)

Thanks for the help

---

### Post by lotharmat on 2010-03-29
could you use the dd command?

Plug in your source USB stick and make a note of its designation (sdx)
Plug in the other one and make a note of its designation - again sd[whatever]

Then use the following command

```
dd if=/dev/sd[source] of=/dev/[dest] bs=512
```

That should work fine - there may be more options though

---

### Post by schwabdale on 2010-03-29
I'll give it a go and let you know.

---

### Post by schwabdale on 2010-03-31
It looked like it was going to work. However, when I plugged the flash drive in (the one that had the data copied to it) the computer and tried to boot... It said missing operating system. 

I used Unetbootin to make the original drive. Any other ideas?

---

### Post by Bungler on 2010-03-31
There are also tools available to create the boot sector, because that is what you are missing in this case.

I used 'ghost 4 linux' to make identical copies of hard drives, including boot sectors. It will probably work for usb keys as well.
Good luck!

---

### Post by schwabdale on 2010-03-31
Sorry, 
The software I am using is called Universal USB Installer, from there you can do the persistent option

---

### Post by schwabdale on 2010-03-31
How is Ghost for Linux different from using the "dd" command if you don't mind me asking?

---

### Post by schwabdale on 2010-03-31
Ghost for Linux worked! Thanks for the help

---

### Post by Bungler on 2010-03-31
I don't know what g4l differs from dd, perhaps it uses the same command but using dd there are probably many variations and g4l just uses the right one ;)
Anyway, nice that it works :)

---

