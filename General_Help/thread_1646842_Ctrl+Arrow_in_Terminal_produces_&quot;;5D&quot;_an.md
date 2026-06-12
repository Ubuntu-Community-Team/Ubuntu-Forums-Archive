---
title: "Ctrl+Arrow in Terminal produces &quot;;5D&quot; and &quot;;5C&quot;"
date: 2010-12-16
forum: General Help
---

### Post by mvmacd on 2010-12-16
I just installed Ubuntu 10.10 64-bit, testing it out to see if it will become my Primary OS, [which used to be openSUSE].
I used my old /home partition from openSUSE.

So anyway, I open a terminal, and when I press ctrl+left, instead of going back 1 word, it writes  ";5D"
if I do ctrl+right, it does ";5C" :confused:
I googled, and found somebody else with the problem.
I did what fixed it for them, edited /etc/inputrc. 

This is what it looked like before:

```

...
# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[5C": forward-word
"\e[5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word
...

```

And what it looks like now: 

```

...
# mappings for Ctrl-left-arrow and Ctrl-right-arrow for word moving
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e[1;5C": forward-word
"\e[1;5D": backward-word
"\e\e[C": forward-word
"\e\e[D": backward-word
...

```

Because the thread [on another website, not Ubuntu] the person said to change "\e[5D" to "\e[1;5D".... Anyway, it didn't work for me. I even tried rebooting. And also commenting out the 2 last lines of the copy/paste above. [the 2 "\e\e" lines] Though I didn't reboot. Does anybody know how to fix this? It is really annoying, I use ctrl+arrow shortcut ALL the time! [as well as tons of other ctrl+ shortcuts]. It would be **so** annoying if I had to leave it like this. :-k
Thanks in advance!

Note: When I SSH into my iPod Touch [jailbroken w/ openSSH] the ctrl+arrow doesn't work, it does the same thing my laptop is now doing. :-|

**EDIT:** I just noticed that when I am root, ctrl+arrow works fine! But when I am my regular user ["matt"], it does **not** work! o_O

Edit: Ok. so I copied /etc/inputrc to ~/.inputrc, and it works!

---

### Post by eGelor on 2011-08-30
That works for me thanks. Al thought that previus commands where 
bindkey '^[[5D' emacs-backward-word
bindkey '^[[5C' emacs-forward-word

---

