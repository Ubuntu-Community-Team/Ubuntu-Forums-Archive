---
title: "Need help!!"
date: 2009-09-15
forum: General Help
---

### Post by Hamadp on 2009-09-15
hey guys, this is my fisrt post, and my first time using Ubuntu, i am a complete noob to linux, when ever i try to install something on ubuntu it doesn't seem to work, i have attached a screenshot of my problem, (p.s im not up to scratch with the terminology and programs)

I have installed linux on a partiton on my 1yr old laptop because vista messed up for me, here is my spec if that may help:

250GB HDD
3gb ram DDR3 1791MB Nvidia 9600m gs 
intel core 2 duo processor t6400 
(gaming laptop by the way)

if you need anymore info please ask

thanks in advance

---

### Post by tad1073 on 2009-09-15
did you follow the instructions the error message gave you?

If not, open a terminal and run the command:
```
sudo dpkg --configure -a
```

---

### Post by wojox on 2009-09-15
In a terminal ( Applications > Accessories > Terminal )

```
sudo dpkg --configure -a
```

---

### Post by rocket16 on 2009-09-15
Run the command as wojox and tad1073 have told you. Then will work. I think your Machine has got some partly broken packages there.

---

### Post by Hamadp on 2009-09-15
thanks guys i love you for thisman im gratful to youguys but now i have another problem >(

I have no soundd!!

---

### Post by wojox on 2009-09-15
Okay open your terminal back up and run:

```
alsamixer
```

Make sure all the PC Speakers are tured up as well as PCM.

---

### Post by Hamadp on 2009-09-15
> **wojox said:**
> Okay open your terminal back up and run:

```
alsamixer
```Make sure all the PC Speakers are tured up as well as PCM.


Dude its not working :(

---

