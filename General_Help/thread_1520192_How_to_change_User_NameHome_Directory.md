---
title: "How to change User Name/Home Directory?"
date: 2010-06-29
forum: General Help
---

### Post by vickoxy on 2010-06-29
So, i just plugged in my new thinkpad r500 the harddisk from r400. My username was **r400**. Can i change it in r500. Some easy way?

I tried to change in users and groups, but nothing.

I tried to follow this instructions, but nothing:
[http://ubuntuforums.org/showthread.php?t=821685&page=4](http://ubuntuforums.org/showthread.php?t=821685&page=4)

 Am i missing something?

Thanks

---

### Post by Leppie on 2010-06-29
did you do this from the recovery shell as suggested?
you will never be able to move your account, while you're logged on with the same account.

---

### Post by vickoxy on 2010-06-29
I tried but i just made half a job:
i want to rename my r400 to R500.
I used: ```
usermod -l R500 -m -d /home/R500 r400
```

And i got this in terminal:
```
R500@r400:~$ 
```

If i logout i have on login screen up (little letters r400 and bellow as user name R500)

Home Directory is now R500.

Any idea?

Thanks

---

### Post by Vaphell on 2010-06-29
can't you simply create a new account, configure it to have proper rights and move stuff there?

---

### Post by Leppie on 2010-06-29
> **vickoxy said:**
> I tried but i just made half a job:
i want to rename my r400 to R500.
I used: ```
usermod -l R500 -m -d /home/R500 r400
```And i got this in terminal:
```
R500@r400:~$ 
```If i logout i have on login screen up (little letters r400 and bellow as user name R500)
the part before the "@" is the account name, the part after the "@" is the computer name.
so, r400 is the computer name...
you can change that easily like this (you can do this while logged on):
```
sudo hostname -v -b r500
```but this will not change anything for your account (which apparently already is r500).

or if you want, you can edit the hostname file directly:
```
gksudo gedit /etc/hostname
```

---

### Post by vickoxy on 2010-06-30
Thanks!!!:popcorn:

---

### Post by Leppie on 2010-06-30
you're welcome :)

---

