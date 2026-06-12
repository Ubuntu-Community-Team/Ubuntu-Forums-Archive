---
title: "How to access my folders by CLI? Where did they go?"
date: 2011-03-16
forum: General Help
---

### Post by kleinebre on 2011-03-16
Lately (since about Ubuntu 9.10 though I'm on 10.4 now) there seems a trend towards showing folders in the GUI but not
through the command line interface. Most prominent examples are 
the trash folder ("Waste basket", nowadays) and Samba mounts.

As it happens, I *like* the command line and would rather access those folders from CLI rather than having to use the GUI. 

The folders don't show up in /etc/mtab either. Yet in "Places" they show up with an eject button next to them, implying they're mounted. Right clicking the folders in "Places" doesn't allow me to show folder properties or path. It doesn't give any further clues.

So, where did my trash folder, samba mounts, usb drives go? :confused: I'd like to be in control of my system rather than to have it control me!

---

### Post by lithopsian on 2011-03-16
Hidden files and folders have names starting with a dot.  By default "ls" does not show them.  You can show them with "ls -a".  Maybe you want to alias that.  Most GUI file managers have a toggle to show the hidden files or not and the default is generally not.

---

### Post by seawolf167 on 2011-03-16
If you open your terminal, you can show the folders & their properties with 3 commands

show folders & files

```
ls
```show hidden folders & files

```
ls -a
```show folder & file properties

```
ls -l
```by default you have 3 alias' in your bashrc file:

```
alias     long command
ll          ls -alF
la          ls -A
l           ls -CF
```

---

### Post by Morbius1 on 2011-03-16
I'm going to guess that by "samba mounts" you mean after you connect to it from Nautilus. The mount point is at:
> /home/username/.gvfs/share-name on server-name

---

### Post by r.osmanov on 2011-03-16
Make some aliases in ~/.bashrc or ~/.bash_aliases. For instance, 
```
$ cat ~/.bash_aliases
alias ll='ls -alhF'
alias la='ls -A'
alias l='ls -CF'
# ...
```

Ensure that in ~/.bashrc you load these: 
```
if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
Load them:
```
$ source ~/.bashrc
```

Then browse:

```
$ ll ~/Desktop
$ ll ~/Documents
$ ll ~/Music
...
```

---

### Post by r.osmanov on 2011-03-16
I'd also recommend Midnight Commander
```
sudo apt-get install mc
```

---

