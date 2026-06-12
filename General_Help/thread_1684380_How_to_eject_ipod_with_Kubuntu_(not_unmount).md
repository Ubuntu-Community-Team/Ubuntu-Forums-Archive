---
title: "How to eject ipod with Kubuntu (not unmount)"
date: 2011-02-09
forum: General Help
---

### Post by quickk on 2011-02-09
I have an ipod shuffle that will only charge if I eject it.   This is easy to do with Ubuntu as I only have to right click on the ipod icon and select "eject."  If I select unmount instead, the ipod does not charge.   

I am now trying out kde 4.6 with Kubuntu, but cannot see a way to eject.  There is an option to safely remove the ipod, but this does not correspond to the eject option in Ubuntu as the ipod does not subsequently charge.

Anyone know how to do this?

Thanks!

---

### Post by tredegar on 2011-02-09
In a terminal try **eject /path/to/ipod**
eg
**eject /media/ipod**

---

### Post by [Snc] on 2011-02-09
If you have an icon for your iPod in File Browser, right click and select "Safely Remove Drive".

---

### Post by tredegar on 2011-02-09
> If you have an icon for your iPod in File Browser, right click and select "Safely Remove Drive".
Yes, but the OP is running **K**ubuntu where R-click - Safely Remove just unmounts the device, it does not "Eject" it as the gnome desktop does.

---

### Post by quickk on 2011-02-12
Hi everyone, 

  Thank you for the suggestion, tredegar, unfortunately it does not work.  When I try to eject the ipod via the command line I get the following error:
```
eject: tried to use `/media/ipod' as device name but it is no block device
eject: tried to use `./ipod' as device name but it is no block device
eject: unable to find or open device for: `ipod'
```

I am sure the path is correct, and the device name is correct.   It's too bad there isn't an easy way to "eject" the ipod as this is the only way I can charge it without using iTunes.

---

### Post by cunaldo on 2011-03-16
This is how I do it. At a command prompt:

```
$ mount
```Shows all the devices mounted, including my ipod mounted at /dev/sdc2

```
$ sudo eject /dev/sdc2
```Should eject the hardware and allow you to charge away. Hope that helps.

---

### Post by quickk on 2011-03-25
Thanks cunaldo!  That worked perfectly.

---

