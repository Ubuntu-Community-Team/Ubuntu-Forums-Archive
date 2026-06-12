---
title: "Mounting a USB key"
date: 2012-07-14
forum: General Help
---

### Post by markeee on 2012-07-14
Hi
I know this has been covered extensively and numerous forum posts/guides out there..and I did read some guides/help

I've also don it before.but cant remember exactly what I didbeen a few years since I used ubuntu..back to it now anyway :)

Plugged in my 16gb SanDisk cruzer and nothing so i typed sudo dmesg | grep sd which returns saying sdc

then i tried mounting sdc 

sudo mount /dev/sdc1 -t vfat /media/external and it says sdc1 does not exist?

not sure what I am doing wrong-  :(  please help!!

many thanks

---

### Post by sudodus on 2012-07-14
> **markeee said:**
> Hi
I know this has been covered extensively and numerous forum posts/guides out there..and I did read some guides/help

I've also don it before.but cant remember exactly what I didbeen a few years since I used ubuntu..back to it now anyway :)

Plugged in my 16gb SanDisk cruzer and nothing so i typed sudo dmesg | grep sd which returns saying sdc

then i tried mounting sdc 

sudo mount /dev/sdc1 -t vfat /media/external and it says sdc1 does not exist?

not sure what I am doing wrong-  :(  please help!!

many thanks

If the USB key contains a partition /dev/sdc1 with a file system, it should be recognized as a storage device, and you should see it on the left panel of your browsing tool. Anyway, try the following command
```
sudo fdisk -lu
```
Please post the output and put it between CODE tags (mark the text and click on the # icon at the top of the editing window).

I usually put the options before the parameters, and the last parameter must be an existing path, so I would try these commands

```
sudo mkdir /mnt/usb-key
sudo mount -t vfat /dev/sdc1 /mnt/usb-key
```
or use automount
```
sudo mount -t auto /dev/sdc1 /mnt/usb-key
```

But maybe you need to create or repair the partition or the file system. Does it work in Windows? Try to repair it from Windows with ```
chkdsk /f
```

Or maybe there is some hardware error, bad connection (bad USB port or cable) or bad hardware in the key.

---

### Post by Tank Jr on 2012-07-14
Cruzer? Isn't that the one that comes with the U3 file system that shows up like a CDROM under Windows?
I had one of these and Ubuntu did not like it. I had to get a friend to delete the U3 stuff and possibly format it using their Windows laptop before I could use the USB drive.

---

### Post by bazzal1941 on 2012-07-14
Not sure if I'm being any help, insert usb and type:

fdisk -l

It should at least confirm you are using the correct device.

---

### Post by bazzal1941 on 2012-07-14
Sorry ignore that nonsense somebody who knows what they are talking about has answered.

---

### Post by sudodus on 2012-07-14
> **Tank Jr said:**
> Cruzer? Isn't that the one that comes with the U3 file system that shows up like a CDROM under Windows?
I had one of these and Ubuntu did not like it. I had to get a friend to delete the U3 stuff and possibly format it using their Windows laptop before I could use the USB drive.
Ubuntu can manage such USB keys (although it cannot run the software for U3). I have two of them, plugged one in and ran ```
df
```
```

/dev/sr1                  6828      6828         0 100% /media/U3 System
/dev/sdg2              5234980   4885160    349820  94% /media/USB-OS
/dev/sdg1              8794976   6990072   1804904  80% /media/USB-DATA
```
It also automounted and showed up in the file-browser.

There is some other problem with *markeee*'s USB key.

---

### Post by sudodus on 2012-07-14
> **bazzal1941 said:**
> Sorry ignore that nonsense somebody who knows what they are talking about has answered.
It is a good piece of advice - we were writing answers at the same time, no need to be sorry about that :-)

---

