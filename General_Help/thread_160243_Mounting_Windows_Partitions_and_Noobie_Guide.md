---
title: "Mounting Windows Partitions and Noobie Guide"
date: 2006-04-14
forum: General Help
---

### Post by danakatheone on 2006-04-14
I followed the instructions in the [http://ubuntuguide.org]("Ubuntu Guide") and I was successfully able to mount my first windows partition with

```
sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222
```

But I can't figure out how to mount my second windows partition. I've tried making a different directory and mounting hda2, but it doesn't work. Any suggestions?


Also, I was wondering if there was a good Ubuntu guide somewhere. I don't really like ubuntuguide.org because it just tells me how to do some stuff, I wanna actually LEARN how to use linux not just be a script kitty.

---

### Post by PriceChild on 2006-04-14
What error message are you getting?

---

### Post by aysiu on 2006-04-14
The Ubuntu Guide's instructions are abbreviated for simplicity's sake and assume your drive is /dev/hda1.

This is more in-depth:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by _linux_ on 2006-04-14
The Ubuntu Wiki pages have much more information. Try checking it out.

---

### Post by danakatheone on 2006-04-14
Thanks

---

