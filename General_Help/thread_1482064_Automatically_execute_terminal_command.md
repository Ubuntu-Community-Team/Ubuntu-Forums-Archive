---
title: "Automatically execute terminal command"
date: 2010-05-13
forum: General Help
---

### Post by peterofferman on 2010-05-13
Maybe this is a very stupid question, but I googled around and couldnt find what I was looking for. Maybe I used the wrong search terms, but whatever....

I was wondering if there was a possibility to execute a series of terminal commands just by double-clicking an icon. 

For example, there would be an icon on my desktop, and if I were to doubleclick it, it would execute "cd ~/.wine2" and then "WINEPREFIX="$HOME/.wine2" wine program.exe".

I realise that most of you will probably go "duh, that's simple" or something similar, but I am extremely new to ubuntu, and dont know my way around yet.

---

### Post by peterofferman on 2010-05-13
anybody?

---

### Post by pmlxuser on 2010-05-13
why not creat a bash script, and then put it in /usr/local/sbin

@ which point you could creat a short cut on desktop to do what you want..
ie
```

$cat >> myscript
#! /bin/bash
cd ~/.wine2
WINEPREFIX="$HOME/.wine2 
wine winfolder/program.exe
[ctrl +C]

```

then
```

chmod +x myscript
sudo mv myscript  /usr/local/sbin/

```

then creat link on the desktop
```

cd ~/Desktop
ln -s mylink /usr/local/sbin/myscript

```

please not that the above is just an example of how you would do the script.. am not vey concersant with wine to write the actual script..

---

### Post by peterofferman on 2010-05-13
a bash script eh? Never heard of it... I'll research it. Thanks a lot :)

---

