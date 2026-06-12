---
title: "Startup Disk Creator"
date: 2012-04-25
forum: General Help
---

### Post by cshin9 on 2012-04-25
I'm having trouble with the Startup Disk Creator. I've previously made bootable USB for Ubuntu and Lubuntu 11.10 with the SDC. However, I'm trying to add another ISO file to the list, but it does not show up on the "Source disc image (.iso) or CD:" list. The only two that appear are the Ubuntu and Lubuntu images.

---

### Post by techsupport on 2012-04-25
> **cshin9 said:**
> I'm having trouble with the Startup Disk Creator. I've previously made bootable USB for Ubuntu and Lubuntu 11.10 with the SDC. However, I'm trying to add another ISO file to the list, but it does not show up on the "Source disc image (.iso) or CD:" list. The only two that appear are the Ubuntu and Lubuntu images.

Well, what is it that you are adding? Lubuntu, Ubuntu, or something different?

Try unetbootin instead. And see if that works.

In terminal:

```
sudo apt-get install unetbootin
```

---

### Post by cshin9 on 2012-04-25
I'm trying to make a bootable LMDE USB. Is SDC only for making bootable media of *buntus?

---

### Post by techsupport on 2012-04-25
> **cshin9 said:**
> I'm trying to make a bootable LMDE USB. Is SDC only for making bootable media of *buntus?

Yes, that is correct. 

Try Unetbootin.

---

### Post by cshin9 on 2012-04-25
Thanks, that's what I'm doing now.

---

### Post by Lemuriano on 2012-04-25
Is my understanding that disk creator is for the buntus only but  unetbootin will work or a DVD with brasero.

Regards.

---

### Post by techsupport on 2012-04-25
> **cshin9 said:**
> Thanks, that's what I'm doing now.

If it works out, let us know, and don't forget to close the thread and mark as solved when you are done here.

---

### Post by techsupport on 2012-04-25
> **Lemuriano said:**
> Is my understanding that disk creator is for the buntus only but  unetbootin will work or a DVD with brasero.

Regards.

Unetbootin is the same as Startup Disc Creator except it can handle more distos. I've only used ISO files with Unetbootin, so I wouldn't know about DVD functionality.

---

### Post by Lemuriano on 2012-04-26
I have been using dvd-rw lately and works like a charm.

Regards.

---

### Post by techsupport on 2012-04-26
> **Lemuriano said:**
> I have been using dvd-rw lately and works like a charm.

Regards.

Try USB Thumb Drives. They install much faster than DVD-RW. And you can set them up to use "persistance" when you boot from them to save all your settings during the USB Live session.

---

### Post by Lemuriano on 2012-04-26
The beauty of Gnu/Lunix is that every one, perhaps for different reasons, like no usb, damage one ect. most accomplish their task and sometimes there are a plethora of roads to get there, like there are distros, and probably one path will be better for the member if that tool is available, but if not then it will be useless. 

Regards.

---

### Post by cshin9 on 2012-05-04
Thanks. I used UNetbootin, and it works with non-*buntus.

---

