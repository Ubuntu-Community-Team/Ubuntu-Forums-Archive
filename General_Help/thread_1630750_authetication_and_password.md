---
title: "authetication and password"
date: 2010-11-25
forum: General Help
---

### Post by mannyanthony on 2010-11-25
It seems that every time I try to dowwnload any apps kept on asking me for authetication and a password and later denied me the download. Where is the password  it kept asking and should get the authecation automatic (Why to)? I'm new at this so pardon for my ignorance. Looking forward to use your os . Manny.

---

### Post by Hippytaff on 2010-11-25
It will ask for passwords whenever you try to do anything that requires root (admin) priveledges...it's an excellent security feature, a bit annoying at first until you realise how important it is :-)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
:-)

---

### Post by ianc1 on 2010-11-25
I agree with hippytaff it'll be the root password and if you go eh what?!? its most likely your login password.  It is indeed a good security measure meaning that to install anything requires your approval first unlike a standard Windows installation.

---

### Post by mannyanthony on 2010-11-25
> **Hippytaff said:**
> It will ask for passwords whenever you try to do anything that requires root (admin) priveledges...it's an excellent security feature, a bit annoying at first until you realise how important it is :-)

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
:-)
    Thanks for your fast answer. I read the info .  but Is the password the one create during installation ? If not ; When asked for a password What I do? Is kind of complicate to me and I do not whant to screw this up.         i believed go the terminal  write sudo and write a password? Please help but  in dummy help mode. IIs there a way for me to check where or whiich it is?  The only password I know is the log in  and the installation one that is the same. Thanks . Manny.:D

---

### Post by Hippytaff on 2010-11-25
It is the one created during install (probably) try it :-)

open a terminal (CTRL+ALT+T) and type
```

sudo apt-get update

```
then when it asks for your password try the one you used at install (it will be the same)

:-)

---

### Post by mannyanthony on 2010-11-25
Thanks . I did it and worked with my installation password. It shows lots of entries. THanks again. Manny.

---

### Post by Hippytaff on 2010-11-25
no problem :-)

If you can mark this thread as solved in the thread tools at the top of the page others with the same question will benefit from how you solved it :-)

---

