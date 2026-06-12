---
title: "How to format flash drives/memory cards in ubuntu ?"
date: 2010-01-04
forum: General Help
---

### Post by Raik.48 on 2010-01-04
Hi!

Can anyone please tell me how to format flash drives in ubuntu. In windows there was a "format" on the right click menu but I did not find one in ubuntu. i am using ubuntu jaunty.

Any help would be appreciated.

Thank You.

---

### Post by howefield on 2010-01-04
You could use GParted.

Install with Synaptic Package Manager, and you will then find it in your System > Administration menu.

---

### Post by Raik.48 on 2010-01-04
thanks a lot

---

### Post by t0p on 2010-01-04
Install **gparted**.  Do this through **System > Administration > Synaptic Package Manager**; alternatively, open a terminal (**Applications > Accessories > Terminal**) and type in the command:

```
sudo apt-get install gparted
```

Once installed, you'll find it under **System > Administration > Partition Editor**; or you can hit **Alt+F2** and type into the box that appears:

```
gksudo gparted
```

---

### Post by 3rdalbum on 2010-01-04
Format your drive to "fat32" format if you want to use it across Windows, Linux and Mac OS.

---

