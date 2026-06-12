---
title: "Better Zsh history?"
date: 2012-07-14
forum: General Help
---

### Post by Argenteus on 2012-07-14
A while back, I installed Zsh and set it to be used instead of bash. Even with my minimal, newbish config it seems far better than what came with bash. But the one thing I miss from bash is some features of it's history function. I like Zsh's dynamic history to where I can fill out part of the command to filter history, but in Zsh the history is cleared when I close the terminal. I want the history to remain even after closing the terminal like in bash. Any help? Thanks.

---

### Post by sisco311 on 2012-07-14
[http://zsh.sourceforge.net/Guide/zshguide02.html#l17](http://zsh.sourceforge.net/Guide/zshguide02.html#l17)

This is what I have in my ~/.zshrc file:
```

# Keep 1000 lines of history within the shell and save it to ~/.zsh_history:
HISTSIZE=1000
SAVEHIST=1000
HISTFILE=~/.zsh_history

```

---

### Post by codemaniac on 2012-07-14
Add something like below to ~/.zshrc to enable shell history in zsh (Create it if it doesn't already exist).

```

# number of lines kept in history
export HISTSIZE=1000
# number of lines saved in the history after logout
export SAVEHIST=1000
# location of history
export HISTFILE=~/.zhistory
# append command to history file once executed
setopt inc_append_history
```

---

### Post by Argenteus on 2012-07-14
Thanks for the help.

---

