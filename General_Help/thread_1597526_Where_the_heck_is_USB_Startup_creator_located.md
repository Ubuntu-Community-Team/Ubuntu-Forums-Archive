---
title: "Where the heck is USB Startup creator located?"
date: 2010-10-15
forum: General Help
---

### Post by oxf on 2010-10-15
I'm trying to use USB Startup Disk Creator. The problem is I can't find it!
I mean it is installed on my system, the Software Centre shows that but it doesn't appear in Applications>Accessories   or anywhere else I can see.

So where the heck is it????????

---

### Post by ubudog on 2010-10-15
System>Admin>Startup Disk Creator.

---

### Post by FinalShot on 2010-10-15
Pretty sure it will only appear if you're running a live copy, but try System -> Admin -> Startup Disk Creator.

---

### Post by ubudog on 2010-10-15
That's where it is for me.

---

### Post by oxf on 2010-10-15
OK Duuuh...
Yes it's there under System> Admin.
I was expecting it in Applications!
Thanks

---

### Post by ubudog on 2010-10-15
NP, cool.

---

### Post by VMC on 2010-10-15
From a Terminal, can use ```
locate usb-creator-gtk
``` 

Also you can launch it from a Terminal

```
usb-creator-gtk
```

---

### Post by ubudog on 2010-10-15
Also, on a kind of unrelated note, the USB Startup creator only installs ubuntu-version.iso's.  If you want to install, say, Fedora to a flash drive, install the unetbootin package.

```
sudo apt-get install unetbootin
```

---

### Post by oxf on 2010-10-16
> **ubudog said:**
> Also, on a kind of unrelated note, the USB Startup creator only installs ubuntu-version.iso's.  If you want to install, say, Fedora to a flash drive, install the unetbootin package.

```
sudo apt-get install unetbootin
```

OK thanks thats good to know!

---

### Post by ubudog on 2010-10-16
Yeah, it's a good program to have.

---

