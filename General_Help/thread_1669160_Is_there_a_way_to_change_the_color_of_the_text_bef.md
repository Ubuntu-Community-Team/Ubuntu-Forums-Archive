---
title: "Is there a way to change the color of the text before the input at the terminal?"
date: 2011-01-17
forum: General Help
---

### Post by Rodayo on 2011-01-17
I really don't know what to call it, but I want to change the color of text that appears before you type in whatever your input is.

For example:
```
negrabee@david-desktop:~$ ls /home/david/

```

I would want "negrabee@david-desktop:~$" to be in a different color. When you have whole bunch of commands and text in a full screen terminal, it gets really annoying to have to look for where you're entering the command so changing the color would help.

thanks in advance

---

### Post by James78 on 2011-01-17
Edit ~/.bashrc, and uncomment "#force_color_prompt=yes"

If you don't like the colors that gives you, you can play with the colors it displays in this part:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}_\[\033[01;32m\]_\u@\h_\[\033[00m\]_:_\[\033[01;31m\]_\w_\[\033[00m\]_\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```

[http://www.arwin.net/tech/bash.php](http://www.arwin.net/tech/bash.php)

---

### Post by James78 on 2011-01-17
Double post; Ubuntuforums is having those weird mysterious and really annoying proxy errors again.

---

### Post by Smart Viking on 2011-01-17
This is not very pretty but lol, enter this in terminal for red color:
```
PS1="\[\033[0;31m\]negrabee@david-desktop:~$\[\033[1;37m\] "
```
If you want it permanently, enter the same command in the bottom of your bashrc file.

I just used a website to generate that, try yourself:
[http://www.linuxhelp.net/guides/bashprompt/](http://www.linuxhelp.net/guides/bashprompt/)

---

### Post by Rodayo on 2011-01-17
> **James78 said:**
> Edit ~/.bashrc, and change "force_color_prompt=no" to "force_color_prompt=yes"

If you don't like the colors that gives you, you can play with the colors it displays in this part:
```
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}_\[\033[01;32m\]_\u@\h_\[\033[00m\]_:_\[\033[01;31m\]_\w_\[\033[00m\]_\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
```[http://www.arwin.net/tech/bash.php](http://www.arwin.net/tech/bash.php)

The variable was already set to "yes" but how would you change the colors? I mean, I don't see anything in that text that would indicate a color....

Edit: found that part that I had to uncomment silly me. The text is green now but I'd still like to change to something else...

---

### Post by James78 on 2011-01-17
I gave you a link to a guide which shows the color values, and I underlined the parts in the script where the colors are located.

---

### Post by Rodayo on 2011-01-17
> **James78 said:**
> I gave you a link to a guide which shows the color values, and I underlined the parts in the script where the colors are located.
Lol, didn't see that at first. Thanks mate

---

