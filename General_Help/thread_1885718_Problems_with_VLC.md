---
title: "Problems with VLC"
date: 2011-11-23
forum: General Help
---

### Post by Jayhawker on 2011-11-23
My VLC accepted DVDs, but accidentally I have changed /dev/sr1 for sr2, and now I don't remember where to go to fix it.

Please, what's /dev/sr1, and how can I find it again?

Thanks a lot

---

### Post by claracc on 2011-11-24
/dev/sr1 is where is your optical device.

When you want to play a CD or DVD, you run VLC, media, open disk, select the kind of disk: DVD or CD and then the kind of device, where you have to write /dev/sr1 .

Other place to where to put your optical device is: tools, preferences, input and codecs, default optical device, and there you write /dev/sr1

---

### Post by Jayhawker on 2011-11-24
Thanks for your help, but when I add dev/sr0 or sr1 a pop up says to me I must check the register because VLC can not work. Where is the register, and how to fix all this mess?

Thank You again



> **claracc said:**
> /dev/sr1 is where is your optical device.

When you want to play a CD or DVD, you run VLC, media, open disk, select the kind of disk: DVD or CD and then the kind of device, where you have to write /dev/sr1 .

Other place to where to put your optical device is: tools, preferences, input and codecs, default optical device, and there you write /dev/sr1

---

### Post by claracc on 2011-11-24
I think you can do the following:

Introduce the dvd you want to play in your optical device, then you open an xterm and write mount, you'll find a line as: > /dev/sr0 on /media/cdrom0 type udf (ro,nosuid,nodev,utf8,user=clara)


Then open VLC, go to media, open disk, select dvd, write in disk device: /media/cdrom0 ( or the filesystem when it is mounted), enter and then play. VlC will work (I think). Then write this filesystem in tools, preferences, input and codecs, default optical device, there you write /media/cdrom0

In xterm, you can also write df -h (with CD or DVD introduced), I obtain the following > clara@clara1:~$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda5              24G  6,0G   17G  27% /
none                  999M  296K  999M   1% /dev
none                 1003M  840K 1002M   1% /dev/shm
none                 1003M  208K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sda7              46G   23G   21G  54% /home
/dev/sr0              7,6G  7,6G     0 100% /media/cdrom0

Last line is what you have note: /dev/sr0 or /media/cdrom0 is what you have to write is disk device or default optical device

---

### Post by claracc on 2011-11-24
Note, /dev/sr0 not dev/sr0 > I add dev/sr0 or sr1

---

