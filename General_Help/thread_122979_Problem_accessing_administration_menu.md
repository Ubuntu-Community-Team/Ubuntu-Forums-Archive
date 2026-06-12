---
title: "Problem accessing administration menu"
date: 2006-01-28
forum: General Help
---

### Post by g3r41d on 2006-01-28
Help... I cant seem to access some of the menu in under administration. Eg are
- networking
- user groups

initially it run and ask for the password. I tink is the root password. Then when i enter the password. It continues to run the process in the background. But it never opens the menu. Initially it shows opening networking in the panel. But it later just closes without opening the relevant window. What is the problem here.

Thanx

---

### Post by codejunkie on 2006-01-28
[QUOTE=g3r41d]Help... I cant seem to access some of the menu in under administration. Eg are
- networking
- user groups

initially it run and ask for the password. I tink is the root password. Then when i enter the password. It continues to run the process in the background. But it never opens the menu. Initially it shows opening networking in the panel. But it later just closes without opening the relevant window. What is the problem here.

Thanx[/QUOTE]
did you do an expert install or a normal install? and when it asks for the password enter the password of the first user you created when installing ubuntu.

---

### Post by g3r41d on 2006-01-29
Yep i did expert install. becos my cd does not allow me to do normal install..

I did input the password. But after that it still would not work. Could it be due to the fact that my root and normal user uses the same password..

---

### Post by codejunkie on 2006-01-29
[QUOTE=g3r41d]Yep i did expert install. becos my cd does not allow me to do normal install..

I did input the password. But after that it still would not work. Could it be due to the fact that my root and normal user uses the same password..[/QUOTE]
what causes it is the menu items in ubuntu use the command gksudo before the actual command for example: ```
gksudo /usr/bin/synaptic
``` opens the package manager as root. and when you do an expert install, the installer dosen't add your name to the sudoers file, and because it's required that your username be in the sudoers file before gksudo will work apps will still asks for the password but exit right after it's entered because you don't have gksudo privliges.
This will fix it open a terminal login as root with the su command then enter this command 
```
export EDITOR=gedit && visudo
```
then add your username to the bottom of the file like this
```
yourusername	ALL=(ALL) ALL
```save the file and close gedit and test the admin apps again when it asks for a password enter you user password hope this helps.

---

