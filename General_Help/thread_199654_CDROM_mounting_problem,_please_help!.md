---
title: "CDROM mounting problem, please help!"
date: 2006-06-19
forum: General Help
---

### Post by saigon_82 on 2006-06-19
Hello!

I have succesfully changed from my old (and pretty buggy) Windows ME to Ubuntu.
I have read all the documentations of Ubuntu and I searched this forum and Google for my problem, but I haven't found a solution to this.

I want to install the build-essential package to have GCC (I installed Ubuntu through Alternate Install CD), but when I try to mount the Ubuntu CD in the Terminal, I get the following error:
> mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
The command I used was **mount /dev/hdc**.
I have played a bit in the fstab file to see if the mounting works, but I guess I did something wrong. Here's my fstab entry:
> /dev/hdc        /media/cdrom0   iso9660 ro,user,noauto  0       0

Please help me with this, thank you!
Any kind of help is very appreciated.

---

### Post by metafile on 2006-06-19
Can you access /media/cdrom0? By defalut, Ubuntu should automatically mount cd-rom devices after you insert a disc.
Anyway, you used mount command wrong: it must be something like
```
mount -t iso9660 /dev/hdc /home/user/cdrom
```
and you shold create /home/user/cdrom directory before that.

---

### Post by saigon_82 on 2006-06-19
I can access /media/cdrom0 but Ubuntu isn't mounting the CD automatically.
I still get the same error, and your command should be like this:
> mount -t iso9660 /dev/hdc /home/user/cdrom

Thanks anyway.

---

### Post by metafile on 2006-06-19
Maybe, bad disc? Did you try to read it in any other OS?

---

### Post by saigon_82 on 2006-06-19
Yes, I tried the CD in my other computer which has Windows XP installed. Works fine.

---

### Post by saigon_82 on 2006-06-19
Anyone? Please don't tell me to go back to my buggy Windows :(
I can't find a solution to this, but I think I have to change or tweak my fstab file.

Thanks anyway!

---

### Post by metafile on 2006-06-19
I`ve just tried
```
mount -t iso9660 /dev/hdc /home/user/cdrom
```
and it worked for me.
My fstab entry is
```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

If this won`t help, you should probably check, if you can mount another cd (not the disk with ubuntu). If you do, it must be a particular disk problem (try to re-burn it or something), if not, something`s must be wrong with your hardware.

---

