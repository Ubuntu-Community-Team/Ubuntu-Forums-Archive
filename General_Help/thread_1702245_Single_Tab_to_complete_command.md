---
title: "Single Tab to complete command"
date: 2011-03-07
forum: General Help
---

### Post by lime_90 on 2011-03-07
Hi!

I have recently installed Ubuntu 10.10 Server onto a old PC. Everything seems to be working fine except that i can't tab the next command. 
Like when you are typing

cd hom (Then you press tab and the 'e' appears.)

When i double click tab I get a list of all the possible directories but I wont seem to work when I press it one time just to complete my command. :confused:

Anyone got a clue how to fix this?


(I am new to this community but I got to say i Love it. We use Ubuntu at our university and it rocks!)

---

### Post by ianc1 on 2011-03-07
Have you got another directory beginning with "hom"?.  For example ie have ~/Downloads and ~/Documents and when in the ~ directory if I do cd Do and press tab I get nothing a double tab shows the list of options ie the two directories.  If I add the 'c' or 'w' ie the next character in the directory name I can then do tab completion.

As far as I am aware, although, I'm a relative newcomer (1 year ish) this is normal behaviour.

In case you don't know ~ corresponds to me home directory ie /home/myusername

---

### Post by edhplus2 on 2011-03-07
I did this when I first started using Ubuntu and it worked:
add these two lines to ~/.bashrc for command line tab completion:
```

bind 'set show-all-if-ambiguous On'
bind 'TAB:menu-complete

```

---

### Post by AlphaLexman on 2011-03-07
> **lime_90 said:**
> When i double click tab I get a list of all the possible directories but I wont seem to work when I press it one time just to complete my command.
As was stated previously, you must type enough characters to generate a unique identifier, before utilizing the tab key in order to invoke programmable completion.

---

