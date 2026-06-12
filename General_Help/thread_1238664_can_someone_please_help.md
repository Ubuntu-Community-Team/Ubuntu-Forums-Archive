---
title: "can someone please help"
date: 2009-08-12
forum: General Help
---

### Post by libri1234 on 2009-08-12
hello my name i Pål Sivertsen, im not really good at english but ill try my best
 
i downloaded ubuntu yesterday i set it up tok away windows vista.
so when i was setting it up i saw that inn the end it stod that my keyboard
was italy so i just let i go i thot i could config it to norwegian. so now my
 
username: pél
 
i thot that was a little strang but ok come on it didnt matter much to me.
so when woke up this morning and turned on my computer i found out that i
could change language to norwegian on the screen where i log inn which i 
wanned to be so i did that yes it came to norwegian and then my username was
 
username: pål
 
and then i saw that i cannot log inn because its not the same and i cannot change 
the language back to the last...so the only thing i can do now is turn on my computer and
turn it off.. or simply just write an incorrect password/username ..ive tried everything
 
i hope you understand what i mean... im tottaly out of options..

---

### Post by alastair on 2009-08-12
Sorry - not sure. Maybe try :

1) Boot to loginj screen
2) Switch to a virtual (text) console : CTRL+ALT+F1 (or F2 etc.)
3) Login?

If you can login - try :

4) Type :

sudo dpkg-reconfigure xserver-xorg

Hopefully you can reset the language/locale?

---

### Post by scaramanzia on 2009-08-12
I don't know if I got you right. But let's see (my english is worst than yours, believe me)
Did you tried to log in from console?
If you can do it, you may then:
```
#sudo su
passwd
// you set a new password, without special characters

```
then log off, and log in into Gnome as root. Change your language, and log out again. Then, you may try to log in into Gnome with your correct name

---

### Post by libri1234 on 2009-08-12
i dont get to log inn since the username is incorrect
 
really thanks to those who tries to help me..anymore sugestment??

---

### Post by pizza-is-good on 2009-08-12
You could try to do a new install of Ubuntu. You'll loose all your settings and files saved on your Ubuntu partition, but that's all.

---

### Post by libri1234 on 2009-08-12
ok thanks so much ill do that..

---

### Post by pizza-is-good on 2009-08-12
No problem.
 
I can also help in Spanish if you're better at that. I know enough of it to get by.
 
Good luck.

---

### Post by libri1234 on 2009-08-12
sorry i dont think you need to do that im from norway....:)

---

### Post by pizza-is-good on 2009-08-12
Ok :d

---

### Post by libri1234 on 2009-08-12
ive made a new cd ubuntu 8.0... and the thing is dont i have to log in and then reboot?? to start it??

---

### Post by libri1234 on 2009-08-12
cause thats the thing i dont get to log inn because of incorrect username

---

### Post by Iowan on 2009-08-12
Not exactly the same problem, but [this]("http://www.psychocats.net/ubuntu/resetpassword") *might* help.

---

### Post by pizza-is-good on 2009-08-12
No. You would just boot from the CD, and then install Ubuntu over the old Ubuntu.
 
I would recommend you use 9.04, as it is the latest and most up to date version of Ubuntu.

---

### Post by libri1234 on 2009-08-12
ty no i got finaly thanks for all the help..

---

