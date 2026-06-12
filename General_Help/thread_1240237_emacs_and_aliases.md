---
title: "emacs and aliases"
date: 2009-08-14
forum: General Help
---

### Post by Qvintvs on 2009-08-14
I currently have emacs aliased as 'emacs -nw' in my .zshrc file, but I want to have another command, say, emax, that will run emacs in windowed mode. I tried this: 
```

alias emax='emacs'
alias emacs='emacs -nw'

```
but running emax still runs in -nw mode. is there a way to have the first alias definition not expand 'emacs' to 'emacs -nw', or any other way to get the desired effect?

---

### Post by DaithiF on 2009-08-14
Hi,
yes there is.  \command runs the unaliased version of a command, so make your emax alias equal to:
alias emax="\emacs"
and that should work

cheers
d

---

