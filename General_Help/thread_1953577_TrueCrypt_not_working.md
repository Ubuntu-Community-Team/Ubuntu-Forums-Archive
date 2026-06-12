---
title: "TrueCrypt not working"
date: 2012-04-06
forum: General Help
---

### Post by Shadow21 on 2012-04-06
I'm trying to get TrueCrypt running on my Kubuntu machine but it won't open after I install it. I'm using the install script that you get off of truecrypt.org.

I checked "/usr/bin" and both "truecrypt" and "truecrypt-uninstall.sh" were there but when I run "truecrypt" in a terminal it says that there is "No such file or directory" and if I try to run it from the menu nothing happens although it does sometimes give the error "KDEInit could not launch "/usr/bin/truecrypt".. "truecrypt-uninstall.sh" does work and removes all the files.

I ran the install script on my Xubuntu machine and the program opened fine after I installed it.

Does anyone know it's not working on my Kubuntu machine?

---

### Post by azmyth on 2012-04-06
Typing the command truecrypt should work unless /usr/bin isn't in your path. You could try in a terminal by typing /usr/bin/truecrypt to see what type of out put you're seeing. May also want to try re-running the install script to see if generated an error you missed.

---

