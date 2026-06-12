---
title: "Help with .bash_profile"
date: 2010-03-24
forum: General Help
---

### Post by megamark on 2010-03-24
I'm currently going through a tutorial for the bash shell, and need some help.
I need to edit my .bash_profile and I can't find it. I cannot access it in the terminal by typing in .bash_profile. I read it was in the home folder. when I type pwd I get 

/home/mark

I'm confused...

---

### Post by darolu on 2010-03-24
The .bash_profile is not created by default in Ubuntu, you have to create it yourself; in a terminal run:
```
~$ touch .bash_profile
```
Or you can create a buffer in your favourite text editor and the file will be created when you save it.

---

### Post by jobix on 2010-03-25
> **megamark said:**
> I'm currently going through a tutorial for the bash shell, and need some help.
I need to edit my .bash_profile and I can't find it. I cannot access it in the terminal by typing in .bash_profile. I read it was in the home folder. when I type pwd I get 

/home/mark

I'm confused...

If ".bash_profile" is exactly what you typed, you won't see it. It will complain that command not found. If you want to see it, you need to list it. You do this by:

```
ls -l ~/.bash_profile
```

or

```
ls -l /home/mark/.bash_profile
```

If it's there, you edit it using vi,emacs, gedit, or whatever you like.

The "pwd" command only shows you the present working directory. It won't show you all the files unless you use ls. Also, by default the "." files like .bash_profile are hidden. So you need to use "ls -la" to list them all.

---

### Post by megamark on 2010-03-25
I believe that it had not been created yet. Thanks darolu and jobix. I would touch both of your bash profiles if it wasn't so awkward. ____[]("http://ubuntuforums.org/member.php?u=436585")

---

### Post by anarkhos on 2010-03-25
> **megamark said:**
> i believe that it had not been created yet. Thanks darolu and jobix. I would touch both of your bash profiles if it wasn't so awkward. ____[]("http://ubuntuforums.org/member.php?u=436585")

lol

---

