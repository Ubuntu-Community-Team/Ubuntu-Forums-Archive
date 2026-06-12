---
title: "Let GNOME automatically mount encrypted drive after login"
date: 2011-03-14
forum: General Help
---

### Post by Prodoc on 2011-03-14
Hi,

I've set up an encrypted drive using the "Disk Utility" application. This added a drive to the places menu as expected. I would like GNOME to automatically mount this drive after login, to a different mount point "/mnt/Data Backup" instead of the default one "/media/Data Backup". Reason for the auto mount is to prevent having to do this manually every time I login and prevent applications using the drive by default from chocking when I forgot to do so. Reason for the different mount point is to prevent the drive from appearing on the desktop.

I managed to let the drive to be mounted during boot, instead of after login, using the following config:

/etc/crypttab:
```
sdd_crypt      UUID=7f8d3cce-9509-4526-9fab-fbcb46dc3f07       none    luks
```
/etc/fstab:
```
/dev/mapper/sdd_crypt  /mnt/Data\040Backup     ext4    defaults        0       2
```

The drawback of this approach is that I would need to provide a password during boot twice. Once to unlock the encrypted drive, once to actually login.

There used to be an application called "gnome-mount" which might have done the trick but it is not available any more for Ubuntu 10.10. The application "Storage Device Manager" (pysdm) does nothing more then altering "/etc/fstab" resulting in the same situation as above.

What can I do to achieve what I want in a clean way?

---

### Post by Prodoc on 2011-03-15
Playing around some more made me give the following a try:

/etc/rc.local:
```
cryptsetup luksOpen -U 7f8d3cce-9509-4526-9fab-fbcb46dc3f07 sdd_crypt
mount /dev/mapper/sdd_crypt "/mnt/Data Backup"
```
This, however, did not work. Without any errors given to work on.

Because of this I now resolved to using a key file to unlock the encrypted drive using the following tutorial: [http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile](http://www.howtoforge.com/automatically-unlock-luks-encrypted-drives-with-a-keyfile)

Though not perfect, having a key file around isn't and doesn't feel right, it works for the time being.

The only thing left now is getting rid of the drive entry directly in the "Places" menu. For some reason GNOME still wants to provide me with the option to mount the drive even though "/etc/fstab" already took care of this. Any ideas why this is still happening and any suggestions on how to get rid of it?

---

