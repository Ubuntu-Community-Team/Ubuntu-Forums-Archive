---
title: "ugly root programs"
date: 2006-06-04
forum: General Help
---

### Post by jworr on 2006-06-04
any program I run in fluxbox with root privledges tooks ugly like a gtk 1 app.  Does anyone know how to fix this?

---

### Post by viciouslime on 2006-06-04
Copy your .themes folder from your home directory to /usr/share/themes :)

EDIT: Just realised, you said fluxbox. I'm not sure how fluxbox works exactly as I have never used it... above might be worth a try though

---

### Post by jworr on 2006-06-04
Thanks for the help but that didn't work

---

### Post by garba on 2006-06-04
[QUOTE=jworr]any program I run in fluxbox with root privledges tooks ugly like a gtk 1 app.  Does anyone know how to fix this?[/QUOTE]

move your personal preferences over to /root, that should help, hopefully

---

### Post by zikki on 2006-06-04
Check this link
[http://www.ubuntuforums.org/showpost.php?p=848985&postcount=1](http://www.ubuntuforums.org/showpost.php?p=848985&postcount=1)
It will solve the problem.

---

### Post by jworr on 2006-06-05
I followed the guide but it doesn't seem to work with fluxbox

---

### Post by blackjack6.21.91 on 2006-06-05
You've got to link your plugins folder for your account to the one for your root account.  I dont think many of us use fluxbox so it's up to you to find where they are..:(

---

### Post by Ramses de Norre on 2006-06-05
It doesn't matter whether your using fluxbox, the themes are drawn by gtk.
Do ```
sudo ln -s ~/.icons /root/.icons && sudo ln -s ~/.themes /root/.themes && sudo ln -s ~/.fonts /root/.fonts
```
Works on fluxbox here.

---

### Post by jworr on 2006-06-05
I tried these commands

sudo ln -s ~/.icons /root/.icons && sudo ln -s ~/.themes /root/.themes && sudo ln -s ~/.fonts /root/.fonts


but it doesn't change anything

---

