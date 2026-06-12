---
title: "[errno 13] with USB Creator"
date: 2009-11-09
forum: General Help
---

### Post by Calixte on 2009-11-09
I'm using Ubuntu karmic netbook remix. I can't manage to install ubuntu on my USB pendrive
I get this error every time:
```
An uncaught exception was raised:
[Errno 13] Permission denied: '/media/cdrom0/casper'
```
It may have something to do with the fact that ubuntu detects my usb devices as cdrom0 (I have to mount them manually).

I tried```
calixte@Lucy:~$ sudo chmod 777 /media/cdrom0/casper
chmod: cannot access `/media/cdrom0/casper': No such file or directory

```
I also tried:
```
calixte@Lucy:~$ sudo chmod 777 /media/cdrom0

```
No reaction from the teminal, so I guessed I had worked.

My next try resulted in the error:
```
An uncaught exception was raised:
[Errno 13] Permission denied: '/media/cdrom0/ldlinux.sys'
```

Do you have an idea of what I should do?

Thanks,
Calixte

PS: One idea I had was to try to run the 'USB Startup Disk Creator' as root, ut I don't know how to do that

---

### Post by Calixte on 2009-11-10
Bump...

---

### Post by rajeev1204 on 2009-11-11
Are you running the usb creator program from the menu?

Does it open ?

Also , can i see the output of command mount from a terminal.Please keep the usb plugged in.

---

### Post by sakubas on 2009-11-11
try create a new filesystem before create the cd image:

```

#umount /dev/sdb (chek the "mount" command output to select the device)
#mkfs.ext3 /dev/sdb

```

and try again



(sorry my english is horrible - :))

---

### Post by Calixte on 2009-11-11
> **rajeev1204 said:**
> Are you running the usb creator program from the menu?

Does it open ?

Also , can i see the output of command mount from a terminal.Please keep the usb plugged in.

Yes, I used the usb creator program from the menu (GTK version).
I get the error just after clicking "make startup disk"It seems as if the program does not have root privileges.

@sakubas

Yep, I get the same problem :???:

---

### Post by Calixte on 2009-11-11
Ok, I did a couple of things (reformatted twice, first ext2 then fat32, mounted, unmounted, reboot, etc.) and finally managed to make things work (using "sudo usb-creator-gtk")
 
Now, I have a new problem: The seems to do it's job correctly until  the end when a dialog pops up and says "checksums do not match"

Do you know what that means?

---

### Post by Calixte on 2009-11-11
When I try to boot from the USB, I get an error "kernel not found: Linux" :???:

---

### Post by rajeev1204 on 2009-11-12
Try the program unetbootin instead of usb creator.Works good.

---

### Post by sakubas on 2009-11-12
If the system have problems finding the kerner then you have a creation problem... Try using  unetbootin... ( rajeev1204 )

---

### Post by dlbueno on 2011-01-01
> **Calixte said:**
> Ok, I did a couple of things (reformatted twice, first ext2 then fat32, mounted, unmounted, reboot, etc.) and finally managed to make things work (using "sudo usb-creator-gtk")

I had the same problem and it appears to be that formatting the USB disk with a FAT filesystem works, while ext2 (which I tried first) does not. I have no idea whether ext4 works.

To format the disk, right-click on it in nautilus and click 'Format...'.

---

### Post by C.S.Cameron on 2011-01-01
Have you checked the downloaded iso's MD5SUM?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

