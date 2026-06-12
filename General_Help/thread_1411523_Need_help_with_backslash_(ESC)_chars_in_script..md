---
title: "Need help with backslash (ESC) chars in script."
date: 2010-02-20
forum: General Help
---

### Post by jptech on 2010-02-20
Hi,

I have a script where I use escape codes to align some of the output:

```
let jump=`tput cols`-${#MESSAGE}-${#SUCCESS}-2
MESSAGE+="\033[${jump}C $SUCCESS"
```All it does is align [OK] or [FAILED] at the end of a line.  It works fine when I run it in a terminal, but as soon as I try to e-mail the output to myself or save the output to a file and open it in an editor, I get a bunch of ESC chars.

Does anyone know of a way I can replace \033[${jump}C with spaces?  I could probably use:

```
if tty -s; then
        let jump=`tput cols`-${#MESSAGE}-${#SUCCESS}-2
    else
        let jump=80-${#MESSAGE}-${#SUCCESS}-2
fi
```The only thing is I don't know of an easy way to add an arbitrary number of spaces to my output.  Is there a command that will, for example, let me add 32 spaces to my output?

Ex:

```
MESSAGE+="put 32 spaces here $SUCCESS"
```Thanks.

---

