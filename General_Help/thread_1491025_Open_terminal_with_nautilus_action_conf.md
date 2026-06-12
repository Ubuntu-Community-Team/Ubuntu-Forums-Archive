---
title: "Open terminal with nautilus action conf"
date: 2010-05-23
forum: General Help
---

### Post by TryHarder on 2010-05-23
Hello to everybody. 
I'd like to setup my ubuntu to open terminal from nautilus window (right click and 'Terminal'). I've succeded in this with nautilus action configuration feature. However, I also want that working directory in terminal will be similar to folder it was called from. For now it always opens terminal to home directory. So I've tried to pass as argument --working-directory="$PWD", but this wasn't helpful, and it makes sence, because PWD is env. var. of gnome-terminal. 
So, the question is. What should I pass as argument to --working-directory? Is there some gnome env.var. that is similar to PWD?
Thanks.

---

### Post by VeeDubb on 2010-05-23
How did you set it up originally?

I set it up by installing the package for it through synaptic, and it has defaulted to the same directory for a working directory as the one I opened it from.

---

### Post by mc4man on 2010-05-23
There is a nautilus extension you can install
 nautilus-open-terminal

for nautilus actions it would be
command
```
gnome-terminal
```

parameters
```
--working-directory=%d/%f
```

conditions - on folders only

---

### Post by TryHarder on 2010-05-23
> How did you set it up originally?
Installed nautilus configurations from aptitude. They got intuitive GUI. 


> --working-directory=%d/%f
:cool: worked. Thank you. May I still get some explanation about %d %f creatures? Who's those guys?

---

### Post by mc4man on 2010-05-23
Well look at the parameters list (legend) in n.a. -[COLOR="Blue"] %d [/COLOR]equals the "base directory" , %f equals name of file or folder (what you clicked on

[COLOR="Blue"]base[/COLOR]/folder

so if folder was on the desktop - [COLOR="Blue"]$HOME/Desktop[/COLOR]/folder clicked on

---

### Post by TryHarder on 2010-05-25
Well, thank you.

---

