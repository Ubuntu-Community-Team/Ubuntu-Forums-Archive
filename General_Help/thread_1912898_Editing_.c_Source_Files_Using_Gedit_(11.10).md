---
title: "Editing .c Source Files Using Gedit (11.10)"
date: 2012-01-21
forum: General Help
---

### Post by WariusBirde on 2012-01-21
I searched the forums and didn't see anything concerning this so I've opted to make a thread; sorry if I missed an existing thread.

I'm working with C programming for an ECE class I'm in and due to the professor's agonizing pace, I've opted to start teaching myself a bit. Right now I can set up a straightforward "Hello world!" program using gedit and Gcc/cc for compiling, but I'm curious as to whether I can go in and edit the source code to muck about with the program. 

However, when trying to open the .c file with gedit post intial saving I am unable to save my changes (all of this done through the console), I am notified that it is a read only file.

Why is this? I'm under the impression that you should be able to go in and make changes for debugging reasons and that having to redo an entire file to make a single edit is a bit silly. I'm still very very new to the OS and programming so I'm sure I'm missing something.

Any help?


- 11.10 on a HP 1330a partition

---

### Post by dino99 on 2012-01-21
you need to run:

gksu gedit yourfile2edit

then with the gedit menu settings, you can choose color syntaxes and so on.

[https://help.ubuntu.com/community/gedit](https://help.ubuntu.com/community/gedit)

---

### Post by sudodus on 2012-01-21
Where is your file stored? What file system is it and what permissions? It seems that your file is read-only, which can be changed if you the details.

So please give the full path of the file, for example
```
/home/warius/code/hello-world.c
```

Are you familiar with the basic commands in terminal?
```
cd, ls -l, cp, mv, chmod, sudo
```

Post the result of the following command (modified to fit the actual situation)
```
ls -l /home/warius/code/hello-world.c
```

---

### Post by WariusBirde on 2012-01-21
> **dino99 said:**
> you need to run:

gksu gedit yourfile2edit

This worked, thanks! But is there a way to have it save as something other than Readonly so I don't have to reenter gksu? (Not that I really mind doing it really.) I don't quite understand what gksu is anyway, Google seems to think its a beefed up sudo or the like.


> **sudodus said:**
> Where is your file stored? What file system is it and what permissions? It seems that your file is read-only, which can be changed if you the details.

So please give the full path of the file, for example
```
/home/warius/code/hello-world.c
```

Are you familiar with the basic commands in terminal?
```
cd, ls -l, cp, mv, chmod, sudo
```

Post the result of the following command (modified to fit the actual situation)
```
ls -l /home/warius/code/hello-world.c
```

*Where is your file stored? *
See path below.

*What file system is it and what permissions?*
Whatever the standard settings with 11.10 are. I'm the only account on this computer so I should have full run of things as far as I am aware.

The path is

```
/home/warbird/Coding/Goodbye.C
```

I'm familiar with cd, ls, and sudo, but cp and mv are new to me.

And the ls -l produces:

-rw-rw-r-- 1 warbird warbird 72 2012-01-17 18:10 /home/warbird/Coding/Goodbye.C

---

### Post by sudodus on 2012-01-22
> **WariusBirde said:**
> This worked, thanks! But is there a way to have it save as something other than Readonly so I don't have to reenter gksu? (Not that I really mind doing it really.) I don't quite understand what gksu is anyway, Google seems to think its a beefed up sudo or the like.




*Where is your file stored? *
See path below.

*What file system is it and what permissions?*
Whatever the standard settings with 11.10 are. I'm the only account on this computer so I should have full run of things as far as I am aware.

The path is

```
/home/warbird/Coding/Goodbye.C
```

I'm familiar with cd, ls, and sudo, but cp and mv are new to me.

And the ls -l produces:

[COLOR="Red"]-rw-rw-r-- 1 warbird warbird[/COLOR] 72 2012-01-17 18:10 /home/warbird/Coding/Goodbye.C
gksu and gksudo are sudo commands for GUI applications (or other cases) when sudo would not work properly. For example run
```
gksudo nautilus
``` but ```
sudo ls -l
```

***cp*** is the copy command, similar to copy in dosprompt
***mv*** is the move command, similar to move in dosprompt
***chmod*** is the command to change the file permissions (read/write/execute), a distant relative to attrib in dosprompt

Your output of ***ls -l*** shows that the file has read and write permissions for the owner and the members of his/her group (warbird). In other words, when you are logged in as warbird, you should be able to read-edit-write the file. You should not need superuser privileges. But other people (not the owner or not in the group) can only read the file.

So you should be able to write the file. Could the file have been temporarily locked by some other application (for example another instance of gedit or some other editor)? When in your Coding directory, run the command, edit and try to save the file again.
```
warbird@raven-ubuntu:~/Coding$ [COLOR="Red"]gedit Goodbye.C &[/COLOR]
```

Anyway, in the terminal you set the permissions with ***chmod*** and you watch the permissions with ***ls -l***. Read about chmod in the manual pages ```
man chmod
``` and browse for it on the internet.

You can also set and watch the permissions in the file browser Nautilus by right-clicking on a file, select properties, then permissions, but I suggest that you use the terminal commands.

---

### Post by WariusBirde on 2012-01-22
Thanks!

---

