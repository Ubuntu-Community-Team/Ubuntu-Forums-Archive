---
title: "How do I install alias?"
date: 2010-06-14
forum: General Help
---

### Post by hreichgott on 2010-06-14
I would like to create some aliases for bash shell.

On other Unix/Linux machines I have done this using the alias command like this:

alias rm rm -i

When I type that into a terminal on Ubuntu, it looks like alias is not installed.  I get this:

bash: alias: rm: not found
bash: alias: rm: not found
bash: alias: -i: not found

I tried adding the alias to .bashrc instead, but then I get the same error message every time I start terminal.

Just for fun I tried apt-get install alias, just to see what would happen, and it installed something called libperl-alias instead, and alias still doesn't work.

How do I install alias?

thanks

---

### Post by CharlesA on 2010-06-14
Try this:

alias rm='rm -i'

This is what my alias(es) look like:

```
alias egrep='egrep --color=auto'
alias fgrep='fgrep --color=auto'
alias grep='grep --color=auto'
alias l='ls -CF'
alias la='ls -A'
alias ll='ls -alF'
alias ls='ls --color=auto'

```

---

### Post by hreichgott on 2010-08-20
Hi CharlesA,
Aha! The apostrophes made it work.
Thanks!

---

