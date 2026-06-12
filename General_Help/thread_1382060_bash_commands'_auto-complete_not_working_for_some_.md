---
title: "bash commands' auto-complete not working for some apps"
date: 2010-01-15
forum: General Help
---

### Post by Dragon ELEMENTAL on 2010-01-15
Hiya,
I've got an annoying problem that 'man' and some other commands do not auto-complete (via TAB).

e.g. typing:    man rsyn   (TAB, TAB, TAB, etc)

will not auto-complete to 'man rsync'

however, if i 'sudo -s' & then try the above, 'man' auto-completes everytime.

Any suggestions?

(Directories always auto-complete successfully)

My ~/.bashrc contains:
```
# enable bash completion in interactive shells
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```

Thanx

^_^

---

### Post by Dragon ELEMENTAL on 2010-01-21
Anyone???

I would really appreciate it.

---

### Post by nothingspecial on 2010-01-21
Are you sure you are using bash? Not sh.

Have you created your user in an unconventional way?

If you type ```
cat /etc/passwd
``` is your user`s path /bin/bash?

---

### Post by Dragon ELEMENTAL on 2010-01-21
Hiya,

I'm running /bin/bash (not sh) - I've checked.

I have been using this user for many months - this problem just randomly occurred a few weeks ago.

It's really annoying for me, as I read man pages a LOT

Thanx

---

### Post by nothingspecial on 2010-01-21
Well I`m stumped, if anything occurs to me though........

---

### Post by nothingspecial on 2010-01-21
The default .bashrc in /etc/skel is the same as yours
```

if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi
```

However mine just says

```
if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi
```

However, I`ve had my /home directory since 7.10 so something has obviously changed.

Do you have a seperate home and have you downgraded, say from 9.10 to 8.04 LTS

If I add the extra bit, and restart bash, tab completion still works, I`m just wondering weather this is true the other way.

Clutching at straws here.

---

### Post by oakgrove on 2010-01-31
Well I commented
 
```

if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

```
out in my .bashrc with hashes and now tab completion is working like it used to.

---

### Post by Dragon ELEMENTAL on 2010-01-31
Okay, I usually only restart about once every 1-2 months!, however have had to restart a lot in the past few days due to other things I've been doing, and this issue did not fix itself (I mean why would it?).  However, I just restarted my system again today and it's all working as it should for some stupid reason.

I'm really sorry about this, and still have no idea why it went funny.  I really appreciate all the replies.
I've always hated stumbling across a support thread only to follow it and read 'fixed after restarting' at the end - I guess I've just done that myself...

WOW

---

### Post by scottysb on 2011-06-09
If others are experiencing problems with auto-completion,
In the bash prompt, you can run "set -x" then attempt the auto-completion via <command> <TAB>.

This will show you the auto-completion commands that the shell is executing in your terminal.

Execute "set +x" to get the shell out of debug mode.

---

