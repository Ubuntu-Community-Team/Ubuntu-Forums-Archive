---
title: "just installed, couldn't find vim"
date: 2012-05-29
forum: General Help
---

### Post by marinara on 2012-05-29
I just installed 12.04 lubuntu.  I had a stupid little thing, here it is:

(a fresh install.) I needed to edit a text file, so I started a terminal, typed vim.  It didn't work (vim: command not found) .  It suggested a list of packages I could install for vim.

later I figured out, vim-tiny was installed.  I just wasn't typing that. Am I stupid?

is this a bug?  where would i report it?

TIA

---

### Post by Gyokuro on 2012-05-29
Vim on a fresh install is only a symlink to vi; do get vim you have to install either vim or vim-tiny

sudo apt-get search vim shows  them

afterwards you get your favourite editor. Vim rules :-) emacs

---

