---
title: "truecrypt"
date: 2011-05-02
forum: General Help
---

### Post by user2904 on 2011-05-02
program truecrypt don't work in new ubuntu 11.04
When i want close decrypted disk system massege "device-mapper: remove ioctl failed: Device or resource busy
Command failed"
 In ubuntu 10.10 this program work good .Please help:confused:

---

### Post by cragwolf on 2011-05-02
Maybe you have Nautilus open to that encrypted folder, and hence why it's "Device or resource busy". Or some other application is using a file from that folder. Make sure you close all applications that are using files within your encrypted folder. Then you can unmount it.

---

### Post by lotharmat on 2011-05-02
> **user2904 said:**
> program truecrypt don't work in new ubuntu 11.04
When i want close decrypted disk system massege "device-mapper: remove ioctl failed: Device or resource busy
Command failed"
 In ubuntu 10.10 this program work good .Please help:confused:

I used to get this error in 10.10

I can't remember the fix off-hand - I'll have a look

---

### Post by aeronutt on 2011-05-02
Just FYI, Truecrypt works fine for me in 11.04.

---

### Post by user2904 on 2011-05-08
I found what is problem (I just need to defradment my hdd and all works).But Thanks you all.

---

