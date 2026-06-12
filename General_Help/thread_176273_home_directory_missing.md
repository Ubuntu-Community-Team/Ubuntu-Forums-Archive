---
title: "/home directory missing???"
date: 2006-05-14
forum: General Help
---

### Post by adamgfry on 2006-05-14
well i installed ubuntu about 3 hours ago, just fixed a prob with the graphics card driver coz that was messed up. When i get onto the login screen, and login it comes up with /home directory is not there, would you like to login with the /root directory, so i click yes, and it still dosnt log in. I have tried failsafe mode taht dosnt work. I nedd ubuntu quick so plz can someone help me???

---

### Post by Gomek on 2006-05-14
Seems like you've got some serious hardware compatibility issues or something.  Try logging in from a terminal.

Type:
```
cd /
ls
```

Is **home** there?

---

### Post by Ramses de Norre on 2006-05-14
Can you log in through a shell?
Try to choose recovery mode in grub otherwise, that will give you a root prompt.
I'll look up the command to set the home folder if you can get into a shell.

---

### Post by adamgfry on 2006-05-14
[QUOTE=Gomek]Seems like you've got some serious hardware compatibility issues or something.  Try logging in from a terminal.

Type:
```
cd /
ls
```

Is **home** there?[/QUOTE]

this dosnt work, there is no such directory or file.



but i can get onto the root through the recovery system, so if u can tell me how to make a home folder, it will be much appreciated

---

### Post by Ramses de Norre on 2006-05-14
There is no /home folder?? This really isn't normal.. You can create it with ```
mkdir /home; mkdir /home/username
``` but I doubt your installation went ok..

---

### Post by adamgfry on 2006-05-14
[QUOTE=Ramses de Norre]There is no /home folder?? This really isn't normal.. You can create it with ```
mkdir /home; mkdir /home/username
``` but I doubt your installation went ok..[/QUOTE]

and now it works
 Thankx for all your help and support on this 1, it was really urgent

---

### Post by Ramses de Norre on 2006-05-14
Oh because you created it as root you might have to run ```
sudo chown -R username /home/username && chmod -R 755 /home/username
``` (or some other permission but at least 6 for yourself)

---

