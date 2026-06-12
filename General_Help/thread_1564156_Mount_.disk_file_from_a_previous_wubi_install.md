---
title: "Mount .disk file from a previous wubi install?"
date: 2010-08-30
forum: General Help
---

### Post by todd_r on 2010-08-30
Hello all, I had an installation of Ubuntu under windows via wubi, after an update last week it wouldn't boot up at all, I tried everything I could find about how to fix grub, none of which worked, after looking at a working installation of Ubuntu with wubi I realised that my root.disk file had dissapeared. 

I gave up and decided to get rid of windows all together, and now have a fresh 'proper' install of Ubuntu, but that root.disk file has turned up in a file called 'found'. 

Is there any way I can mount that file in ubuntu to retrive the documents etc that I thought I had lost?

Many thanks, Todd

---

### Post by bcbc on 2010-08-30
Yes,

```
sudo mount -o loop /<path_to_root_disk>/root.disk /mnt
nautilus /mnt   # to browse

```
If you have problems mounting it, you can fsck it (don't do it if you mounted it already):
```
sudo fsck /<path_to_root_disk>/root.disk
```

---

### Post by todd_r on 2010-08-31
Fantastic! Got photos back I thought were lost, thank you very much :)

---

### Post by bcbc on 2010-08-31
Cool :)

---

### Post by ecthileon on 2011-07-04
> **bcbc said:**
> Yes,

```
sudo mount -o loop /<path_to_root_disk>/root.disk /mnt
nautilus /mnt   # to browse

```


I just thought I'd say that this also works if you installed wubi, saved the old disk, and installed wubi again.


Time to get my minecraft worlds back...  ;)

---

