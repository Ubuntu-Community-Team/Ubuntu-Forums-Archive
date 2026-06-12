---
title: "Needed a permanent link !!"
date: 2009-07-23
forum: General Help
---

### Post by chinmaya_n on 2009-07-23
i needed a permanent link or shortcut to a folder on to my desktop !!

The folder is present in a partition which is not automatically mounted... and should be mounted manually!! 

Can any one suggest a way ?:)

Thanx

---

### Post by sisco311 on 2009-07-23
In nautilus, right click on the folder > Make link, Cut and Paste the link to the new location(rename it if you want).

or, open a terminal:
```
ln -s -T /media/path/to/dir /path/to/link/name
```


EDIT:
On the desktop you can create a new launcer. In the command field write:
```
gnome-open /path/to/dir
```

---

### Post by Johnny B on 2009-07-23
try this:
> 
#!/bin/bash
drivename=
folder=
if [ -d /media/$drivename ] ;then
          nautilus /media/$drivename/$folder
else
          gksu mount /dev/hdX /media/$drivename
          nautilus /media/$drivename/folder
fi


---

### Post by chinmaya_n on 2009-07-23
Mr Jhonny B

Can u tel me what that code is and what that will do ??

Thanx Mr Sisco311 !

---

### Post by Johnny B on 2009-07-23
sorry, i forget how hard scripts are to read.

this will test to see if the drive is mounted
if not, it will mount the drive
then open the file manager to your directory

[ the name of your drive, folder and drive device need to be filled in ]

---

### Post by chinmaya_n on 2009-07-25
Your script is very nice!
I tried the script with some manipulations.

```
#!bin/bash
drivename=Entertainment1
folder1=Songs
if [[-d /media/$drivename]] 
 then
 nautilus /media/$drivename/$folder1
else
 gksu mount /dev/sda5 /media/$drivename
 nautilus /media/$drivename/$folder1
fi
```

When i used this script it showed an error :
 [COLOR="Red"]The folder contents could not be displayed.
 "Songs" could not be found. Perhaps it has recently been deleted.[/COLOR]
It showed this error when the drive was not mounted. But it worked when the drive was mounted !!

Can u plzz help!:P

---

### Post by chinmaya_n on 2009-07-26
I forgot to mention that i saved the file with .sh extention...... 
and i run the file by using "sh script.sh"

---

### Post by Johnny B on 2009-07-26
oops... /media/Entertainment1 will always exist even when the drive is not mounted, it should read:

> #!bin/bash
drivename=Entertainment1
folder1=Songs
if [[-d **/media/$drivename/folder1**]] 
 then
 nautilus /media/$drivename/$folder1
else
 gksu mount /dev/sda5 /media/$drivename
 nautilus /media/$drivename/$folder1
fi

---

### Post by chinmaya_n on 2009-07-26
I'm very sorry to say u.....

It showed the same error !!

I observed ...
/media/Entertainment1 doesnt exist always, it only gets created only when it is mounted (/dev/sda5)

---

### Post by Johnny B on 2009-07-26
i think maybe its because /media/Entertainment1 doesnt always exist
> #!bin/bash
drivename=Entertainment1
folder1=Songs
if [[-d **/media/$drivename/folder1**]] 
 then
 nautilus /media/$drivename/$folder1
else
**gksu mkdir /media/$drivename**
 gksu mount /dev/sda5 /media/$drivename
 nautilus /media/$drivename/$folder1
fi

---

### Post by chinmaya_n on 2009-07-27
It worked !! :p

Thanx 'johnny b' !!

---

### Post by chinmaya_n on 2009-07-29
@ Old_Gray_Wolf

Yes that was my actual purpose !!

@ Whiffle

If we do as u said, it wont automount but in the nautilus it will showup the partition and asks for the password to mount the drive...!!  My purpose will not be served !

---

### Post by chinmaya_n on 2009-08-01
Worked fine ....... :popcorn:

Thanx 2 everyone !! :)

---

