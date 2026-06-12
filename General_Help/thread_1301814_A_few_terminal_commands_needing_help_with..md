---
title: "A few terminal commands needing help with."
date: 2009-10-26
forum: General Help
---

### Post by RCantw3ll on 2009-10-26
Hello all,

Sry that this is a repost, but I feel as though I may have put the question in the wrong section earlier so I am moving it over here. Sry again and thanks again for the help.

I am in need of some help that I feel most could answer with relative ease. Here are my questions: (Note that I am in ubuntu 8.10)

How to enable a newly created user to use the sudo command through the terminal.

What command to run in terminal to find out what servers are running on my local system?

and what command will list all of the open files on my system? (some sort of specific -ls command maybe?)

I normally am able to find answers to my questions with a quick google search or with playing with the system, but that just has not been the case today. Thanks to everyone in advance.

Best,

RCantw3ll

---

### Post by OpenGuard on 2009-10-26
To add a new user to sudoers file, open it's configuration file:
```
nano /etc/sudoers

```Add:
```
[COLOR=Gray]root ALL=(ALL) ALL[/COLOR]
newuser ALL=(ALL) ALL
```

---

### Post by undecim on 2009-10-26
for running services:```
service --status-all
```

for listing open files, look at lsof

---

### Post by sisco311 on 2009-10-26
> **RCantw3ll said:**
> 
How to enable a newly created user to use the sudo command through the terminal.


add the user to the admin group:
```
sudo adduser username admin
```


> **OpenGuard said:**
> To add a new user to sudoers file, open it's configuration file:
```


```Add:
```
[COLOR=Gray]root ALL=(ALL) ALL[/COLOR]
newuser ALL=(ALL) ALL
```

You should always edit the file with visudo:
```
sudo visudo
```

BTW, the admin group is already in the sudoers file.
```
%admin ALL=(ALL) ALL
``` 

[uhelp]community/Sudoers[/uhelp]

---

### Post by RCantw3ll on 2009-10-26
Thanks to everyone for the help. All of my questions were answered and worked well.

Best,

RCantw3ll

---

### Post by SuperSonic4 on 2009-10-26
> **sisco311 said:**
> add the user to the admin group:
```
sudo adduser username admin
```




You should always edit the file with visudo:
```
sudo visudo
```

BTW, the admin group is already in the sudoers file.
```
%admin ALL=(ALL) ALL
``` 

[uhelp]community/Sudoers[/uhelp]

You can also use environment variables to edit sudoers in nano ```
sudo EDITOR=nano visudo
```

---

### Post by sisco311 on 2009-10-26
> **SuperSonic4 said:**
> You can also use environment variables to edit sudoers in nano ```
sudo EDITOR=nano visudo
```

nano is the default editor in most releases.

but, yes you can use VISUAL/EDITOR to edit it in your GUI/CLI text editor of choice:
```
sudo env VISUAL=gedit visudo
```

---

### Post by OpenGuard on 2009-10-26
> **sisco311 said:**
> nano is the default editor in most releases.

but, yes you can use VISUAL/EDITOR to edit it in your GUI/CLI text editor of choice:
```
sudo env VISUAL=gedit visudo
```

gedit != terminal

---

### Post by sisco311 on 2009-10-26
> **OpenGuard said:**
> gedit != terminal

It's safe to use a GUI editor for editing the file, until you run the command from a terminal.

If a syntax error is detected, the "What now?" dialog will show up in the terminal window.

---

