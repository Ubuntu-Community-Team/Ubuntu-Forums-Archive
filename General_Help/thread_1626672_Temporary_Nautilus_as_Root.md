---
title: "Temporary Nautilus as Root"
date: 2010-11-20
forum: General Help
---

### Post by pennstatebadboy on 2010-11-20
From time to time, I need to modify files in a directory that requires root permissions. The way I do it is to open nautilus from a terminal using the sudo command, then navigate to the folder that I need to modify. This works, but it's clunky, tedious, and seems like a lot of work to perform what is often a simple task.

I can't be the only one who finds this annoying. Has anyone devised a way to solution that prompts you for your password to temporarily allow root permissions to modify files? I'm envisioning this happening instead of the "Error permission denied" window that pops up.

Thanks.

---

### Post by mc4man on 2010-11-20
Myself just use nautilus-gksu - r. click on a file or dir. -> Open as administrator

sudo apt-get install nautilus-gksu
or search in your preferred package manager

---

### Post by aysiu on 2010-11-20
I just create a keyboard shortcut for the command ```
gksudo nautilus
```

---

### Post by randumnumber on 2010-11-20
^^^^ thats about right, and you can make a shortcut on your toolbar that calls the gksudo nautilus.

---

### Post by pennstatebadboy on 2010-11-20
Creating a shortcut eliminates one step (opening a terminal), but you still need to to re-navigate to the directory you want to modify.

---

### Post by Ancanus on 2010-11-20
> **mc4man said:**
> Myself just use nautilus-gksu - r. click on a file or dir. -> Open as administrator

sudo apt-get install nautilus-gksu
or search in your preferred package manager

@pennstatebadboy:

Did you try mc4man's solution?

---

### Post by stinkeye on 2010-11-20
Already been said.

---

### Post by pennstatebadboy on 2010-11-20
Great! I thought -gksu was just an argument for opening Nautilus from a terminal, but now I see that it does exactly what I'm looking for.

Thanks!

---

### Post by oldfred on 2010-11-20
I just right click on file and Open with Other Application. Then click on use custom application and enter gksudo gedit. Next time it will be in the list of apps to open files with.

---

