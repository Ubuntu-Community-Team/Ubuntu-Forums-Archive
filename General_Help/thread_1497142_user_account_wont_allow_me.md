---
title: "user account wont allow me"
date: 2010-05-30
forum: General Help
---

### Post by sb4100 on 2010-05-30
hi
i have just recently installed ubuntu 10.04 on my server but, im now having problems, i created a new user on it, via ssh but now i need to some how change it to full rights.as i cant run commands when i type in sudo su (it comes up enter password i type in my password and it comes up is myusername not in the sudoers file.  This incident will be reported.)


but how do i do this. any ideas please

thanks if you can help me out



sorry if this is posted in the wrong forum.

---

### Post by Ryan Dwyer on 2010-05-30
You need to add the user to the admin group so it has sudo rights.

---

### Post by sisco311 on 2010-05-30
Add the user to the admin group:
```
sudo gpasswd -a username admin
```

Oh, and instead of **sudo su** use **sudo -i**, for details see [unutbu's post]("http://ubuntuforums.org/showpost.php?p=6188826&postcount=4").

---

### Post by sb4100 on 2010-05-30
hi just tried the command above and it says the same sb4100 is not in the sudoers file.  This incident will be reported.). sudo -i  aswell

thanks again any ideas

---

### Post by Monotoko on 2010-05-30
Use this:
```
visudo
``` (from your normal account)
then add the following line (replace username with your account username)
username ALL=(ALL) ALL

---

### Post by sisco311 on 2010-05-30
> **sb4100 said:**
> hi just tried the command above and it says the same sb4100 is not in the sudoers file.  This incident will be reported.). sudo -i  aswell

thanks again any ideas

You have to log in as the first user, the one with sudo rights (admin privileges).

---

### Post by sb4100 on 2010-05-30
thank you that worked i believe, ran it over ssh and it worked.  thanks alot m8, 
thanks as well all for that helped

thank you

---

