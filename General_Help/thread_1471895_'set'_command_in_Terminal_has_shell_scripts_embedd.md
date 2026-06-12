---
title: "'set' command in Terminal has shell scripts embedded inside?"
date: 2010-05-03
forum: General Help
---

### Post by sshetye on 2010-05-03
Ok, I just installed Ubuntu 10.04 for some development. I was trying to set some environment variables are noticed that when I hit 'set' inside a terminal (to dump environment vars) I get the usual first few variables but then I see a whole lot of script code .... 

Its QUITE long, so copy-pasting just the point where is starts getting weird ...

```
WINDOWID=23068675
XAUTHORITY=/var/run/gdm/auth-for-sid-5IDovs/database
XDG_CONFIG_DIRS=/etc/xdg/xdg-gnome:/etc/xdg
XDG_DATA_DIRS=/usr/share/gnome:/usr/local/share/:/usr/share/
XDG_SESSION_COOKIE=f858cd67db7215e6c2a47c214bdeefbc-1272902816.143978-851081700
_=set
bash205='4.1.5(1)-release'
bash205b='4.1.5(1)-release'
bash3='4.1.5(1)-release'
bash4='4.1.5(1)-release'
_ImageMagick () 
{ 
    local prev;
    prev=${COMP_WORDS[COMP_CWORD-1]};
    case "$prev" in 
        -channel)
            COMPREPLY=($( compgen -W 'Red Green Blue Opacity \
                Matte Cyan Magenta Yellow Black' -- "$cur" ));
            return 0
        ;;
        -colormap)
            COMPREPLY=($( compgen -W 'shared private' -- "$cur" ));
            return 0

<<<many, many screens of code, sub routines etc here>>>


```

I've installed a lot of tools (NetBeans, Ruby, Java, build-essentials etc) but essentially I installed Ubuntu today - so it shouldn't have rotted out this quickly.

Sooo ... is this hijacking of environment vars to embed script code intentional with Ubuntu 10.04? Seems like poor practice ... if it's not, then I need to figure out what's causing it at my end (not that's its destructive so far ...)

---

### Post by gmargo on 2010-05-04
Those functions are for command completion, and come from the file **/etc/bash_completion**, which is sourced by the default **.bashrc**.

If you comment out those lines in your **$HOME/.bashrc**, then log out/in, those functions will not appear.  The (supposedly) smart completion will not work either, but you're probably not using it anyway.

If you just want to dump environment variables, use the **env(1)** command.  The "set" command that you're using is a **bash(1)** internal that dumps all variables (exported or not) and functions.

---

