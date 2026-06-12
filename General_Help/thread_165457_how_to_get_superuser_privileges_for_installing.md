---
title: "how to get superuser privileges for installing"
date: 2006-04-24
forum: General Help
---

### Post by 1002285 on 2006-04-24
I am trying to install some debian packages, but terminal says after my dpkg -i command that I need superuser privileges. What is this - the same as root user? But the command run as different user and writing "terminal" where the name of the program to be run as a different user has to be written gives an answer 
"Failed to run terminal as user root:
 Child terminated with 1 status"
What is this, and how to get the privileges I need for installing?

---

### Post by johso on 2006-04-24
[QUOTE=1002285]I am trying to install some debian packages, but terminal says after my dpkg -i command that I need superuser privileges. What is this - the same as root user? But the command run as different user and writing "terminal" where the name of the program to be run as a different user has to be written gives an answer 
"Failed to run terminal as user root:
 Child terminated with 1 status"
What is this, and how to get the privileges I need for installing?[/QUOTE]

Just use sudo - 'super user do' - and then your command, i.e. 'sudo dpkg -i <program>'.
Otherwise, if you find it easier or something, you can type 'sudo -s' to log in as root permanently.
Oh, and the password is the same you use to login, in case you're in doubt! :-)

---

### Post by aysiu on 2006-04-24
Open a regular terminal and type ```
sudo dpkg -i *.deb
```

---

### Post by 1002285 on 2006-04-24
thank you,
I did not know that. The packages got installed. Now I will just have a 100 new problems, like
- what are the similar commands for sh and bin-s
And I will have to find again the thread where they told how these deb-s I just installed should have helped me to get Estonian keyboard working.
Thanks.

---

### Post by johso on 2006-04-24
[QUOTE=1002285]thank you,
I did not know that. The packages got installed. Now I will just have a 100 new problems, like
- what are the similar commands for sh and bin-s
And I will have to find again the thread where they told how these deb-s I just installed should have helped me to get Estonian keyboard working.
Thanks.[/QUOTE]

You're welcome. ;-)
If you just installed a layout, I think (unless it's something not really standard) you'll find it in:
System->Preferences->Keyboard, go to the 'Layouts' tab, find the Add button - se if Estonian doesn't show up in the list to the left.

---

