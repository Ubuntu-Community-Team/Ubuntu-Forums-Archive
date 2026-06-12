---
title: "Odd Bash behavior"
date: 2009-09-13
forum: General Help
---

### Post by codemyster on 2009-09-13
I'm noticing some odd behavior in Bash regarding new lines and command history. Namely, using the command history via the "up" or "down" arrows makes about ~4 characters of the previous command stick to the console. Regarding new lines, it seems that whenever I enter a line that is longer than what the window allows it stays smushed onto one line rather than going onto a new one.  Here's a screenshot demonstrating the behavior:

[img]http://nek.ath.cx/notright.png[/img]

The first line should read "this is a very long line of text that is being used to demonstrate an odd behaviour".

The second line is just running scrot for any random reason, and the next is what happens when I press the up arrow. I cannot erase the "scro"

The next line is just me narrating what I'm doing :)

And finally the next line is pressing "up" twice. Also note that when the text is stuck to the line that it does in fact wrap the text to a new line.

My PS1 variable: ```
\e[32;1m[ Mah Laptop \w ]\n\e[0m$
```

Also, I've narrowed this down to a problem with Bash and not with Gnome-terminal. This happens in xterm, rxvt, and a variety of other shells as well.

Can anyone lend me a hint here?

---

### Post by codemyster on 2009-09-13
Figured I'd bump one time before I passed out from exhaustion.

---

### Post by codemyster on 2009-09-13
Anyone?

---

### Post by codemyster on 2009-09-13
Last bump, I promise.

---

### Post by geirha on 2009-09-13
Non-printable characters in the prompt should be enclosed inside \[ \], otherwise bash loses count on how long the prompt is.

```
PS1='\[\e[32;1m\][ Mah Laptop \w ]\n\[\e[0m\]\$ '
```

This is explained in the PROMPTING chapter of bash's manual page - «man bash».

---

### Post by codemyster on 2009-09-13
> **geirha said:**
> Non-printable characters in the prompt should be enclosed inside \[ \], otherwise bash loses count on how long the prompt is.

```
PS1='\[\e[32;1m\][ Mah Laptop \w ]\n\[\e[0m\]\$ '
```

This is explained in the PROMPTING chapter of bash's manual page - «man bash».

I guess you learn something new every day. It's resolved now. 

Thanks.

---

