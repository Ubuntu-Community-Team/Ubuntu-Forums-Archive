---
title: "change default editor for crontab"
date: 2010-10-29
forum: General Help
---

### Post by vinay nadig on 2010-10-29
hi, i wanted to schedule some backup scripts so used crontab -e option
it gave me 5 editors to choose from
the editor i am used to is vim but i accidently pressed the wrong key and the crontab file was opened in nano.. :(
the problem is that now every time i give the crontab -e command, it directly takes me to the nano editor.
can anyone tell me how to reset it so that i get the option to choose the editor??
or to set the default editor for crontab as vim??
thanx in advance..  :)

---

### Post by sisco311 on 2010-10-29
```
sudo select-editor
```
or to select the default editor only for your user:
```
select-editor
```

---

### Post by vinay nadig on 2010-10-29
thnx a bunch. worked like a charm.. :D
cheers!

---

