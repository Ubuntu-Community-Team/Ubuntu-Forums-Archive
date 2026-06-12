---
title: "Hi Whenever I do cat tux.txt it doesn't change the picture"
date: 2010-08-24
forum: General Help
---

### Post by Lukasz Tarkowski on 2010-08-24
Hi Whenever I do cat tux.txt it doesn't change the picture, I'm in the correct directory to, I have Asus G1S, asus oled and asus daemon the latest, from berlios.
The picture shows up and disapears but doesn't start on startup

[PHP]cat tux.txt > /sys/class/asus_oled/oled_1/picture[/PHP]

---

### Post by jpaugh64 on 2010-08-24
> **Lukasz Tarkowski said:**
> 
[PHP]cat tux.txt > /sys/class/asus_oled/oled_1/picture[/PHP]

So, is this really a PHP problem, or are you using a shell? 
If you are using a shell, you will not be able to redirect into there without root privileges.
Infact, not even
```
$ sudo cat > /path/filename 
``` will work, because the shell itself needs root privileges, not the cat program.

Try this:
```
$ sudo -i
# cat tux.txt > /sys/class/asus_oled/oled_1/picture
# exit
$ 
```

Incidentally, if you are using PHP, your php program will still need root privileges to mess with stuff under the /sys directory.

---

### Post by Lukasz Tarkowski on 2010-08-24
Copying the picture did not work, I still get their website, I did the command cat as well, i Was using the terminal.  

Dunno why it didn't work is this a bug with asus oled from berlios?

---

