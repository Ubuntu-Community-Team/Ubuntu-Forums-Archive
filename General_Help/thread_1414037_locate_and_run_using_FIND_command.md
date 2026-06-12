---
title: "locate and run using FIND command?"
date: 2010-02-23
forum: General Help
---

### Post by arayici22 on 2010-02-23
Easy quastions for expert!
 
I was trying to find and run the program from command line like calculater
but i was unable to do these two thing togethet.
i can find the path seperetly or i can find and run the program without seeing the path
 
I want to find and see the path and run it at the same time?
 
So what command shoul I use?:confused:

---

### Post by ajgreeny on 2010-02-23
Probably easiest to run ```
locate -i calculator
``` (note spelling) or even ```
locate -i calculat
``` (just part of the name, but spelled correctly) and then just highlight the /usr/bin/gnome-calculator from the list and then middle click at the command prompt in terminal to run it.

---

### Post by arayici22 on 2010-02-23
actually I want to do this from command line and with FIND command like
 
 
find ./ -type f -exec grep -l 'gnome-calculator' {} \;    (this is not workin for me)
 
I can find the path with
 
find ./ -name 'gnome-calculator'
 
and I can find and run it with
 
find ./ -exec 'gnome-calculator' {} \;
 
but I was trying to make these last two command as one.
 
meaning by that ; I want to see the path and run the program!

---

### Post by Darkish Dave on 2010-02-23
I am not sure but, you can fuse two command using "|" between them.

I am sure if this will work

```
find ./ -name 'gnome-calculator' | find ./ -exec 'gnome-calculator' {} \;
```

---

### Post by pi/roman on 2010-02-23
```
sudo find / -name 'gnome-calculator' -print -exec {} \;
```

---

### Post by arayici22 on 2010-02-23
> **Darkish Dave said:**
> I am not sure but, you can fuse two command using "|" between them.
 
I am sure if this will work
 
```
find ./ -name 'gnome-calculator' | find ./ -exec 'gnome-calculator' {} \;
```
 
 
Piping to commands as yours only runing the calculator but still not displaying the path!

---

### Post by arayici22 on 2010-02-23
> **pi/roman said:**
> ```
sudo find / -name 'gnome-calculator' -print -exec {} \;
```
 
 
Yes this did the trick like how i wanted:D
 
Thanks pi/roman
 
[COLOR=blue]find / -name 'gnome-calculator' -print -exec {} \; [/COLOR]

---

