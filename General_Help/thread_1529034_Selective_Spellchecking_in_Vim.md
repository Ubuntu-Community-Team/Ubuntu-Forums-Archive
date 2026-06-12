---
title: "Selective Spellchecking in Vim"
date: 2010-07-11
forum: General Help
---

### Post by Birion on 2010-07-11
Is there a way to automatically enable or disable spellchecking in vim depending on the filetype? I often work with tex files (with lots of text) where the spellchecking is useful, and scripts and conf files where spellchecking often marks variables and functions (which are often in red or similar colour), making them unreadable (red text on red background).

---

### Post by RHTopics on 2010-07-11
You can use the autocmd feature in Vim to have selective spell checking based on file type.  The autocmd is placed in the .vimrc file in your home directory.

Here is an example for having files ending in .txt to have spell checking turned on:

```
autocmd BufNewFile,BufRead *.txt setlocal spell

```

---

### Post by Birion on 2010-07-11
Yep, that works great. Thanks.

---

### Post by RHTopics on 2010-07-11
You are welcome.  I am glad it worked for you.

---

