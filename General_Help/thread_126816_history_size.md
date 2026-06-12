---
title: "history size"
date: 2006-02-07
forum: General Help
---

### Post by denisesballs on 2006-02-07
How do I increase the amount of entries in my history? Usually it's setting HISTFILESIZE in ~/.bashrc, but there isn't a variale in there. Should I just include it, or is it stored somewhere else? Thanks.

---

### Post by dpm on 2006-02-07
I've just had a look at the usual bash config files on my system:[LIST]
[*][SIZE=3][COLOR=#000000]/etc/profile [/COLOR][/SIZE]
[*][SIZE=3][COLOR=#000000]/etc/bashrc [/COLOR][/SIZE]
[*][SIZE=3][COLOR=#000000]~/.bash_profile                                [/COLOR][/SIZE]
[*][SIZE=3][COLOR=#000000]~/.bashrc [/COLOR][/SIZE]
[*][SIZE=3][COLOR=#000000]~/.bash_logout[/COLOR][/SIZE][/LIST]and HISTFILESIZE is not defined there, although I can see it defined if I do an

```
echo $HISTFILESIZE
``` 
which defaults to the default value of 500 (see 'info bashref'). I'm guessing this shell variable is then defined by bash per default.

Anyway, you should safely be able to override the defaults by defining a new value for it in ~/.bashrc, I believe. It should not do any harm.

Cheers.

---

### Post by z_diver on 2006-02-07
I also had this quesiton so I tried adding HISTFILESIZE=600 to .bashrc and it didn't do it for me.  Is there anything else that would need to be done?

---

### Post by denisesballs on 2006-02-08
[QUOTE=z_diver]I also had this quesiton so I tried adding HISTFILESIZE=600 to .bashrc and it didn't do it for me.  Is there anything else that would need to be done?[/QUOTE]

Yeah that doesn't work. I can't believe no one knows how to do this?

---

### Post by kabus on 2006-02-08
I think you'll have to set $HISTSIZE too.
From man bash :


> When an interactive shell exits, the last $HISTSIZE lines are copied from the  history  list  to $HISTFILE.  If the histappend shell option is enabled (see the description of shopt under SHELL BUILTIN COMMANDS below),the lines are appended to the history file, otherwise the history file is overwritten.  
If HISTFILE is unset, or if  the history  file  is unwritable, the history is not saved.  After saving the history, the history file is truncated to contain no more than HISTFILESIZE lines.  If HISTFILESIZE is not set, no truncation is performed.

---

### Post by denisesballs on 2006-04-11
If anyone is curious, putting:

```
export HISTSIZE=1000
```

in /etc/profile will do it.

---

### Post by z_diver on 2006-04-11
[QUOTE=denisesballs]If anyone is curious, putting:

```
export HISTSIZE=1000
```

will do it.[/QUOTE]
I had to close that shell and open a new one to get it to take effect but then, yes, it did work.  Thanks for finding the thread and posting the answer.

---

### Post by dpm on 2006-04-12
[quote=denisesballs]If anyone is curious, putting:

```
export HISTSIZE=1000
``` 
will do it.[/quote]

Well, that will only work from the point you execute it onwards. Whenever you logout, you'll have to do the export again.

Or did you just add that line to your ~/.bashrc file?

---

### Post by denisesballs on 2006-04-12
[QUOTE=desp]Well, that will only work from the point you execute it onwards. Whenever you logout, you'll have to do the export again.

Or did you just add that line to your ~/.bashrc file?[/QUOTE]

I actually added it to /etc/profile .

---

