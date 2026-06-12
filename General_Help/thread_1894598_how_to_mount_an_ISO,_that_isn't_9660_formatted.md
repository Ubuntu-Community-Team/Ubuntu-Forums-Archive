---
title: "how to mount an ISO, that isn't 9660 formatted"
date: 2011-12-12
forum: General Help
---

### Post by new to linux help needed on 2011-12-12
Okay, so I have this ISO that is called civV.iso. but I have tried countless attempts to mount it(if that is the proper term for finding all the files within). And they all have came up short, i have used "Gmount-iso" and i get this error

"In some cases useful info is found in syslog - try
       dmesg | tail  or so"

1.) what does it mean?
2.) how do i solve this?
3.) is this the best way to go about installing a windows game on linux that isnt on steam or other third party application?
4.)should i use the terminal?
5.) How should i get it to the 9660 format?
6.) How do i unpack all of the files from an ISO

Playonlinux is an amazing program but it will not help me with the ISOs.
i already have the iso on a CD.
this last one is off subject but how do i reset my root password, i think i misspelled it..... i know im sad, haha.

---

### Post by oldtimer7777 on 2011-12-12
What I use is playonlinux, it is located about 1/3rd the way down the new user checklist:

[https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](https://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)

You will need to burn the iso to a dvd-r to install it in PlayOnLinux.

Brasero might work for burning it to a disc.  Otherwise you may have to burn it back in windows to a disc to install it with PlayOnLinux.

> **new to linux help needed said:**
> Okay, so I have this ISO that is called civV.iso. but I have tried countless attempts to mount it(if that is the proper term for finding all the files within). And they all have came up short, i have used "Gmount-iso" and i get this error

"In some cases useful info is found in syslog - try
       dmesg | tail  or so"

1.) what does it mean?
2.) how do i solve this?
3.) is this the best way to go about installing a windows game on linux that isnt on steam or other third party application?
4.)should i use the terminal?
5.) How should i get it to the 9660 format?

this last one is off subject but how do i reset my root password, i think i misspelled it..... i know im sad, haha.

---

### Post by RealityMaster on 2011-12-12
Have you tried to mount it from the command line?

```
sudo mount -o loop -t iso9660 /path/to/iso /empty/folder/to/mount/in
```

If it's not 9660 do you know what type it is?

---

### Post by nothingspecial on 2011-12-14
Duplicate Thread. Closed.

---

