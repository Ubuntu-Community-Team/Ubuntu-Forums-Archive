---
title: "Bash history problem"
date: 2006-02-01
forum: General Help
---

### Post by abovett on 2006-02-01
Bash history expansion doesn't seem to work properly for me under Breezy. For example, if I have typed:```
ls /usr/local/share/emacs
``` and then later on I type ```
cd !ls:^
``` that should expand to ```
cd /usr/local/share/emacs
``` but instead I just get **bash: !ls:^: event not found**. This does work on Mandriva and should work according to the Bash man page. Can anyone suggest what's going wrong? Is it a bug in this version of bash?

---

### Post by dcstar on 2006-02-01
[QUOTE=abovett]Bash history expansion doesn't seem to work properly for me under Breezy. For example, if I have typed:```
ls /usr/local/share/emacs
``` and then later on I type ```
cd !ls:^
``` that should expand to ```
cd /usr/local/share/emacs
``` but instead I just get **bash: !ls:^: event not found**. This does work on Mandriva and should work according to the Bash man page. Can anyone suggest what's going wrong? Is it a bug in this version of bash?[/QUOTE]
**extglob** shell option is probably not enabled (use shopt to see if it is)

---

### Post by abovett on 2006-02-01
[QUOTE=dcstar]**extglob** shell option is probably not enabled (use shopt to see if it is)[/QUOTE]

Sorry - it is enabled, so that's not it :(

Any other ideas?

Andy B

---

### Post by abovett on 2006-02-01
Found it - and it looks like it's a bug.

Got the clue from here: 
[http://lists.gnu.org/archive/html/bug-bash/2005-11/msg00026.html](http://lists.gnu.org/archive/html/bug-bash/2005-11/msg00026.html)

It looks like history expansion doesn't work right if UTF-8 is being used, and of course that's now the default for Ubuntu.

Changing LANG to en_GB rather than en_GB.UTF-8 and launching a new bash shell causes it to work as expected.

Guess I'll post a bug report, though I guess it'll be pretty low priority for most people (how many Ubuntu users live mostly at the bash prompt, like me?).

UPDATE: Someone else has already raised the bug (some time ago) but it looks like it's not entirely consistent (it seems Matt Zimmerman couldn't reproduce it). The bug number on Malone is Bug #9979.

---

