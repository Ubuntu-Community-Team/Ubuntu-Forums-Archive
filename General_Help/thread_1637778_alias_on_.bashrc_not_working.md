---
title: "alias on .bashrc not working"
date: 2010-12-04
forum: General Help
---

### Post by c2tarun on 2010-12-04
hi friends
i created this alias first

```

alias pro="cd /home/tarun/Documents/Programs"

```

and it worked

but when i created this alias
```

alias lucid="sudo chroot /var/chroot/lucid"

```
it is not working. why so ????

---

### Post by asmoore82 on 2010-12-04
Have you reloaded your Bash config since you added it?

---

### Post by c2tarun on 2010-12-04
> **asmoore82 said:**
> Have you reloaded your Bash config since you added it?


sorry i didn't reloaded it.
actually i dont know how to reload, :(
can you please tell

---

### Post by Habitual on 2010-12-04
alias reload='source ~/.bashrc' in your ~/.bashrc

Exit the terminal and restart, the next time you edit the .bashrc (after this).
just add your edits, save+exit then type reload. 

Done.

---

### Post by asmoore82 on 2010-12-04
You could also just close and reopen the terminal.

---

