---
title: "I can't log in after I installed LIGHTDM (11.04)"
date: 2011-06-13
forum: General Help
---

### Post by Aguilarn on 2011-06-13
Greetings. 

I read on a blog that the cross desktop display to be featured in Ubuntu 11.10 named LIGHTDM was available for tests and debug. I decided to try it, and sucessfuly installed it by entering the following command at the code terminal:

sudo apt-add-repository ppa:lightdm-team/ppa
sudo apt-get install lightdm lightdm-theme-gnome

It all had been alright until I rebooted. Nonetheless, just as I tried the new feature for the first time, I found a bug to report: it won't accept accented letters.

My password has the character "ó". I must press "Alt Gr" + "´" followed by "o" to enter this character. However the new login screen won't accept this command. As I type "alt gr" + "´" it promptly shows a character in the password field. Additionaly, I can't set the keyboard settings on the new screen the same way I could on GDM. I tried to change it from USA, to Brazil, Portugal and other languages, but nothing has worked so far. 

I also tried to input Window's Alt Key Codes, but it is just as uneffective.

Finally I tried to boot in the security mode by pressing spacebar, enter, ESC, F6 and whatever else during the boot process. No success.

Does anyone know what can I do? I really hope I won't need to format. 

(sorry about the bad English, btw)

Thanks!

---

### Post by garvinrick4 on 2011-06-13
ctrl/alt/F1 keys will put you in terminal:
login and password:
```
sudo dpkg-reconfigure lightdm
```
select gdm with arrow key hit enter and reboot.

---

### Post by garvinrick4 on 2011-06-13
Lightdm is in testing and will be unstable use if you want to bug test it.

I also find that going into a terminal and:
```
sudo stop lightdm
```
```
sudo start gdm
```
also works and vice versa:

---

### Post by Aguilarn on 2011-06-13
It worked, pal. Thanks! :D

I'm aware of LightDM is in testing and was indeed willing to test it.

---

