---
title: "Terminal Experts?"
date: 2009-11-12
forum: General Help
---

### Post by MikeVaughanG on 2009-11-12
Is there a way to make terminal open to a specific location by Default?

---

### Post by samuelhug on 2009-11-12
Add "cd <specific location>" (without quotes) to your ~/.bashrc file

---

### Post by tuwe on 2009-11-12
You could put the following code at the end of your ~/.bashrc.

```
MYDIR=/the/directory/you/want/to/go/to
test -d $MYDIR && cd $MYDIR
```

In the first line you specify the location, the second line checks if the location exists and changes to it.
If the location doesn't exist, nothing happens.

edit: @samuelhug: hey you're stealing my answers! :)

---

### Post by issih on 2009-11-12
Both the above are quite correct, but will affect every terminal you create, so that your default directory is no longer your home directory.

Alternatively launching a terminal with the command:

```
gnome-terminal --working-directory=DIRNAME
```

should do what you want for one specific terminal, whilst leaving the defaults alone.

You could have a specific launcher if its something you need regularly.

---

### Post by oldos2er on 2009-11-12
> **MikeVaughanG said:**
> Is there a way to make terminal open to a specific location by Default?

 The package nautilus-open-terminal allows you to open a terminal from the right-click menu, in any folder you happen to be viewing in Nautilus.

---

### Post by MikeVaughanG on 2009-11-12
Someone posted about making a specific launcher fro this. This seems like the best idea. 

I made a launcher but im not quite sure how to get it to work right?

gnome-terminal /home/mike2/Desktop/Scripts=DIRNAME

That doesnt work..

---

### Post by DaithiF on 2009-11-12
you need it this way around:
```
gnome-terminal --working-directory=/home/mike2/Desktop/Scripts

```

---

### Post by tuwe on 2009-11-12
> **MikeVaughanG said:**
> Someone posted about making a specific launcher fro this. This seems like the best idea. 

I made a launcher but im not quite sure how to get it to work right?

gnome-terminal /home/mike2/Desktop/Scripts=DIRNAME

That doesnt work..

gnome-terminal --working-directory=/home/mike2/Desktop/Scripts

i totally forgot about that one.

edit: today i'm always too late.

---

### Post by MikeVaughanG on 2009-11-12
> **DaithiF said:**
> you need it this way around:
```
gnome-terminal --working-directory=/home/mike2/Desktop/Scripts

```

Thank Yiu, That worked Like A charm

And thanks anyway Tuwe. lol. :)

---

