---
title: "ViM. Howto autoindent and auto bracket."
date: 2010-11-15
forum: General Help
---

### Post by dragos240 on 2010-11-15
Hi,

How can I configure vim so that it simply auto-indents when I create a bracket '{' and on the next line creates an end bracket. This would help a lot when I'm programming.

Thanks.

---

### Post by x1a4 on 2010-11-16
Add the following to your ~/.vimrc file: 
```
set smartindent
set autoindent
```

To automatically append closing characters look [here]("http://vim.wikia.com/wiki/VimTip630")

---

