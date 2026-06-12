---
title: "Unetbootin does not find USB"
date: 2010-12-17
forum: General Help
---

### Post by feddozz on 2010-12-17
Hi
as per title UNetbootin did not show any USB devices in the list although there was one inserted and recognised by Ubuntu 10.10.
ideas?
Tnx

---

### Post by wilee-nilee on 2010-12-17
> **feddozz said:**
> Hi
as per title UNetbootin did not show any USB devices in the list although there was one inserted and recognised by Ubuntu 10.10.
ideas?
Tnx

It has to be mounted is it?

---

### Post by feddozz on 2010-12-17
> **wilee-nilee said:**
> It has to be mounted is it?

It was mounted. I could browse the files.

---

### Post by wilee-nilee on 2010-12-17
> **feddozz said:**
> It was mounted. I could browse the files.

So do you have more then one partition on the thumb, and what files are you referring to and where are they.

You should see the thumb icon on the desktop before opening unetbootin.

---

### Post by feddozz on 2010-12-17
> **wilee-nilee said:**
> So do you have more then one partition on the thumb, and what files are you referring to and where are they.

You should see the thumb icon on the desktop before opening unetbootin.

I just have a single partition. I insert the thumb and a folder opens showing the files in it. then i open unetbootin and it does not show any usb devices in the drop down menu.

Does it need to have a specific file system? Fat, ext?

---

### Post by wilee-nilee on 2010-12-17
> **feddozz said:**
> I just have a single partition. I insert the thumb and a folder opens showing the files in it. then i open unetbootin and it does not show any usb devices in the drop down menu.

Does it need to have a specific file system? Fat, ext?

It should be an fat32 partition empty of any other files.

I use gparted to format my HD, thumbs...etc. Gparted just needs to be installed in a installed Ubuntu, in the terminal. You can format it with the disc utility or a right click on the icon, as well, in Ubuntu.
```
sudo apt-get install gparted
```

Just be sure your formatting the thumb, and other issues when using it.

---

### Post by feddozz on 2010-12-20
Thanks, it worked! There were some files in the USB. I thought UNetbootin would format the USB itself like similar apps do.

After format it recognised it.
Bye

---

### Post by amsterdamharu on 2010-12-20
The version I use is non destructive to the drive, it will ask you if it's ok to overwrite a file if it wants to copy a file that exists already.

There is a change something can go wrong so make sure to make a backup of all importaint files on the stick.

```
me@computer:/home/me$ dpkg-query -W | grep unetbootin
unetbootin    408-1ubuntu0.10.04.2
unetbootin-translations    408-1ubuntu0.10.04.2

```

---

