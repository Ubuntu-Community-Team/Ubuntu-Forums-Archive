---
title: "Ubuntu not obeying editor for crontab"
date: 2010-11-03
forum: General Help
---

### Post by Calcipher on 2010-11-03
When I do run crontab -e as root (or any user) the crontab is open in Emacs.  I thought this was weird, so I ran ```
sudo update-alternatives --config editor
``` and found that vim was set as my default editor.  Printenv, on the other hand, has no environmental variable for editor, but running editor from a prompt does cause vim to run.  Why is crontab -e not obeying the editor choice?

---

### Post by efflandt on 2010-11-03
You can put one or both of the following in your ~/.bashrc (or /etc/bash.bashrc as default for all users) or whatever editor you want to use:

export EDITOR='nano'
export VISUAL='nano'

For some reason without the "export" it would work in console, but not in xterm.  Then close that xterm and open another. If you have both variables set, the result from the following should sound like Mork from Ork (Mork & Mindy).

efflandt@efflandt-XPS-8100:~$ **echo $EDITOR $VISUAL**
nano nano

---

### Post by Calcipher on 2010-11-03
> **efflandt said:**
> Mork from Ork (Mork & Mindy).

efflandt@efflandt-XPS-8100:~$ **echo $EDITOR $VISUAL**
nano nanoThis is probably one of the best replies I've ever gotten, thanks for the chuckle.  On the other hand I know that I can define these variables, but I'm a bit curious why the -e isn't obeying the default editor.

---

### Post by dcstar on 2010-11-04
> **Calcipher said:**
> When I do run crontab -e as root (or any user) the crontab is open in Emacs.  I thought this was weird, so I ran ```
sudo update-alternatives --config editor
``` and found that vim was set as my default editor.  Printenv, on the other hand, has no environmental variable for editor, but running editor from a prompt does cause vim to run.  Why is crontab -e not obeying the editor choice?

Look in the following file: **~.selected_editor**

---

### Post by Calcipher on 2010-11-04
> **dcstar said:**
> Look in the following file: **~.selected_editor**
That got it.  Thank you very much!

---

