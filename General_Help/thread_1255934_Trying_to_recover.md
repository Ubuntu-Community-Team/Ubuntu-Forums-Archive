---
title: "Trying to recover"
date: 2009-09-02
forum: General Help
---

### Post by jordank on 2009-09-02
hi there. my girlfriend downloaded some programs in windows, and she screwed up her boot order, so now when she starts up her computer all she sees is a mouse.

So i decided i would try to use the ubuntu live disc to access her files, and saved the important ones to my external hard drive, and then erase and reinstall windows.

However, when i attempt to access her harddrive from ubuntu, i get this error:

unable to mount the volume ACER.

logfile indicates unclean shutdown (0,0) Failed to mount '/dev/sda2': operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: choice 1: if you have windows then disconnect the external devices by clicking on the safely remove hardware icon in the windows taskbar then shutdown windows cleanly. Choice 2: if you don't have windows then you can use the 'force' option for you own responsiblity. For example type on the command line: Mount - t ntfs-3g /dev/sda2 /media/ACER -o force or add the option to the relevant row in the /etc/fstab file: /dev/sda2 /media/Acer ntfs-3g defaults, force 0,0

so i take the error's advice, and i typed what it said to in the terminal, and it gave this error.

ubuntu@ubuntu:~$ sudo mount -t ntfs-3g /dev/sda3 /media/ACER -o force
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/ACER: No such file or directory
FUSE mount point creation failed
Unmounting /dev/sda3 (DATA)


what should i do to force mount the existing hard drive so that i can recover files from it?

Thanks

---

### Post by lisati on 2009-09-02
Does Windows show up in the Grub menu or are you taken straight to xubuntu?

If a grub menu doesn't show up, try pressing "Esc" and then start Windows if you can. Then shut down windows properly next time.......

---

### Post by jordank on 2009-09-02
no, i'm just using the live disc, so ubuntu isn't even actually installed on my computer, i'm just using it to try to access the existing files on the hard drive.
what i'm asking is how to force mount the harddrive in to ubuntu so i can access what is on it

---

### Post by nothingspecial on 2009-09-02
I don`t know if ntfsprogs is included on the live cd but if it is try

```
sudo ntfsfix /dev/sda3
```

---

### Post by gradinaruvasile on 2009-09-02
I think it is not included, but u can install packages from the live cd. just go to system->administration->software sources, tick everything on the "ubuntu software" tab, click close and reload.
Then u can install whatever u want.

Of course it works only if ubuntu can use ur net card ...

---

