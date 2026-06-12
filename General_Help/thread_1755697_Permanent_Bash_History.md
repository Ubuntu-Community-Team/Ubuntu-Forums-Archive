---
title: "Permanent Bash History"
date: 2011-05-11
forum: General Help
---

### Post by supradave on 2011-05-11
Over time I've found the need to keep a more permanent record of my command line history.  I currently do it to a file but have found that that can get clobbered rather easily.  Therefore I'm looking to start to dump it into a database.  

Currently in .bashrc I have the following:
```
unset HISTTIMEFORMAT
PROMPT_COMMAND="${PROMPT_COMMAND:+$PROMPT_COMMAND ; }"'echo "$(history 1 | /usr/bin/cut -c8-)" >> $HOME/.bash_history.archive'
```

This dumps well into said file and then I process it at some point, i.e. remove duplicate commands because I only need ls and cd in there only once (or zero).

A little help on this structure to do something to the effect of:
```
sqlite bash_history.db 'insert or ignore into history values("$(history 1 | /cut -c8-)")'
```

Thanks

---

