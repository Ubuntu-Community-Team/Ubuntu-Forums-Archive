---
title: "Doubt in Vim text editor"
date: 2010-12-01
forum: General Help
---

### Post by srinivasan1691 on 2010-12-01
I am not accustomed to the new VIM editor of ubuntu so could anyone help me out in how should i able to enter the text into the editor.... in earlier version 'i' key was pressed for input mode....here to 'i' is used to enter but when i click backspace i feel that it does not erase.. but navigates left what should i do now ?

---

### Post by lykeion on 2010-12-01
The backspace problem can be solved by either
a) creating the empty file ~/.vimrc

or
b) install vim-full package```
sudo apt-get install vim-full
```

---

### Post by WorMzy on 2010-12-01
Yes, if you don't have a .vimrc file vim will run in compatible mode, which makes it behave like Vi. Run vimtutor for a rather nice tutorial on how to use vim and enable some of it's features.

---

