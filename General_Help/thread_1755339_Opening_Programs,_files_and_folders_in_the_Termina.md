---
title: "Opening Programs, files and folders in the Terminal"
date: 2011-05-11
forum: General Help
---

### Post by Linux BASHer on 2011-05-11
I know I can call up a program from the terminal by typing its name. But how can I change the name corresponding to any particular program (to make it shorter, for instance)?

Also how would I go about opening specific files and folders in the GUI file manager or in a corresponding app (have an openoffice file open in openoffice from the terminal, or a folder open in the file manager from the terminal)?

---

### Post by lmarmisa on 2011-05-11
In relation to your first question, you can define an alias in the file $HOME/.bashrc . These are some examples:

```

alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

```

---

### Post by sweetleaf on 2011-05-11
As to your second question, many programs allow you to enter simply "programname filename". (For an overview, check "programname --help", and for more details, check "man programname".) If you're launching a GUI program this will tie up your terminal session until the GUI program exits, unless you launch as a background process: "programname filename &".

Hint 1: one way to "shorten" things is to use tab-completion: "progr<tab> filena<tab>".

Hint 2: if you don't know the name of your file manager, it's probably nautilus.

---

### Post by Linux BASHer on 2011-05-11
Thank you guys for the spot-on answers to what I needed.

---

