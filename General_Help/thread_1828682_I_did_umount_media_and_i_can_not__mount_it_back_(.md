---
title: "I did umount media and i can not  mount it back :("
date: 2011-08-19
forum: General Help
---

### Post by IT Support on 2011-08-19
I umount my media (it`s called IMPORTANT) and when i  am  trying  mount it back  terminal sad that  IMPORTANT is not exist 


i did it like this 

sudo mount /dev/sda5


i know that my  IMPORTANT media is on the sda5 


 how i will back  mount my media ??

[img]http://ipovne.com/other/newbie.gif[/img]

---

### Post by dave01945 on 2011-08-19
it looks like your command is missing some parameters

```
sudo mount /dev/sda5 /dir/to/mount
```

to mount drives you need to specify the drive (/dev/sda5) and after that you need to tell it a directory where to mount usually in /media/ but you may need to make a new directory in /media

```
mkdir /media/newdirectory
```

also if it's anything like mine you might just be able to go into the file manager and on the left there should be a places bar in that bar i usually have all my drives just click it to mount if not the above will work

---

### Post by IT Support on 2011-08-19
> **dave01945 said:**
> it looks like your command is missing some parameters

```
sudo mount /dev/sda5 /dir/to/mount
```

to mount drives you need to specify the drive (/dev/sda5) and after that you need to tell it a directory where to mount usually in /media/ but you may need to make a new directory in /media

```
mkdir /media/newdirectory
```

also if it's anything like mine you might just be able to go into the file manager and on the left there should be a places bar in that bar i usually have all my drives just click it to mount if not the above will work

thank you my friend but wile u wrote it  i did awful job :D :D
i make new dir how u  write above  

mkdir /media/name
mount /dev/sda5 /media/name 

anddddddddddddddddddd


finally i make something  awful :D 

rm -r /media/name  


and how u feel  i delete all what i had there :D


i l laugh because i had backup everything in my usb storage disk   :D

from today i will be carefully  :D

i am stupid :(

---

### Post by dave01945 on 2011-08-19
it's always good to have back up's especially if it's **important** :P

---

### Post by IT Support on 2011-08-19
> **dave01945 said:**
> it's always good to have back up's especially if it's **important** :P

yeah it very good when you delete something and  than you have  backup  to restore  it back :)

---

