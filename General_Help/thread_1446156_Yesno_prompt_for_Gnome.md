---
title: "Yes/no prompt for Gnome"
date: 2010-04-03
forum: General Help
---

### Post by patman0623 on 2010-04-03
I am creating a bash script file, and I want to know if there is a yes/no command for Gnome? Specifically, if I accidentally click the batch file, I want it to prompt me first. I a clutch I could use gksudo, but that's really not what I'm looking for.

---

### Post by dcstar on 2010-04-03
> **patman0623 said:**
> I am creating a bash script file, and I want to know if there is a yes/no command for Gnome? Specifically, if I accidentally click the batch file, I want it to prompt me first. I a clutch I could use gksudo, but that's really not what I'm looking for.
```

man zenity
```

---

### Post by kblft on 2010-04-03
you can do 

```
zenity --question --text "Are you sure?"
```

or 

```
zenity --warning --text "Are you sure?"
```

it will basically return a zero exit code (e.g $? ) if you press OK

---

