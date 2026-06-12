---
title: "vi syntax on"
date: 2012-07-19
forum: General Help
---

### Post by buffchick on 2012-07-19
So uh... yeah. I've googled this. A lot. And I'm probably just not searching for the right thing but, how do I turn the color syntax on in vi?

ubuntu 12.04 LTS

---

### Post by drmrgd on 2012-07-19
Like this?

[http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/](http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/)

---

### Post by sudodus on 2012-07-19
If this option is included your version, it should be available with the command ```
:syntax on
``` but I don't think it is included in Ubuntu 12.04.

[[COLOR="Red"]_http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/_[/COLOR]]("http://www.cyberciti.biz/faq/turn-on-or-off-color-syntax-highlighting-in-vi-or-vim/")

However, there is good support for high-lighting in gedit and emacs.

---

### Post by buffchick on 2012-07-19
yeah, it's not supported in 12.04. I get the error [COLOR=Red]E319: Sorry, the command is not available in this version.[/COLOR]

And can't use gedit or emacs. Sorry, should have specified 12.04 LTS server :D

---

### Post by sudodus on 2012-07-19
> **buffchick said:**
> yeah, it's not supported in 12.04. I get the error [COLOR=Red]E319: Sorry, the command is not available in this version.[/COLOR]

And can't use gedit or emacs. Sorry, should have specified 12.04 LTS server :D

Yes, you can :-) ```
emacs -nw
``` makes it run in a terminal window, and if you run via ssh text mode, this will probably be chosen automatically without the nw option. (It does for me in 10.04 LTS)

---

### Post by buffchick on 2012-07-19
I'm perfectly ok with VI.

---

### Post by sudodus on 2012-07-19
> **buffchick said:**
> I'm perfectly ok with VI.

Sure, vi and vim are very nice when you know how to use them, but you wanted colours ...

---

### Post by buffchick on 2012-07-19
only because my 10.04 has colors. It's always had colors.

---

### Post by spjackson on 2012-07-19
> **buffchick said:**
> only because my 10.04 has colors. It's always had colors.
The vim packages installed by default in 12.04 (and earlier versions too I believe) are vim-tiny and vim-common. vim-tiny has limited functionality and does not have syntax coloring.

You need to install additional vim packages. I'm not sure what would be a minimal set to provide this feature because I always install one of the gui vim packages, which includes syntax coloring when run in a terminal as a bonus. If you can't find which extra vim packages to install, come back and I'll find out.

---

### Post by sudodus on 2012-07-19
> **spjackson said:**
> The vim packages installed by default in 12.04 (and earlier versions too I believe) are vim-tiny and vim-common. vim-tiny has limited functionality and does not have syntax coloring.

You need to install additional vim packages. I'm not sure what would be a minimal set to provide this feature because I always install one of the gui vim packages, which includes syntax coloring when run in a terminal as a bonus. If you can't find which extra vim packages to install, come back and I'll find out.
You helped us both :KS

```
sudo apt-get install vim
``` made my vim work with colours.

Thanks :-)

---

### Post by buffchick on 2012-07-19
Yup! that did it for me! THANKS!

---

