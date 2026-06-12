---
title: "sound at ubuntu 9.04"
date: 2009-08-03
forum: General Help
---

### Post by masoud23 on 2009-08-03
Hello

I have just installed ubuntu 9.04. have no sound, how do i start the sound?

---

### Post by Codix121 on 2009-08-03
Make Sure Your Sound is Turned up,
By going to the top right corner and selecting the sound options,
or hit 

ALT+F2 and type in 

```
GNOME-VOLUME-CONTROL
```

make sure and see if that works,
if not, open your terminal,

```

APPLICATONS > ACCESSORIES > TERMINAL

``` 

and copy and paste this:

```
cat /proc/asound/card0/codec#* | grep Codec
```

and paste the results on this forum,
that line should tell you what sound card you have.

---

### Post by masoud23 on 2009-08-03
Done all that, have still no sound. i have: C-Media CM9880

---

### Post by Codix121 on 2009-08-03
What's the model of your laptop or computer,
I'll try to see what I can find.

---

### Post by masoud23 on 2009-08-03
The mother bord is asus. I have run ubuntu 7.10 on this computer and the sound worked well then. i just upgrade to 9.04 today and can't start the sound!?

---

