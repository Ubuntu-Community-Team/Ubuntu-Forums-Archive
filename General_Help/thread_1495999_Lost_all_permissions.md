---
title: "Lost all permissions"
date: 2010-05-28
forum: General Help
---

### Post by gylti on 2010-05-28
I bought a small notebook which had Ubuntu preinstalled. My main computer also has the same op sys. At some time in a state of brainlessness I think I tried to stop unauthorised access and lost my internet connection ability.
If I right click on the log in switcher and select Edit users and groups, then select my username and go to properties then preferences, there are a lot of things shaded out and I can't access them, these include connecting to the internet.

I have logged in as sudo root but then I don't know what to do to access the user-properties-user privileges
can anyone help me with this?
The notebook was working fine before I messed around and even though I'v had it about 6 months I'v not been able to use it since which is a real shame

Also I added myself to root with adduser root in terminal but after restarting comp im not allowed to access user privileges or even make a new user

---

### Post by lmarmisa on 2010-05-28
Try to create a new user with Administrator privileges (System -> Administration -> Users and Groups).

Login in this new user account and check if you have privileges for internet access in this new account.

Best regards,

Luis

---

### Post by gylti on 2010-05-28
unfortunately I can't as I don't have permission to make a new user
The Add User is shaded out same as the permissions I can't change

---

### Post by Darkness Des on 2010-05-28
Try to find the program name, and then gksudo it from the terminal. Sudo uses your own user password instead of the root user's (long story) and you should basically have all permissions ever used.

---

### Post by lmarmisa on 2010-05-28
> **gylti said:**
> unfortunately I can't as I don't have permission to make a new user
The Add User is shaded out same as the permissions I can't change

Do you see a **Click to make changes** icon?

Click on this icon, give your password and you will be able to create a new account.

---

### Post by gylti on 2010-05-28
It's the one Imarmisa said to use: Aministration - Users and Groups, but I was accessing it by right clicking the Log out on the menu bar.
Im thinking that as there's nothing on the notebook I may as well reinstall Ubuntu so I might buy an external cd drive lol 

I don't know how to gksudo users and groups in terminal
I can sudo into a root user but I don't really understand the language terminal is needing to do things, I put in gksudo users after getting into the root but it is just giving me root@username

---

### Post by gylti on 2010-05-28
the key is shaded out I tried that, nothing happens

---

### Post by lmarmisa on 2010-05-28
Open a terminal a type this command:

> 
sudo users-admin


You will have the correct privileges then.

---

### Post by gylti on 2010-05-28
(users-admin : 4233) : CRITICAL ** Unable to look up session information for process '4233'

also it opened the users window but everything still shaded out

---

### Post by gylti on 2010-05-28
wow i tried it again and i got ** (users-admin:4249): CRITICAL ** :Unable to look up session information for process '4249'

---

### Post by gylti on 2010-05-28
and again and this time the number was 4265

---

### Post by gylti on 2010-05-28
its ok thank you for trying I will just get a cd drive and reinstall ubuntu

---

### Post by lmarmisa on 2010-05-28
Your system seems too rebel for me. Maybe you will need to reinstall Ubuntu.

Best regards,

Luis

---

### Post by gylti on 2010-05-28
:) thank you I will renew the op sys

---

