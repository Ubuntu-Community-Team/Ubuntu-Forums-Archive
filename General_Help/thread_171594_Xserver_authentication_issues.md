---
title: "Xserver authentication issues"
date: 2006-05-07
forum: General Help
---

### Post by rupy on 2006-05-07
Everytime I boot I have to run "xhost local:" to add my machine to be allowed to interact with the X server:
"non-network local connections being added to access control list"

After that its fine...

Any ideas?

---

### Post by rupy on 2006-05-08
*Bump*

---

### Post by uteck on 2006-05-09
You could add that to your .Xsession

---

### Post by rupy on 2006-05-10
I dont have such a file? I assume I just need to create ~/.Xsession

And then add "xhost local:"

---

### Post by rupy on 2006-05-10
Well I did as above, and restarted, but no luck:
ru@mythicness:~$ su
Password:
root@mythicness:/home/ru# mythfrontend
Xlib: connection to ":0.1" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
mythfrontend: cannot connect to X server :0.1****

As soon as I run "xhost local:" as non root user I can launch anything as root...

---

### Post by rupy on 2006-05-10
Welll I did as above? Is that correct? It doesnt seem to have worked:
ru@mythicness:~$ su
Password:
root@mythicness:/home/ru# mythfrontend
Xlib: connection to ":0.1" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key
mythfrontend: cannot connect to X server :0.1

I still have to "su ru" "xhost local:" before I can then get anything on root....

---

### Post by rupy on 2006-05-12
No one else has any ideas? I have tried adding stuff to my bootmisc.sh file and editing the .Xauth.. and .Xsession files, but nothing...

---

### Post by cyracks on 2006-05-13
For gdm(gnome)
```

gdmsetup

```

By default because security reasons you can't login into X with root account

---

### Post by rupy on 2006-05-14
im using kdm :(

I found a work around however though - I just copied all config files over and am now running using non root user.

Quite annoying though :(

---

