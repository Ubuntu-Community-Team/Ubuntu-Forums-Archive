---
title: "auto complete option  not working 9.10"
date: 2009-12-27
forum: General Help
---

### Post by karian021 on 2009-12-27
hi guys i have a problem i kinda like made a new install i erased almost every hidden folder  in the home folder and i reinstalled ubuntu 64 9.10,i formated  the the boot and / partition  and the home partition i didn't format it,i didn't  want to lose all my stuff,now every time i open up a terminal an try to use the auto-complete option [tab] it doesn't work like if i try to do and update i type sudo apti[tab] or sudo apt-g[tab] or something like that and it doen't work,can you help me with this problem? :(

---

### Post by sisco311 on 2009-12-27
Is bash-completion installed?
```
sudo apt-get install bash-completion
```

If you don't have a ~/.bashrc file, then copy the default file in your home directory and source it:

```
cp /etc/skel/.bashrc ~
. ~/.bashrc
```

If you use a custom ~/.bashrc file, then append it with:
```

if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

---

### Post by karian021 on 2009-12-27
thanks a lot  i had it installed but for some reason  it wasn't working i had to  do 

cp /etc/skel/.bashrc ~
. ~/.bashrc
and now it works like a charm,i'm so happy   :grin:  THANKS.

---

### Post by sisco311 on 2009-12-27
> **karian021 said:**
> thanks a lot  i had it installed but for some reason  it wasn't working i had to  do 

cp /etc/skel/.bashrc ~
. ~/.bashrc
and now it works like a charm,i'm so happy   :grin:  THANKS.

Cool!!!

Please mark your thread as [SOLVED] by selecting **Mark this thread as solved** from the [color="Red"]Thread tools[/color].

---

