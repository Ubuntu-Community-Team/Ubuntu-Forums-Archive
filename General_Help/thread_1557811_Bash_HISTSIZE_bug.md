---
title: "Bash HISTSIZE bug?"
date: 2010-08-21
forum: General Help
---

### Post by qiet72 on 2010-08-21
Hi,

Since upgrading to Lucid Lynx, I have found out that my .bash_history gets truncated to 2000 lines where before I had over 50000 lines.

I have the following two lines in my .bashrc file:

export HISTSIZE=100000
export HISTFILESIZE=100000

This used to work fine in previous versions of Ubuntu.  Has there been a change in bash so HISTSIZE has a limit of 2000 lines?

I have tried googling but there are only examples where they include "HISTSIZE=2000".

qiet72

---

