---
title: "how to permanently keep colored shell prompt"
date: 2010-11-03
forum: General Help
---

### Post by danac on 2010-11-03
After I succesfully instaled ubuntu 10.04 server, I applied
 
**export PC1="\[\e[36;1m\]\u@\[\e[31;1m\]\h:\w\$ \[\e[32m"**
 
and my prompt was nice and colorfull.
But, when I make logout and login, my prompt appears all green (**[COLOR=seagreen]\[\e[32m[/COLOR]**.)
After restart, nevertheless, it looses color settings (of course) and appears plain white. 
 
What should I do in order to keep my prompt color settings permanently?
 
thanx

---

### Post by Barriehie on 2010-11-03
> **danac said:**
> After I succesfully instaled ubuntu 10.04 server, I applied
 
**export PC1="\[\e[36;1m\]\u@\[\e[31;1m\]\h:\w\$ \[\e[32m"**
 
and my prompt was nice and colorfull.
But, when I make logout and login, my prompt appears all green (**[COLOR=seagreen]\[\e[32m[/COLOR]**.)
After restart, nevertheless, it looses color settings (of course) and appears plain white. 
 
What should I do in order to keep my prompt color settings permanently?
 
thanx

Put your line where you define your prompt in your ~/.bashrc file.

Edit: I use this, same thing for root except red path.
```

#
#   Set the prompt(s)
#   Bright green /path/ >
#
export PS1='\033[1;32m\T $PWD \$ \033[1;36m>\033[1;37m '

case $TERM in
dumb)
export PS1='\u@\h \W\$ '
esac

#
#    Colored manpages
#
export LESS_TERMCAP_mb=$'\E[01;31m'       # begin blinking
export LESS_TERMCAP_md=$'\E[01;33;5;74m'  # begin bold
export LESS_TERMCAP_me=$'\E[0m'           # end mode
export LESS_TERMCAP_se=$'\E[0m'           # end standout-mode
export LESS_TERMCAP_so=$'\E[38;5;246m'    # begin standout-mode - info box
export LESS_TERMCAP_ue=$'\E[0m'           # end underline
export LESS_TERMCAP_us=$'\E[04;36;5;146m' # begin underline

```

---

### Post by stinkeye on 2010-11-03
You can have a colored prompt by searching for and uncommenting the line
```
force_color_prompt=yes
```
in your **~/.bashrc** file.

---

### Post by danac on 2010-11-03
well...
i managed to enable coloring. now i will play a bit until i hit the right combination.
 
thanx a lot
 
cheers

---

### Post by iBojan on 2010-11-25
How to add &#9492; ( Alt-192) into prompt?

---

