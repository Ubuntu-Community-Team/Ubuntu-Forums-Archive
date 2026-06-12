---
title: "short path on command line"
date: 2011-03-01
forum: General Help
---

### Post by v923z on 2011-03-01
Hi All,

I have a quick question: how can I make the path short on the console? My problem is that if I descend 10 levels in a directory tree, the path becomes so long that it takes more, than one line of the console window. Is there a way to shorten it, and show only the name of the current directory, without the whole path, i.e., instead of 
```

v923z@penguin: first/second/third/fourth/fifth/sixth/seventh/eighth/ninth/tenth>

```only
```

v923z@penguin: tenth>

```Thanks,
Zoltán

---

### Post by nothingspecial on 2011-03-01
Sure,

edit your bashrc

```
nano .bashrc
```

and on the line (or lines) that starts PS1=

change the lowercase \w into an upper case \W

eg ```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR="Red"]W[/COLOR]\$ '
```

Then get bash to read your new bashrc
```

. ~/.bashrc
```

---

### Post by v923z on 2011-03-01
Many thanks for the reply! This did the trick. The only thing that I would perhaps add is that by leaving the terminal header alone (i.e., not changing w to W), the full path is shown on the title bar of the terminal window, which I found quite useful.
Cheers,
Zoltán

---

### Post by nothingspecial on 2011-03-01
You could also just change the PS1 variable on the cli if you only wanted this to be temporary

or have 2 or more .bashrcs

eg ```
cp /etc/skel/.bashrc ~/.bashrc1
```

Then customise your prompt as you wish and start a new instance of bash with the --rcfile option like so

```

[COLOR="Blue"]ns@box:The Avant-Garde$[/COLOR] bash --rcfile bashrc1
[COLOR="Red"]ns@box:~/Music/John Coltrane/The Avant-Garde$[/COLOR] exit
exit
[COLOR="Blue"]ns@box:The Avant-Garde$[/COLOR]
```

---

### Post by zobayer1 on 2012-07-14
> **nothingspecial said:**
> Sure,

edit your bashrc

```
nano .bashrc
```and on the line (or lines) that starts PS1=

change the lowercase \w into an upper case \W

eg ```
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\[COLOR=Red]W[/COLOR]\$ '
```Then get bash to read your new bashrc
```

. ~/.bashrc
```

Thanks man! solved my problem :D

---

### Post by matt_symes on 2012-07-14
Old thread.

Going to sleep. ZZZZZzzzzzz

---

