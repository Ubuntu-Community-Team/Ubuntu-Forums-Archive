---
title: "disable service from GUI"
date: 2010-06-14
forum: General Help
---

### Post by ammarosu on 2010-06-14
I have upgraded to ubuntu 10.4 i have some issues with it, first how to disable service permanently using GUI, second how can i change root passwd i tried  sudo passwd root does not work, third i have network shared driver i want to mount permanently and create short cut to desktop, any help would be much appreciated.

---

### Post by ThesaurusRex on 2010-06-14
Periods would be a nice addition to your post. Let's divide your question up into three parts:

1. I don't know what you mean by service. Please be more specific.

2. Do you actually know the root password and want to change it, ro can you not remember it? Did you try simply:

```
sudo passwd
```

3. ```
man mount
```

---

### Post by doas777 on 2010-06-14
there isn;t a gui for services that I am aware of. there used to be one, but it didn't work too well.

be sure you know what you are doing before enabling root. you really really don;t need it.

check this out for permenantly mapping smb shares:
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

---

### Post by sites on 2010-06-14
System > Preferences > Startup Applications

Here you'll find a list of things you can modify. Is that what you're looking for?

---

### Post by crjackson on 2010-06-14
> **ammarosu said:**
> I have upgraded to ubuntu 10.4 i have some issues with it, first how to disable service permanently using GUI, second how can i change root passwd i tried  sudo passwd root does not work, third i have network shared driver i want to mount permanently and create short cut to desktop, any help would be much appreciated.

For services:

System > Preferences > Startup Applications

**and/or**

```
sudo apt-get install bum
```

---

### Post by ammarosu on 2010-06-14
thanks guys for reply, what i mean by disabling service is i want to disable avahi-daemon service permanently, root passwd i don't know it i have not logged as the root since i upgrade, tommorrow im going to try sudo apt-get install bum as it's 11 PM now, anyway thx for help.

---

### Post by crjackson on 2010-06-16
avahi-daemon is listed under bum, however on my system it's not activated during bootup. I suppose it's activated when you plug in a new network device or printer.

---

