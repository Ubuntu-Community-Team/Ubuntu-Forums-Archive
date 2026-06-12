---
title: "Terminal problems &lt;newbie&gt;"
date: 2006-02-03
forum: General Help
---

### Post by riwa on 2006-02-03
Ok. My first post just dissapeared so I'll be somewhat brief...

3 problems:

1. Using terminal to download. Eg. I have the adress but wants to download it from the terminal. What's the correct syntax?

2. Setting envvar TERM='gnome-terminal' gives me several error messages while:
ex. *info command* and *clear*/*Ctrl-L*. 
ouput= gnome-terminal is not recognised or us to dump to perform the action. 

3. aliasing ls with starting and ending echo statements:
*alias ls='echo ; ls ; echo*
works fine until i try to invoke it with options(-al) etc. alias set in :-? .bashrc..

Regards
Richard

---

### Post by greenpenguin on 2006-02-03
For 1: sudo apt-get install wget.  Then wget whatever

---

### Post by riwa on 2006-02-03
I didn't get it to work. It tells me:

$ sudo apt-get install wget [http://voxel.dl.sourceforge.net/sourceforge/suparun/wesnoth-1.1-x86-Opkg.tar.gz](http://voxel.dl.sourceforge.net/sourceforge/suparun/wesnoth-1.1-x86-Opkg.tar.gz)
Reading package lists... Done
Building dependency tree... Done
wget is already the newest version.
E: Couldn't find package http:

---

### Post by GeneralZod on 2006-02-03
[QUOTE=riwa]I didn't get it to work. It tells me:[/QUOTE]

Use:

```
wget http://voxel.dl.sourceforge.net/sourceforge/suparun/wesnoth-1.1-x86-Opkg.tar.gz
```

Also

```

TERM=gnome-terminal

```

> 
3. aliasing ls with starting and ending echo statements:
alias ls='echo ; ls ; echo
works fine until i try to invoke it with options(-al) etc. alias set in .bashrc..


I don't think you'll be able to do this with alias, I'm afraid.

---

### Post by riwa on 2006-02-03
Well that was it! Thank you very much...

I have no idea why but it's so much faster from the terminal...

By the way... By *ctrl-z ; bg* doesn't  work. Don't want to restart and try it but will *wget [http://thingy](http://thingy) &* work

---

### Post by GeneralZod on 2006-02-03
> **riwa]
By the way... By *ctrl-z  said:**
> http://thingy[/url] &* work

You need to provide an argument to bg - this will be the number in the brackets when you press CTRL+Z, shown as x below:

```

[**x**]+  Stopped                 wget http://voxel.dl.sourceforge.net/sourceforge/suparun/wesnoth-1.1-x86-Opkg.tar.gz
bg %**x**

```

---

### Post by kabus on 2006-02-03
> 3. aliasing ls with starting and ending echo statements:
alias ls='echo ; ls ; echo
works fine until i try to invoke it with options(-al) etc. alias set in .bashrc..

That's because the options will be added after the last echo.
Use a function instead :
```

foo () { echo; ls "$@"; echo; }
```

---

### Post by riwa on 2006-02-03
Ok. Usually, though, bash backgrounds the last stopped operation, but I guess of course its better to use correct syntax...

The TERM=gnome-terminal doesn't work though. Tried with/without ''. Many things work but not all.

---

