---
title: "no write access to home directory"
date: 2011-06-27
forum: General Help
---

### Post by SchofieldCharles on 2011-06-27
kernal 2.6.38-8

After updating Kubuntu - the log in screen will not progess to the desktop. It freezes and then shows the message "no write access to the home directory.."

Googling the problem - references to an .ICEauthority in my home directory are mentioned as linked to this problem. However "ls -la /home/charles" reveals that there is no .ICEauthority file present.

Have also tried all the chown instruction permutations from other searches.

Please help, I am a newbie who is determined to crack this problem.

---

### Post by bodhi.zazen on 2011-06-27
Boot to recovery mode and list the ownership and permissions of your home directory

```
ls -LA /home
```Change ownership and permissions of your home directory back to either 750 or 755

---

### Post by ajgreeny on 2011-06-27
> **bodhi.zazen said:**
> Boot to recovery mode and list the ownership and permissions of your home directory

```
ls -LA /home
```Change ownership and permissions of your home directory back to either 770 or 777
Isn't /home usually given 755 permissions, rather than 777 (dangerous, surely?) or 770?

Perhaps I'm just a bit out of touch with things these days, but I am pretty sure I had to use 755 a long time ago when I had permission problems after changing distros.

---

### Post by bodhi.zazen on 2011-06-27
> **ajgreeny said:**
> Isn't /home usually given 755 permissions, rather than 777 (dangerous, surely?) or 770?

Perhaps I'm just a bit out of touch with things these days, but I am pretty sure I had to use 755 a long time ago when I had permission problems after changing distros.

You are correct, permissions should be 750 or 755

---

### Post by SchofieldCharles on 2011-06-29
Many thanks for your contributions I have tried as you suggest, but the charles folder remains stubbornly as:

drwxr-xr-x 32 1003 USERS 2010 10 05 23:36 charles.

I have a working Ubuntu on another PC and that folder lists as

drwxr-xr-x 40 charles charles 4096 2011 06 29 20:36 charles

(just noticed the date on the problem system has also not updated).

Any suggestions?

---

### Post by bodhi.zazen on 2011-06-29
boot to recovery mode and

```
chown -R charles.charles /home/charles
```

How did this change happen ?

---

### Post by SchofieldCharles on 2011-06-29
SOLVED

Many thanks for your help. 

chown -R charles.charles /home/charlesThis solved my problem.

Also noticed that the .. directory in /home was

drwxr -xr -x 22 1003 USERS 4096 2011 -10 05 23:36 ..

changed this via/to:

chown -R root.root /home/..
Hope this is OK - everything seems fine with my system.


Thanks again for all your help.

No idea how this happened in the first place I will go more carefully now.

---

