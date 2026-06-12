---
title: "Emulate ISO? (Dameon Tools?)"
date: 2006-04-14
forum: General Help
---

### Post by groovywombat on 2006-04-14
Hello, 
I was wondering if anyone knew a way or a program to emulate an ISO image of say a DVD?  I have some DVD ISO's but a broken DVD burner. hehe thanks

---

### Post by PriceChild on 2006-04-14
Taken from "Tips and Tricks" in the Ubuntu Starter Guide, (go to System > Help )

> 26.&#8195;
                 How do I mount/unmount Image (ISO) files without burning?[LIST=1]
[*]                         To mount Image (ISO) file
                         ```
sudo mkdir /media/iso
sudo modprobe loop 
sudo mount file.iso /media/iso/ -t iso9660 -o loop
```
[*]                         To unmount Image (ISO) file
                         ```
sudo umount [FONT=monospace]/media/iso/[/FONT]
```[/LIST]

---

