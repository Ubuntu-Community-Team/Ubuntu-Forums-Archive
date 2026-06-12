---
title: "How can I mount a CD Drive from the command prompt?"
date: 2006-03-07
forum: General Help
---

### Post by ttallos on 2006-03-07
How can I mount a CD Drive from the command prompt?

---

### Post by codejunkie on 2006-03-07
[QUOTE=ttallos]How can I mount a CD Drive from the command prompt?[/QUOTE]
```
sudo mount /dev/**cdrom** /media/cdrom
```
replace **cdrom** with the location of your drive, for example mine are /dev/hdc and /dev/hdd.

---

### Post by ttallos on 2006-03-07
Thanks you are great! It seems to me there was a fdisk command to list all the drives but I forgot. I tried fdisk -l but since i have a raid array5 I get no responce....Hmmmm

---

### Post by ttallos on 2006-03-07
mount /dev/hdd worked I just guessed. Thanks for your help

---

### Post by codejunkie on 2006-03-07
[QUOTE=ttallos]Thanks you are great! It seems to me there was a fdisk command to list all the drives but I forgot. I tried fdisk -l but since i have a raid array5 I get no responce....Hmmmm[/QUOTE]
try```
sudo fdisk -l
```the fdisk command needs to be run as root but the fdisk -l doesn't show cdrom drive locations on mine only harddisks.

---

### Post by ttallos on 2006-03-07
After mounting CD rom drive how do I read it??? I just want to copy 4 files.
I get cant find in /etc/fstab or /etc/mtab

---

### Post by ttallos on 2006-03-07
Thanks you rock! Do you know the answer to above request??

---

### Post by ttallos on 2006-03-07
I figured it out myself here it is..   /media/cdrom0  !!!!

---

### Post by taurus on 2006-03-07
To copy files from CD to your home directory from a command prompt,
```

cd /mnt/cdrom0
cp <file_1> ~/
cp <file_2> ~/
cp <file_3> ~/
cp <file_4> ~/

```

---

### Post by ttallos on 2006-03-07
Thanks that command works great.

---

