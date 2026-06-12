---
title: "irssi sas question"
date: 2011-06-10
forum: General Help
---

### Post by pythonsyntax on 2011-06-10
What does this error mean i try to save it and get  this?

Irssi: Error saving theme to /home/perlsyntax/.irssi/default.theme: 
          Permission denied

---

### Post by andrew.46 on 2011-06-10
It would be interesting to see the results of the following:

```
ls -l /home/perlsyntax/.irssi/default.theme
```

Perhaps your permissions are set incorrectly?

---

### Post by pythonsyntax on 2011-06-10
how do i change themand when i try that command i get no file found.

---

### Post by andrew.46 on 2011-06-11
> **pythonsyntax said:**
> how do i change themand when i try that command i get no file found.

Hmmm.... sounds like something is wrong with permissions in your ~/.irssi folder. I have just setup irssi on Natty and the theme file was created with no problem. Permissions are:
```

andrew@Corinth:~$ **[COLOR="Red"]ls -ld /home/andrew/.irssi/[/COLOR]**
drwx------ 3 andrew andrew 4096 2011-06-11 16:39 /home/andrew/.irssi/
andrew@Corinth:~$ **[COLOR="Red"]cd /home/andrew/.irssi && ls -l[/COLOR]**
total 28
-rw-r----- 1 andrew andrew 7302 2011-06-11 16:45 config
-rw-r----- 1 andrew andrew 8472 2011-06-11 16:40 default.theme
-rw-r--r-- 1 andrew andrew   39 2011-06-11 16:39 sasl.auth
drwxr-xr-x 3 andrew andrew 4096 2011-06-11 16:41 scripts
```

Can you have a look at your permissions and see if they are similar to mine? Perhaps also consider removing irssi and your configuration files and starting afresh, following this guide:

[Howto] Setup irssi and join #ubuntu on Freenode
[http://ubuntuforums.org/showthread.php?t=1010780](http://ubuntuforums.org/showthread.php?t=1010780)

which might get things going for you hopefully :).

---

