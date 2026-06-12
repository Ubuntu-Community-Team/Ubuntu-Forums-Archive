---
title: "Can't Gedit as Root?"
date: 2006-05-24
forum: General Help
---

### Post by veev on 2006-05-24
I am a newbie trying to edit my xconf. So I type sudo -i to change to root (I have to do this, correct?). Once I'm logged in as root, if I try to run gedit, I get: 
(gedit:9468): Gtk-WARNING **: cannot open display:
I can't stand vi, is there any other notepad like editor that I can use to edit things while logged in as root?

---

### Post by daschl on 2006-05-24
try this:

sudo gedit (you have to run this as "normal" user)

if it doesnt work, try "gksudo" :)

---

### Post by veev on 2006-05-24
Tried both of those...but it gives the same error.

---

### Post by dmizer on 2006-05-24
i haven't had alot of luck with gedit ... crashes on me frequently.

i just use nano ... it's commandline like vi, but it's much more user friendly imo.

---

### Post by edeCh on 2006-05-24
you could try using sudo -s:

```

~/scratch$ sudo -s
Password:
~/scratch# gedit 
```

if things do not work then,you could also have a look if 

```

xhost +
```

entered on a non-root shell helps; hope that helps; cu ede:)

---

### Post by Isoss on 2006-05-24
I use 
```
sudo gedit /~/~/
```
and it just works. of course  I run this when I am a normal user and it prompts for password. but I guess you can also try this:
```
sudo su
```
Then enter your password. then run gedit.

---

### Post by ed_agamemnon on 2006-05-24
recently my Gedit has stopped opening from the console with sudo:

```
sudo gedit &
```

... returns a blank line and gedit just doesn't ever come up.

where as:

```
gedit &
```

... works perfectly!

anyway - i've leared to use vi instead. i was just wondering what the problem could've been. and ideas?

---

### Post by edeCh on 2006-05-24
[QUOTE=ed_agamemnon]recently my Gedit has stopped opening from the console with sudo:

```
sudo gedit &
```

... returns a blank line and gedit just doesn't ever come up.

where as:

```
gedit &
```

... works perfectly!

anyway - i've leared to use vi instead. i was just wondering what the problem could've been. and ideas?[/QUOTE]

it might be that if you send your process to the background then you can't supply the password when its requested:
```
scroll:~$ sudo gedit &
[2] 11618
scroll:~$ Password:


[2]+  Stopped                 sudo gedit

```

```
scroll:~$ sudo gedit
Password:

```
works on my machine; you can send it to the background using <CTRL + z> , followed by 
```
bg
``` 
then if you want to use the terminal window; 

you also can run 

```

gksudo gedit

``` 

as mentioned by daschl or perhaps 

```

kdesu gedit

``` 

hope that helps cu ede

---

### Post by Zimmer on 2006-05-24
[QUOTE=ed_agamemnon]recently my Gedit has stopped opening from the console with sudo:


anyway - i've leared to use vi instead. i was just wondering what the problem could've been. and ideas?[/QUOTE]
The problem is probably that because you were editing  xorg.conf then  you did not have X running...
gedit requires it... hence the need to use nano or pico as editors because they do not require X to be running....

---

### Post by ed_agamemnon on 2006-05-24
it could be the background thing - i'll check that out.

- and no, i wasn't editing xorg.conf, yes I did have X running. Gedit can still edit xorg.conf inside X anyway. maybe i should've said 'from the terminal' instead of 'from the console'...

---

