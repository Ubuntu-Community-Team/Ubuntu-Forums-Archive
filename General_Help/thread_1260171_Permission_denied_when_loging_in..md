---
title: "Permission denied when loging in."
date: 2009-09-07
forum: General Help
---

### Post by CCarlson08 on 2009-09-07
I was fooling around with some of the permission settings and had it on my home folder that only you could access it and set it as an executive file. The next time I tried to login it wouldn't let me because permission was denied. Any ideas on how to fix this?

---

### Post by Iowan on 2009-09-07
[This]("http://www.psychocats.net/ubuntu/resetpassword") may not solve a permissions problem, but it's a place to start.

---

### Post by CCarlson08 on 2009-09-07
> **Iowan said:**
> [This]("http://www.psychocats.net/ubuntu/resetpassword") may not solve a permissions problem, but it's a place to start.
 
 
I have already reset the password, i am still able to access the other accounts on the system, just not mine.

---

### Post by Admiral Yi on 2009-09-07
Have you tried logging in a root (of a another user and using Su on a terminal) and changing the permissions back?

---

### Post by P4man on 2009-09-07
indeed, boot into recovery mode, open a root shell, and set your permissions right. Have a look here:
[http://ubuntuforums.org/showthread.php?p=6138880#post6138880](http://ubuntuforums.org/showthread.php?p=6138880#post6138880)

---

### Post by CCarlson08 on 2009-09-07
> **Admiral Yi said:**
> Have you tried logging in a root (of a another user and using Su on a terminal) and changing the permissions back?
 
Yes I have, it still says permission denied you are not the owner of this account. Even in root.

---

### Post by CCarlson08 on 2009-09-07
> **P4man said:**
> indeed, boot into recovery mode, open a root shell, and set your permissions right. Have a look here:
[http://ubuntuforums.org/showthread.php?p=6138880#post6138880](http://ubuntuforums.org/showthread.php?p=6138880#post6138880)
  here's the error msgs that happened when i did this. 
 
sudo: unable to resolve host vaio
sudo chown: command not found
chmod: changing permission of /home/username/  : Operation not permited
 
Any other tips?

---

### Post by P4man on 2009-09-07
> **CCarlson08 said:**
> here's the error msgs that happened when i did this. 
 
sudo: unable to resolve host vaio
sudo chown: command not found
chmod: changing permission of /home/username/  : Operation not permited
 
Any other tips?

are you doing that from a root shell in recovery mode?

---

### Post by CCarlson08 on 2009-09-07
> **P4man said:**
> are you doing that from a root shell in recovery mode?
 
I did it on the main screen in terminal from root. shoudnt that be the same?

---

### Post by CCarlson08 on 2009-09-07
> **CCarlson08 said:**
> I did it on the main screen in terminal from root. shoudnt that be the same?
 
apparently it did make the difference, thank you it is fixed now :)

---

