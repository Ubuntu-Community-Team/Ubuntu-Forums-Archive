---
title: "lucid lynx doesn't recognize flash drives or external dvd/cd roms"
date: 2010-05-16
forum: General Help
---

### Post by fwin on 2010-05-16
Hi everyone i just installed 10.04 and everything works fine except that it does not recognize my external cd/dvd rom and my usb flash drives, I already found some threads related to this and they that talk about going to config editor and activating these options: media_auto_run and automount_open

I tried that and still it does not work, any help would be appreciated

Thanks

---

### Post by cuberts on 2010-05-16
> **fwin said:**
> Hi everyone i just installed 10.04 and everything works fine except that it does not recognize my external cd/dvd rom and my usb flash drives, I already found some threads related to this and they that talk about going to config editor and activating these options: media_auto_run and automount_open

I tried that and still it does not work, any help would be appreciated

Thanks
same thing happened to me, but it wasnt lucid lynx that was messed up it was my flashdrive!
If it works on Windows then you must be having a different problem from me

---

### Post by fwin on 2010-05-16
my flash drive works in windows and in ubuntu 9.10 so i don't know what is wrong

---

### Post by techunit on 2010-05-16
It has something to do with the fstab file. ```
/etc/fstab
```

I had the problem on an old net book.

---

### Post by geoffatmk on 2010-05-20
This is not an automount or fstab problem.  Test with a non usb device like an SD card from a camera if you can.  It will work on default installation settings.

The problem appears (from the message logs) to be enumeration of the USB device on the port.  Search for enumerate to find many threads.

G

---

### Post by dino99 on 2010-05-20
sudo update-pciids && update-usbids

then install mountmanager and set your prefs (system admin mountmanager)

---

### Post by geoffatmk on 2010-05-20
Tried this and got

touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

As I suspected there is a permissions problem.  However the file permission show that root can read ans write so ont sure what is going on.

---

### Post by dino99 on 2010-05-20
> **geoffatmk said:**
> Tried this and got

touch: cannot touch `/var/lib/usbutils/usb.ids': Permission denied
/var/lib/usbutils/usb.ids is read-only, exiting.

As I suspected there is a permissions problem.  However the file permission show that root can read ans write so ont sure what is going on.

you have to use "sudo" as usbutils and its files are owned by "root"

i suppose you have previously tweaked the rights on some files or folders and now have some conflicts.

---

### Post by geoffatmk on 2010-05-20
I used sudo.

The file permissions say it is owned by root who has read/write access.

I still get the same response.

I have not tweaked anything, it is a standard installation of lucid lynx.

I have no idea why it is not writing to the file but something is stopping it.  I can root-nautilus and amend the permissions etc (but have not) so it seems to be something between the update process and the permissions.  It is failing on the "touch".

---

### Post by geoffatmk on 2010-05-20
Tried;

gjj@samson:~$ gksudo update-pciids && update-usbids
Downloaded daily snapshot dated     2010-05-10 03:15:02
/var/lib/usbutils/usb.ids.new: Permission denied
update-usbids: download failed
gjj@samson:~$ 


the usb.ids.new did not come up before and the file does not exist.

---

### Post by dondiego2 on 2010-05-20
> **geoffatmk said:**
> I used sudo.

The file permissions say it is owned by root who has read/write access.

I still get the same response.

I have not tweaked anything, it is a standard installation of lucid lynx.

I have no idea why it is not writing to the file but something is stopping it.  I can root-nautilus and amend the permissions etc (but have not) so it seems to be something between the update process and the permissions.  It is failing on the "touch".


I had the same problem after I upgraded with all my usb drives.  I was trying to delete some files on the drive and it said I did not have permission.  I tried to reformat the drives with the same result.  I dual boot with xp so I booted in windows and mounted the drives there and accessed them.  Once I then booted back into linux I could access the without a problem.  Don't know why it happened.

---

### Post by 1script on 2010-09-27
> **dino99 said:**
> sudo update-pciids && update-usbids


It actually has to be 

```
sudo update-pciids && sudo update-usbids
```

Both commands need root permissions

---

### Post by SIOUX410 on 2012-02-03
Hi guys ! 

I had the same error to the command 

$ sudo update-pciids && update-usbids

Downloaded daily snapshot dated 2012-01-18 03:15:02
touch: no se puede efectuar `touch' sobre «/var/lib/usbutils/usb.ids»: Permiso denegado
/var/lib/usbutils/usb.ids is read-only, exiting.

BUT if you run

$ su- root

and then 

# sudo update-pciids && update-usbids

it works fine ! 

anyways the external dvd is not working even the prior command was sucessful

---

