---
title: "How to make LaTeX find style files?"
date: 2010-05-05
forum: General Help
---

### Post by Bromskloss on 2010-05-05
I have a documentclass for LaTeX that I need to use. Where should I put those files (e.g., ".cls" and ".sty") so that LaTeX can find them and should I run some update command after that? A solution that does not require superuser rights is preferable. Thanks in advance!

---

### Post by dino99 on 2010-05-05
[http://www.ubuntugeek.com/gummi-simple-latex-editor-written-in-pythongtk.html](http://www.ubuntugeek.com/gummi-simple-latex-editor-written-in-pythongtk.html)

you may need to search "latex" into synaptic

---

### Post by Bromskloss on 2010-05-05
> **dino99 said:**
> [http://www.ubuntugeek.com/gummi-simple-latex-editor-written-in-pythongtk.html](http://www.ubuntugeek.com/gummi-simple-latex-editor-written-in-pythongtk.html)

you may need to search "latex" into synaptic

I think there must be some misunderstanding here. What you linked to looks like a text editor tailored for writing LaTeX files, right? I'm already writing my LaTeX files in Emacs, I just want to know where I should put this custom documentclass I must use so that LaTeX finds it.

---

### Post by tacutu on 2010-05-05
the files can be placed either in the current directory or in ~/texmf

AFAIK, you don't need to update anything, latex should just find them in ~/texmf. Hope this helps

---

### Post by Bromskloss on 2010-05-05
> **tacutu said:**
> the files can be placed either in the current directory or in ~/texmf

AFAIK, you don't need to update anything, latex should just find them in ~/texmf. Hope this helps

Thank you! That seems to work, at least as far as I can see by just glancing at it.

---

