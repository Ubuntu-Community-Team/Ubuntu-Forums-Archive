---
title: "Query: history -c in bash shell."
date: 2012-02-11
forum: General Help
---

### Post by garyjmellor on 2012-02-11
Hi, I'm currently reading a book on the Linux command line. One of the commands it uses is history -c which, according to the description, clears the history of command issued in the shell for the current user. The history activity is recorded in a file (.bash_history) in the user's home directory. I'm seeing some strange results with this so I want to understand if it is me not quite grasping something or if there is an issue.

When I issue history -c it does appear to clear my history in the session - I can no longer use the up and down arrows to browse through my past commands. However if I gedit .bash_history in the same session I can still see all the commands I issued. I thought maybe the clearing down of the .bash_history file perhaps doesn't get done until a logout and login but this proved not to be the case. When I logged back in I could immediately start using the up and down arrow keys to peruse the history of the commands I thought I'd just cleared down.

I'm wondering whether this is a security thing since .bash_history is effectively a default keylogger. If I were (not very sensibly) to type in a plain text password in the shell, someone could theoretically just peruse my bash history file (albeit again I would be foolish to have left my machine unlocked and unattended for them to do so).

So my question is: should history -c actually remove the contents of the .bash_history file completely (obviously until the user starts issuing commands at the prompt again) or did I misunderstand something?

For reference I'm using 11.10.

Thanks in advance.

---

### Post by Paddy Landau on 2012-02-12
I am getting the same results as you. The manual clearly states that -c clears the history, so I am also puzzled.

However, you can simply delete the file .bash_history. That will do it!

---

### Post by yabbadabbadont on 2012-02-12
If you would like to completely disable the saving of bash commands, you can add ```
unset HISTFILE
``` to your ~/.bashrc

You'll need to close the terminal window, then open a new one and delete the .bash_history file after you add that by the way.

---

### Post by garyjmellor on 2012-02-12
Thanks for the replies guys. I don't want to disable the history feature as it's very useful but I would like history -c to work how the manual (and my book) states it should. Is this a bug (seems like it is to me). If it is then I will raise it via Launchpad. Thanks for your input once again.

---

### Post by Khayyam on 2012-02-12
garryjmellor ...

The confusion is over what is understood by 'history', history is not the $HISTFILE.

The history that 'history -c' clears is the shells active history, this is why up/down keys nolonger do anything, because there is no history there to navigate. It doesn't remove .bash_history, just clears the 'array' that hold the contents of history.

```
% echo -n $SHELL ; echo '  YAY!'
/bin/zsh  YAY!
% bash -i
$ echo "hello bash"
hello bash
$ history
    1  echo "hello bash"
    2  history 
$ history -c
$ history
    1  history
$ cat .bash_history
$ exit
% bash -i
$ history
    1  history
    2  cat .bash_history
    3  exit
    4  history
$ exit
% bash -i
$ history -c
$ exit
% bash -i
$ history
    1  history
    2  cat .bash_history
    3  exit
    4  history
    5  exit
    6  exit
    7  history
```

So, the history for that session up to the 'history -c' is cleared (and not written to .bash_history) but the subsequent history (and the history written to .bash_history from prior serssions) remains. 'history -c' is just a way of clearing the array, and whatever is cleared nolonger ends up in $HISTFILE.

HTH ... khay

---

### Post by garyjmellor on 2012-02-12
Thanks for that Khayyam - that's a perfect explanation! :D

---

### Post by Khayyam on 2012-02-13
> **garyjmellor said:**
> Thanks for that Khayyam - that's a perfect explanation!

Your welcome ...

For me history is one of the most useful features of interactive shells. I have 'hist_ignore_space' set (in zsh) and so any command prefaced with a space doesn't end up in my history file. This means that I can selectively input to $HISTFILE and not clutter it up with commands I'm not likely to use in future. 

Once you're used to prefacing commands with space $HISTFILE becomes like a notepad, or repository, of useful oneliners.

With zsh's 'print -z' I also store commands in $HISTFILE I've never run (but have copied from various sources) to be used at a later date. With 'HISTSIZE=4000' I've yet to have anything be removed (I also edit $HISTFILE every now-and-again), and so I have a whole arsenal of oneliners, dating back years, at my disposal.

I use an alias for grepping $HISTFILE, use alt-p, alt-n, alt-r, and !{n} for recalling commands .. and save alot of typing!

Also, aliases can be prefaced with a space (eg: alias ls=' ls -FG $@') so they don't end up in history (if you have them aliased it doesn't make sense to also have them in $HISTFILE also).

I keep a copy of ${HISTFILE}.${HOSTNAME} for every account/host I have access to, and sync them every so often to various account/hosts. This means I can have access to these $HISTFILE's simply my changing the $HISTFILE variable. This may not sound useful, but when administrating many machines it has often saved me alot of time.

So, when you write history "is effectively a default keylogger", I have to say .. sorta ... yes ... but unlike a keylogger it doesn't log passphrases, it logs commands, and I'm more than happy to share these with any prying eyes. Should someone gain access to them they are not getting anything more than they might find posted on the internet, and it won't give up too many clues as to my activity as most commands issued are not in the $HISTFILE.

I've read that to gain a similar feature to 'hist_ignore_space' using bash you can add the following to your ~/.bash_profile (untested)

```
export HISTCONTROL=ignoreboth
```

So, some idea of how I use history, hopefully you find something useful there.

best ... khay

---

### Post by garyjmellor on 2012-02-13
Thank you, that's really helpful :)

---

