---
title: "Ext. hard name changed from My Passport to My Passport_"
date: 2009-07-26
forum: General Help
---

### Post by joconnorwi on 2009-07-26
Now I'm having conflicts with my audio programs, amarok, exaile, etc..with my library loading...
it wants to see the regular my passport not (my passport_)     

how can I get back to the regular My Passport....

---

### Post by SuperSonic4 on 2009-07-26
You could always rename it. Either in fstab if it's in on boot or by using mv

---

### Post by joconnorwi on 2009-07-26
mv? when I try to rename it it says I don't have permission..as you can see, everywhere else it says the nake is my passport, except in the title of the browse window....here's what kaffeine looks like...

---

### Post by cosine352 on 2009-07-26
look at the /media directory

> ls /media/

probably there is already a 'My Passport' directory. remove that directory. you may need to use sudo. 

> sudo rmdir /media/My Passport

Unmount and mount the hard drive again.

---

### Post by joconnorwi on 2009-07-26
> **cosine352 said:**
> look at the /media directory



probably there is already a 'My Passport' directory. remove that directory. you may need to use sudo. 



Unmount and mount the hard drive again.

ugh...this is killin' me...i certainly appreciate the help so far though..
here's what i see in the terminal..

---

### Post by SuperSonic4 on 2009-07-26
```
sudo rmdir /media/My\ Passport
```

You can also use tab completion (hit tab after /media/My)

---

### Post by joconnorwi on 2009-07-26
> **SuperSonic4 said:**
> ```
sudo rmdir /media/My\ Passport
```

You can also use tab completion (hit tab after /media/My)

[SIZE="7"]That worked!![/SIZE]

thank you so much!!! success!

---

### Post by cosine352 on 2009-07-26
good

---

