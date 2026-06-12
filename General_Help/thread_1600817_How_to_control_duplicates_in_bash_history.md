---
title: "How to control duplicates in bash history"
date: 2010-10-19
forum: General Help
---

### Post by Rubi1200 on 2010-10-19
Hi,
I have tried a combination of the following lines in .bashrc to try and control duplicates in the bash history file:

export HISTCONTROL=ignoreboth
export HISTCONTROL=erasedups
export HISTCONTROL=ignoredups
export HISTIGNORE="&"

This is fine for ignoring the _last_ command in history, but what I want to do is control all commands.

For example, if the history command shows something like this:
 > 1  uname -r
    2  cat /etc/fstab
    3  sudo update-grub
    4  ls -l
    5  sudo chmod -R 700 ~
    6  env
    7  history
    8  w
    9  historyhow do I get it to ignore duplicating when running, for example, command number 7 again?

All help appreciated and thanks in advance.

---

### Post by Barriehie on 2010-10-19
How about using inotifywait in a daemon and when the file is changed, i.e. written to, then run it through uniq to a tmp file and then rename it.  Not really elegant but it should run fast enough you can't out type it.

---

### Post by Rubi1200 on 2010-10-20
Thanks, I appreciate the response.

However, is it not possible to have a more fine-grained control over bash history than the method you suggested?

EDIT: apparently this may be a bug:
[https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881](https://bugs.launchpad.net/ubuntu/+source/bash/+bug/189881)

Nevertheless, I would like to try and find a way to work this out.

---

### Post by stinkeye on 2010-10-20
Don't know if this is useful to you but this lists your most used commands.
```
history | awk '{print $2}' | sort | uniq -c | sort -rn | head -20
```

---

### Post by Rubi1200 on 2010-10-20
Thanks stinkeye; I know that I can use HISTIGNORE with parameters to suppress the most commonly used commands from being duplicated, but this seems like an awkward solution.

For example, export HISTIGNORE="&:ls:free -m:exit" would prevent the last used command, ls, free -m, and exit from being duplicated. 

Found this tip:
> If you include the expression "[ \t]*" in the HISTIGNORE string, you can suppress history recording at will for any given command just by starting with a space![U]
[http://www.talug.org/events/20030709/cmdline_history.html](http://www.talug.org/events/20030709/cmdline_history.html)
[/U] 
Do you think this is a practical solution?

---

### Post by Rubi1200 on 2010-10-20
> **Rubi1200 said:**
> Found this tip:

[http://www.talug.org/events/20030709/cmdline_history.html](http://www.talug.org/events/20030709/cmdline_history.html)

Do you think this is a practical solution?
To answer my own question (and shamelessly bump this thread for which I humbly apologize :oops:):

This is not a real solution, just a quick fix, because:

1. you have to ALWAYS remember to put a space before the command you want to run

2. it does not save the command into bash history and I want to see the list of commands used, just not duplicated ad infinitum

Any other ideas out there?

---

