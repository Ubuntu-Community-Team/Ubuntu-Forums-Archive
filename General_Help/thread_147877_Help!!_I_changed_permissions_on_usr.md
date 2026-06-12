---
title: "Help!! I changed permissions on /usr"
date: 2006-03-21
forum: General Help
---

### Post by Bubs on 2006-03-21
:oops: so I changed the permissions on my /usr to 777 so that I could add a folder for another program.  then when changing it back I stupidly changed it to 644!!!  is there ANY way to get it back to normal.  please help!!!!

---

### Post by Sutekh on 2006-03-21
You need to make it 755

```
sudo chmod -R 755 /usr
```

If you needed to add a folder to /usr you should have used sudo not change the permissions
```
sudo mkdir /usr/blahfg
```

---

### Post by Bubs on 2006-03-21
sorry I'm a complete n00b at this

I had know idea how ot make a new folder in a directory but that for the tip.

also it gives me an error 

bash: /usr/bin/sudo:  permission denied


the last thing that I want to here is "sorry your F**ked"  so please I need help

---

### Post by Sutekh on 2006-03-21
Okay lets go back to the beginning.  

What exactly have you done?  

How did you change the permissions of /usr?

---

### Post by Bubs on 2006-03-21
ok first in the terminal I typed ```
sudo chmod 777 /usr
```
then I added a folder into /usr
then being an idiot I tried to change the permissions back but changed them to 644 using ```
sudo chmod 644 /usr
```

---

### Post by Sutekh on 2006-03-21
Yo roger.  Okay you need to gain root access to Ubuntu (I'll list some methods) and then change the permissions back.  The 644 permissions on /usr don't allow execute access, which you need to use sudo obviously.

There are 3 ways I can suggest (from the old Ubuntu Starter Guide for Hoary).  They should still apply to Breezy.

[Ubuntu Guide - How to gain root user access without login?]("http://www.ubuntuguide.org/#gainrootwithoutlogin")

[Ubuntu Guide - How to use Ubuntu Installation CD, to gain root user access?]("http://www.ubuntuguide.org/#gainrootinstallcd")

[Ubuntu Guide - How to modify kernel boot-up arguments, to gain root user access?]("http://www.ubuntuguide.org/#gainrootmodifykernel")

The first link is easiest to accomplish.

Then chmod /usr back to 755

---

### Post by Bubs on 2006-03-21
THANK YOU!!!

that totally worked I appreciate the help

---

### Post by Sutekh on 2006-03-21
Excellent, glad to hear it!

---

