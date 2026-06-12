---
title: "How do I give myself full access to my computer?"
date: 2010-02-03
forum: General Help
---

### Post by pr3c1pit0us on 2010-02-03
I'm sure, with me being new to Ubuntu (and linux in general), that I shouldn't be messing around with too many things. But I'm trying to delete a program that I downloaded myself and I keep running into an error -- I'm denied access. 

It's a little frustrating to say the least. So, can you guys help me out on that?

---

### Post by patchwork on 2010-02-03
if you installed it via apt-get:
```
sudo apt-get remove <program_name>
```if you downloaded the package from the internet, you can either use 

```
gksu nautilus
```, which will open the file manager with root permissions, allowing you to erase the files you want to erase, or

```
sudo rm -rf </path_to_file/file_name>
``` in the terminal.  This will run the remove command as root.

Word of caution....the gksu and sudo commands allow you to pretty much do anything, good or bad for your system.  Know exactly what you are trying to delete before doing so.  Again, if you installed from the repositories, use the apt-get remove (or apt-get purge) command.

---

### Post by ajgreeny on 2010-02-03
How exactly did you install it, and what type of package did you use, a .deb file, an executable binary, a .tar.gz archive?  Without knowing that it is impossible to know how to start helping you.

---

### Post by rnerwein on 2010-02-03
hi [patchwork]("http://ubuntuforums.org/member.php?u=982585")
why you give the rm command the option -rf. that's very dangerous even with sudo you are running with root account. don't play with the fire we say in germany
ciao

---

### Post by Iowan on 2010-02-03
It probably bears repeating: **sudo rm -rf** is very risky. 
**sudo rm -rf /** is one keystroke away from wiping your system faster than you can say "OOPS!".
[http://ubuntuforums.org/announcement.php?f=326]("http://ubuntuforums.org/announcement.php?f=326")

---

### Post by bodhi.zazen on 2010-02-03
In ubuntu, sudo rm -rf / does nothing, but it is a key stroke away from giving you a headache and potential data loss.

For admin access use sudo or gksu

[RootSudo - Community Ubuntu Documentation]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ajgreeny on 2010-02-03
To give just one more chance to save the day on any rm command, it is worth making an alias in ~/.bashrc or ~/.bash_aliases, depending on where you keep such things, by adding the line ```
alias rm='rm -i'
```Then when you rm any file/folder you will be asked one more time to confirm that is what you want to do.

It might just make you think again, and save you a lot of trouble.

---

### Post by bodhi.zazen on 2010-02-03
> **ajgreeny said:**
> To give just one more chance to save the day on any rm command, it is worth making an alias in ~/.bashrc or ~/.bash_aliases, depending on where you keep such things, by adding the line ```
alias rm='rm -i'
```Then when you rm any file/folder you will be asked one more time to confirm that is what you want to do.

It might just make you think again, and save you a lot of trouble.

Yep, I include cp and mv in that list.

---

### Post by pr3c1pit0us on 2010-02-04
Thanks, patchwork, for giving me the three commands.

It was actually just a folder that I wanted gone and I was trying to remove it from the GUI, but alas, your **sudo rm -rf** worked even if it was a bit risky.

Thanks.

---

