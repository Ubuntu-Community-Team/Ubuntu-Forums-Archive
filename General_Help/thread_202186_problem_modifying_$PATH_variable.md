---
title: "problem modifying $PATH variable"
date: 2006-06-23
forum: General Help
---

### Post by krazyshane on 2006-06-23
Okay,

I've added the following lines to my ~/.bash_profile files:

> 
PATH=$PATH:~/my_scripts
export PATH


However, if I run "echo $PATH", I still see the following:
> /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

I even tried rebooting (which I figured wasn't necessary... just a windows reminiscence I suppose :rolleyes:   )


Oh, also... How do I add my script to startup?

Thanks,
Shane

---

### Post by oscar on 2006-06-23
I have this in my .bash_profile:
```
# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi
```
so using that as a model you will probably want:
```
# set PATH so it includes user's scripts
if [ -d ~/my_scripts ] ; then
    PATH=~/my_scripts:"${PATH}"
fi
```
As for adding a script to startup do you mean to run every time you open a terminal or to run every time you log in.
For the terminal I think you need to put it in .bashrc
For logging in have a look in System > Preferences > Sessions > Startup Programs

---

### Post by no1wantdthisname on 2006-06-23
It's better to add this to .gnomerc.
Things in .gnomerc get executed automatically (assuming you're using gnome).
And if you use the run dialog (alt+f2), this is the only way to execute commands from the new PATH.
So just create a file
```
touch .gnomerc
chmod +x .gnomerc
gedit .gnomerc
```
and add this
```
#!/bin/sh
PATH=$PATH:~/my_scripts
export PATH
```

---

