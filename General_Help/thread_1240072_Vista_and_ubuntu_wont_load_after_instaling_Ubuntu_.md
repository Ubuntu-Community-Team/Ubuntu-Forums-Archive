---
title: "Vista and ubuntu wont load after instaling Ubuntu Studio 9.04"
date: 2009-08-14
forum: General Help
---

### Post by g.o.r.d.o on 2009-08-14
hello
 im kind of new to ubuntu OS, this is my problem:
I've been using Windows Vista business on my laptop (HP 6730s), then i instaled Ubuntu 9.04 with WUBI i was enjoyng it and had been working fine for about two months. My problem started few days ago when i instaled Ubuntu Studio 9.04 to give it a try, the thing is  that after instaling it my Vista or ubuntu doesn't load, it goes directly to Ubuntu Studio. I need some help on this please because i have some important files on Vista OS. thank you
:confused:


Ps: Forgive me for any mistakes on my English (it is not my country main language)

---

### Post by soapBAR2 on 2009-08-14
It sounds like you may not have specified multi-boot, or worse, you may have overwritten your data when you installed (in which case, you're up poo creek without a paddle, sorry*). However, if you haven't, you should be fine. Firstly, check if it's still there

```
sudo apt-get install gparted; gparted
```

Will install and run gparted (if it's not already there), which is a great GUI partition editor. Check to see if you still have your vista partition. If you do, great! All you have to do now is either fix grub (hard) or, if you only care about the files and don't want to get back into Vista, you can mount your vista partition in linux and get into it (assuming you don't have encryption - ie, Vista Ultimate + BitLocker). I won't walk you through fixing GRUB (too late, don't have time, sorry), but I'll tell you how to mount your Vista partition:

Open up gparted, and make note of your vista partition location. It will be something like /dev/hda1 or /dev/sda1 or something. Then, to mount the vista partition read only,

```
sudo apt-get install ntfs-3g
sudo mkdir /mnt/vista
sudo chmod 777 /mnt/vista
sudo mount -t ntfs-3g -o ro,noperm,norelatime /dev/yourvistapartitionname /mnt/vista
```

Where
/dev/yourvistapartitionname is the name of your vista partition location from gparted. 

To make it writeable, get rid of the -o ro,noperm,norelatime. If you want to make it permanent, add the following to the end of /etc/fstab using 

```
sudo nano /etc/fstab
```

/dev/yourvistapartitionname /mnt/vista ntfs-3g relatime 0 0

Once you're done, type

```
sudo mount -a
```

And if it works (if you've edited /etc/fstab correctly), you'll have vista mounted in /mnt/vista from now on!

---

### Post by 3rdalbum on 2009-08-14
It sounds like you might have erased your Vista partition; from within Ubuntu Studio can you please give us the output of this command:

```
sudo fdisk -l
```

(that's an L at the end, not an I)

---

