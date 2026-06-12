---
title: "Which shell: bash or korn"
date: 2011-01-14
forum: General Help
---

### Post by TorMike on 2011-01-14
Simple question.

Is there a 'native' shell for Ubuntu 10.10?

I usually work in KORN shell, but I've got a feeling that Ubuntu 'likes' BASH OR does it really matter which shell I use?

Thanks.

---

### Post by WorMzy on 2011-01-14
Bash is default, but you can install and use any shell you want. Just use the chsh command if you want to change your default shell.

---

### Post by WorMzy on 2011-01-14
Bash is default, but you can install and use any shell you want. Just use the chsh command if you want to change your default shell.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash (Debian Almquist shell) which is what you get if you try to run the plane Bourn shell (sh).  If you prefer to use ksh for interactive sessions you can install it with ```
sudo apt-get install ksh
```For any scripts that are going to be used across Linux systems I would suggest sticking to bash since that is fairly standard on Linux.

Sorry for the duplicate posts below, something about the submitting the reply hung and refreshing caused the multiple posts.  If the moderator can remove them I would apreciate it.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash (Debian Almquist shell) which is what you get if you try to run the plane Bourn shell (sh).  If you prefer to use ksh for interactive sessions you can install it with ```
sudo apt-get install ksh
```For any scripts that are going to be used across Linux systems I would suggest sticking to bash since that is fairly standard on Linux.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash  (Debian Almquist shell) which is what you get if you try to run the  plane Bourn shell (sh).  If you prefer to use ksh for interactive  sessions you can install it with ```
sudo apt-get install  ksh
```For any scripts that are going to be used across Linux systems  I would suggest sticking to bash since that is fairly standard on  Linux.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash  (Debian Almquist shell) which is what you get if you try to run the  plane Bourn shell (sh).  If you prefer to use ksh for interactive  sessions you can install it with ```
sudo apt-get install  ksh
```For any scripts that are going to be used across Linux systems  I would suggest sticking to bash since that is fairly standard on  Linux.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash   (Debian Almquist shell) which is what you get if you try to run the   plane Bourn shell (sh).  If you prefer to use ksh for interactive   sessions you can install it with ```
sudo apt-get install   ksh
```For any scripts that are going to be used across Linux  systems  I would suggest sticking to bash since that is fairly standard  on  Linux.

---

### Post by hawkmage on 2011-01-14
By default users are assigned the bash shell.  Also there is the dash   (Debian Almquist shell) which is what you get if you try to run the   plane Bourn shell (sh).  If you prefer to use ksh for interactive   sessions you can install it with ```
sudo apt-get install   ksh
```For any scripts that are going to be used across Linux  systems  I would suggest sticking to bash since that is fairly standard  on  Linux.

---

### Post by TorMike on 2011-01-14
Thanks!  Nasty business with the repeats.

I think I'll stick to korn shell, I've got a lot of canned scripts I use and, although not a huge job, I really don't want to rewrite any.

---

### Post by afrodeity on 2012-01-03
There is also zsh, which some users swear by. I haven't found much use for it. What are the benefits of ksh over bash and sh?

---

### Post by nothingspecial on 2012-01-03
[IMG]http://img845.imageshack.us/img845/6976/necro2.png[/IMG]

---

