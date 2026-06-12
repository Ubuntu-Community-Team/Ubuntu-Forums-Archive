---
title: "sudo*nautilus: command not found"
date: 2010-03-28
forum: General Help
---

### Post by vickoxy on 2010-03-28
Ok-this is odd. Suddenly command **sudo nautilus** is not working any more.
Sorry-i have problem with space key-no idea what it is...

gksu nautilus opens file manager:
```
asus@asus ~ $ gksu nautilus
(nautilus:3491): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

```

Also
```
asus@asus ~ $ sudo dbus-launch nautilus

(nautilus:3576): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-open-terminal extension
Initializing nautilus-gdu extension

```

Is this some serious error? Reinstallation or what?

I am running ubuntu 9.10 on asus k50ij (kernel: 2.6.31.20)

Thanks    .   ,.

---

### Post by oldos2er on 2010-03-28
You should be using **gksu nautilus**. If it's not working, can you please post the terminal output?

---

### Post by vickoxy on 2010-03-28
> **oldos2er said:**
> You should be using **gksu nautilus**. If it's not working, can you please post the terminal output?

Thanks-see update in my first post. But, i always use sudo and never had any problems. Well, i was trying whole day to install ms office 2007 with wine, i did it, but in the meantime i noticed that i can not use this command any more```
asus@asus ~ $ sudo*nautilus
sudo*nautilus: command not found
```

---

### Post by Ahadiel on 2010-03-28
> **vickoxy said:**
> Thanks-see update in my first post. But, i always use sudo and never had any problems. Well, i was trying whole day to install ms office 2007 with wine, i did it, but in the meantime i noticed that i can not use this command any more```
asus@asus ~ $ sudo*nautilus
sudo*nautilus: command not found
```

That should be:
```
sudo nautilus
```

---

### Post by vickoxy on 2010-03-28
> **Ahadiel said:**
> That should be:
```
sudo nautilus
```

Well thanks. This is odd. I just navigate with arrow keys through most used commands in terminal, and in terminal it stays **sudo nautilus**, but as i copy the text here it is **sudo*nautilus**.

And i noticed that occasionally my space key on forums (and now in terminal) writes * instead of empty space.

So i manually retyped **sudo nautilus** and everything is working (before that i logged out).

So, it seems i have keyboard problems not sudo.

Thanks

---

### Post by oldos2er on 2010-03-28
Here's why you should use gksu with graphical apps: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by vickoxy on 2010-03-29
> **oldos2er said:**
> Here's why you should use gksu with graphical apps: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

Thanks-it makes a sense.

---

