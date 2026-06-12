---
title: "Bash pipes and redirection"
date: 2006-01-25
forum: General Help
---

### Post by insitu on 2006-01-25
Hi to all,
I recently installed 5.10 on my laptop after a FS crash. Everything worked fine (except suspend to disk) after I discovered the magic irqpoll kernel boot parameter that allowed my ethernet cards to be recognized... I will make an account of this later as my first install (3months ago) was a failure.
My current problem is strange : when i use a  terminal, piped commands and sometimes redirection are not correctly interpreted :

$> cat toto | less
bash: less: command not found 

This is odd !!
Any idea someone ? Locale issues (I use fr_FR.UTF-8)

Thanks

---

### Post by hillbilly on 2006-01-25
hmm...it looks like you dont have the less command on your system. 

try > $/> whereis less
and check whether the path to less is set in your PATH variable with > echo $PATH

---

### Post by insitu on 2006-01-25
This I already checked : less is in /usr/bin as expected and $PATH contains /usr/bin. BTW, less and all commands you could possibly imagine work perfectly standalone (ie. without pipes); Moreover, find has this strange behavior :

$> find . -type d -a -name toto -exec rm -fr {} \;
find: exec: Paramètre manquant pour "exec"

???????????

---

### Post by hillbilly on 2006-01-25
oops  ! Well now I understand, by what you mean could be a locale problem ;) !!

I have not played around with locales, so am at sea here !! Will be watching this thread though !! Best of luck !!

---

### Post by insitu on 2006-02-02
I have found some clues about the behaviour described in the first post. It has something to do with the space character that is produced when I hit spacebar, ie: 

$> find . | less 
-> KO

$> find .|less
-> OK
Note that there is no spaces around the pipe character.

My X11 encoding is pc105/fr/latin9 ?

Anybody has some more advices as to how I can correct this annoying feature ?

Thanks in advance.

PS: I will crosspost to french ubuntu forum.

---

### Post by insitu on 2006-02-08
Hello,
Seems I have a very odd problem: The french forum was unable to solve it !

I desparately need to solve this as it is really annoying, producing random bugs in programs and making tests fail !!

Help or comments appreciated.

Insitu

---

### Post by ultimateclem on 2006-05-05
[QUOTE=insitu]Hello,
Seems I have a very odd problem: The french forum was unable to solve it !

I desparately need to solve this as it is really annoying, producing random bugs in programs and making tests fail !!

Help or comments appreciated.

Insitu[/QUOTE]

Well, just edit your "/etc/X11/xorg.conf" and replace :

*Option          "XkbVariant"    "latin9"*

by 

*Option          "XkbVariant"    "latin1"*

... after all of this it will be OK.

---

