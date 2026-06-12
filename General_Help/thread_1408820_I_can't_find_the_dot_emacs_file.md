---
title: "I can't find the dot emacs file"
date: 2010-02-16
forum: General Help
---

### Post by AmadeusOK on 2010-02-16
With the command "ls -a" inside home I can find a subdirectory called ".emacs.d" which only contains one file "auto-save-list". But the ".emacs" file cannot be found anywhere. Do I need to keep searching for it or should I just go ahead and create one? Why is not in the home directory by default? Thanks for your answers.

---

### Post by 199DMF on 2010-02-16
. in front of a file means its hidden, in nautilus there should be a view button to show hidden folders

---

### Post by baddog144 on 2010-02-16
If you can't see a .emacs when you do `ls -a` in your home directory, then you can go ahead and create one and use that :)

---

### Post by jpkotta on 2010-02-17
If you would rather keep all of your emacs related files in ~/.emacs.d, don't create ~/.emacs and create ~/.emacs.d/init.el instead.

---

### Post by AmadeusOK on 2010-02-17
> **jpkotta said:**
> If you would rather keep all of your emacs related files in ~/.emacs.d, don't create ~/.emacs and create ~/.emacs.d/init.el instead.

That's what I did, I created the file "~/.emacs.d/init.el". I need it to activate the recently installed AUCTeX. Thanks a lot for your help.

---

