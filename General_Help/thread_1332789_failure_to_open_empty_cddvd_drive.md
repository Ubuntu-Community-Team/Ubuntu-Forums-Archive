---
title: "failure to open empty cd/dvd drive"
date: 2009-11-20
forum: General Help
---

### Post by cowboy7305 on 2009-11-20
When i try to open my dvd i press the button and it sounds like its trying to open but does not ,takes about 6/7 times to get it to open  /i am using a dell inspiron 530
about 2 years old

---

### Post by slumbergod on 2009-11-20
You could try ejecting the tray from the command line. 

On my system the DVD writer is identified as scd0 so I would type:
eject scd0

---

### Post by Shazaam on 2009-11-20
Or try this...
```
sudo eject
```
You may have to add the id-
```
sudo eject /dev/cdrom0
```
(that's a zero)
or-
```
sudo eject /dev/scd0
```

---

