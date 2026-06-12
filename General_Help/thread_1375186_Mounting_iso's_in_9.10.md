---
title: "Mounting iso's in 9.10"
date: 2010-01-07
forum: General Help
---

### Post by Twiggeh on 2010-01-07
So, i've made backups over the years of old videogames and i thought i'd throw some over to my new laptop (mainly Fallout 1 & 2) so i can play while sitting on the train etc.

But i just cant mount any images, i've found some "mount ***"-commands, like 3-4 different variants but none worked.
Then i launched synaptic and downloaded som different programes (gmountiso, furious *something something* etc) but they wont mount my image.
And the image im trying to mount is an .bin-file, i didnt care about saving my .cue file but i can make a new one if it has to be there.

So, do you guys have any clue on what i could try next? i'd rather not walk around with a ton of CDs when i could have it all on my HDD..

---

### Post by llawwehttam on 2010-01-07
Have you tried 
```
sudo mount -o loop ~/Desktop/'name you want to call the mounted disk' /media/cdrom0
```

---

### Post by Twiggeh on 2010-01-07
> **llawwehttam said:**
> Have you tried 
```
sudo mount -o loop ~/Desktop/'name you want to call the mounted disk' /media/cdrom0
```


That prints the following :

> mount: you must specify the filesystem type

---

### Post by Jose Catre-Vandis on 2010-01-07
Try this

[http://ubuntuforums.org/showthread.php?t=93706](http://ubuntuforums.org/showthread.php?t=93706)

---

### Post by shazbut on 2010-01-07
or install gmountiso from the repos, for graphical simpleness.

---

### Post by mkvnmtr on 2010-01-07
I believe what I use is gISOmount. It is in the repositories. Very simple and does some other things also

---

### Post by OllyDBG on 2010-01-08
Try this

```
cd /media
mkdir iso
mount <filename.iso> /media/iso -t iso9660 -o loop
```

---

### Post by kenox on 2010-01-08
Where you root when you ran the command?(sudo?)

If so... probably the filesystem is not iso9660. It is not necessary to specify the filesystem it is usually autodetected!

Try: ```
sudo mount -o loop </path/file.iso> /mnt
```

if "you must specify the filesystem type" error occurs

Try: ```
sudo mount -t iso9660 -o loop </path/file.iso> /mnt
```

if "wrong fs type, bad option...." error occurs it is likely not an iso9660 filesystem or is corrupt.

check the folder /mnt for any files in your file browser (nautilus) after each command!

---

### Post by Grenage on 2010-01-08
I frequently mount ISOs on my laptop; I use **OllyDBG**'s method.

---

