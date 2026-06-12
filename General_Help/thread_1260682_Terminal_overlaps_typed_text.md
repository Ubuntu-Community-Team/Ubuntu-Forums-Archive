---
title: "Terminal overlaps typed text"
date: 2009-09-07
forum: General Help
---

### Post by nimbis on 2009-09-07
I use gnome-terminal as my terminal, and have customised my .bashrc file.

When I try to type an extended line of text into the terminal, instead of appearing like this:
>   Tuesday, September 08 09:38:41 2009
  Linux 2.6.28-15-generic unknown
  freman @ freman
  ~ $: abcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwx
yzabcde

It appears like this:
>   Tuesday, September 08 09:35:24 2009
  Linux 2.6.28-15-generic unknown
  freman @ freman
yzabcdeabcdefghijklmnopqrstuvwxyzabcdefghijklmnopqrstuvwx 


This is my PS1:
> PS1='\e[42;32m \e[0m \e[1;33m\u @ \h\n\e[42;32m \e[0m \e[1;33m\w \$: \e[0m'

The text only overlaps once, after that it follows normal behavior.

Can anybody give me a hand?

---

### Post by rifak on 2009-09-08
i had the same problem when i edited my .bashrc. its a problem in your editing. you need to start with \[ and end with a \] after each, ummm, command? im not sure if thats the correct word to use, but try that...

---

### Post by nimbis on 2009-09-08
> **switham said:**
> i had the same problem when i edited my .bashrc. its a problem in your editing. you need to start with \[ and end with a \] after each, ummm, command? im not sure if thats the correct word to use, but try that...

That works! Turns out the problem was due to bad coding on my part it seems, thanks a lot!
I changed my code from this:
> PS1='\e[42;32m \e[0m \e[1;33m\u @ \h\n\e[42;32m \e[0m \e[1;33m\w \$: \e[0m' 
to this:
> PS1='\[\e[42;32m\] \[\e[0m\] \[\e[1;33m\]\u @ \h\n\[\e[42;32m\] \[\e[0m\] \[\e[1;33m\]\w \$: \[\e[0m\]'
... and now it works perfectly :)

---

### Post by rifak on 2009-09-08
niiiiiice :guitar:

---

