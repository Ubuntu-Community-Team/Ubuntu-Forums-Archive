---
title: "How to 'eject' a flash drive"
date: 2011-08-29
forum: General Help
---

### Post by aSystemOverload on 2011-08-29
Hi.  How should I 'safely eject a flash drive'?

---

### Post by aSystemOverload on 2011-08-29
Ignore me, found the UNMOUNT on the right-click.

---

### Post by 3xp10r3r|X13 on 2011-08-29
You can also mount and unmount storage devices using the terminal.

To view available partitions/devices:

```

# fdisk -l

```To mount one:

```

# mount -t (xxx) /dev/xy /mount-point

```replace the "xxx" with the format of your flash drive and "xy" with the actual device.

e.g.: 

```

# mount -t ntfs /dev/sdf1 /home/user/my-drive

```To unmount them just type:

```

# umount /dev/xy 

```
So if you don't want to click your way through the system just use the terminal to do everything a bit faster 
You can surely stick to your methods. I am simply suggesting an alternative :)

---

### Post by spiky001 on 2011-08-29
```
eject /dev/xxx
``` works as well

---

### Post by aSystemOverload on 2011-08-29
I am visually orientated, but I want to move to linux properly, including doing what I can by terminal, so I'll be picking up little bits here and there, thanks.

---

### Post by spiky001 on 2011-08-29
I made a Folder and copied the commands into a doc then save each one for future ref (cant remember them all)

---

### Post by aSystemOverload on 2011-08-30
Yeah, that's kinda what I want to do.  We'll see how well I get on with it.:guitar:

---

