---
title: "is the swap necessary?"
date: 2006-06-24
forum: General Help
---

### Post by koda on 2006-06-24
Hi everybody!
i've just installed ubuntu without a swap partition (just because my drives are unpartitionalbe for many issues) but then i started worrying about the consequences!
I have two (2) gigas of fisical RAM, is that sufficient?
is it possible to create a swap partition somewhere and then make it run under the already installed system?

thanks a lot!
koda

---

### Post by scanez on 2006-06-24
It is possible to create a swap partition (or swap file) afterwards, but with 2 gigs of ram you'd never have to use it! You're fine without one ;)

---

### Post by Ramses de Norre on 2006-06-24
I have 1gig of ram and my swap partition is hardly ever used, and if it is it are only 18MB or something like that..

---

### Post by dmartinsca on 2006-06-25
You can add a swap partition at any time, although you'd probably need to resize other partitions with something like gparted or partition magic(windows only). After you have created the partition, make sure it is marked as a linux swap partition -- you can check this using the command **fdisk -l** which will list all your partitions. Next run **mkswap /dev/hdXY** followed by **swapon /dev/hdXY** -- this will put your swap partition into use right away. To make sure it's used on every boot you need to edit the file /etc/fstab and add a line something like so:
```
/dev/hdXY               none            swap            sw              0 0
```
In all of the commands above replace /dev/hdXY with the node for your swap partition.
You can also make a swap file inside one of your existing linux partitions like so:
```
dd if=/dev/zero of=/path/to/swap/file bs=1024 count=262144
mkswap /path/to/swap/file
sync
swapon /path/to/swap/file
```
Next add a line to /etc/fstab so the file is used every boot.
In the first command above, count is the size of the swap file to be created in kilobytes, 262144 is 256Mb (256*1024) -- your final swap file will be a bit smaller than this due to space taken up when you run the mkswap command.
A couple of notes - a swap partition really is preferred over a file, they're faster and are seperate from all of your data. With 2Gb of RAM i'd doubt you'd ever use swap but it depends on what you're using the computer for. A busy server may need it. Be careful with the dd command above, it writes zeros to disk where ever 'of=' points to. If it's an existing file, kiss it goodbye, if it's a device node pointing to a partition or disk, kiss all your data goodbye:(

---

### Post by koda on 2006-06-25
that's great!!! just what i was looking for!
i wanted to use the computer for video editing so i was pretty sure i needed some swap (2gigs seems enough)

huge thanks everybody :)
Koda

---

### Post by joshrobinson on 2006-06-25
[QUOTE=koda]that's great!!! just what i was looking for!
i wanted to use the computer for video editing so i was pretty sure i needed some swap (i gave it 16 giga of space. is that too much?)

huge thanks everybody :)
Koda[/QUOTE]

yeah thats a hell of a lot of swap space.. with 2 gigs of ram 1-2gigs of swap is fine, but it may not ever even use that much.. you can use the free command to see what the deal is with how much swap you use during video editing, that way you can make your swap smaller and let you know how much you actually use

```
free
```

---

### Post by garyng on 2006-06-25
for most home use, 1G+ RAM would mean swap is not necessary unless you are running GIMP and editing 20M pixel photo.

Typical usage top out at about 512M RAM(regardless of OS, based on my experience).

---

### Post by spockrock on 2006-06-25
yeah my swap is empty with 2GB of ram, but ubuntu partitioned 6Gb for swap...hmmm... I guess it didnt need that much in hindsight.

---

### Post by strabes on 2006-06-25
I have (only?) 1 gig of ram and i just typed 'free' and swap is not even being used at all right now. It's empty. Although I am just running firefox, listen, and gaim right now...

---

### Post by dcstar on 2006-06-26
[QUOTE=koda]Hi everybody!
i've just installed ubuntu without a swap partition (just because my drives are unpartitionalbe for many issues) but then i started worrying about the consequences!
I have two (2) gigas of fisical RAM, is that sufficient?
.......[/QUOTE]
Check out my rant on this subject......   ;) 

[http://ubuntuforums.org/showpost.php?p=891995&postcount=13](http://ubuntuforums.org/showpost.php?p=891995&postcount=13)

---

### Post by joshrobinson on 2006-06-26
[QUOTE=strabes]I have (only?) 1 gig of ram and i just typed 'free' and swap is not even being used at all right now. It's empty. Although I am just running firefox, listen, and gaim right now...[/QUOTE]

yeah same here on my laptop with 1gb, when i video edit/convert it uses a slight ammount is all

---

