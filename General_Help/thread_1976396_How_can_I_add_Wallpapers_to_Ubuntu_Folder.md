---
title: "How can I add Wallpapers to Ubuntu Folder"
date: 2012-05-08
forum: General Help
---

### Post by AbuAkram on 2012-05-08
Hi

There is this option under 12.04 where the Wallpaper changes randomly 

I would like to add some more wallpapers to it, but can't seem to find where ubuntu stores it's wallpapers

Can anyone help me out?

Thanks

---

### Post by Enigmapond on 2012-05-08
They are in usr/share/backgrounds. You need root access to move anything to his folder so when you are ready, do:
```
gksu nautilus
```

---

### Post by AbuAkram on 2012-05-08
thanks alot

mission accomplished

---

### Post by Dar Um on 2012-05-29
> **Enigmapond said:**
> They are in usr/share/backgrounds. You need root access to move anything to his folder so when you are ready, do:
```
gksu nautilus
```

I have done the following commands:
sudo su
gksu nautilus usr/share/backgrounds

then added new pictures into the folder and closed terminal
 and 
didn't find them among those wallpapers which are changing randomly

---

### Post by gandalf3 on 2012-08-31
where is the option for randomly changing the pictures? i can't find it. :confused:

EDIT:

oh wait, is it that one with the clock that says "randomly changes throughout the day"? i thought that was changing the individual picture.. :oops:

---

### Post by Matt2c on 2012-09-26
Oll Korrect. Thank You.

---

