---
title: "nautilus file manager how to ignore files (e.g. *.pyc)"
date: 2011-04-16
forum: General Help
---

### Post by giuspen on 2011-04-16
Hi,
I would like to have Nautilus not display the *.pyc files, is there a way to obtain this result?
Cheers.

---

### Post by TeoBigusGeekus on 2011-04-16
Try this:
Create a file in the directory where your files (*.pyc) are located.
Name it .hidden
Open it with a text editor and add this line
```
*.pyc
```
Open a terminal
```
killall nautilus
```
to stop nautilus (it will be restarted automatically).
Post back with results.

---

### Post by WorMzy on 2011-04-16
The only way I know of is to manually add the name of every .pyc file to the .hidden text file (if you don't have one, you can create one).

e.g. Create ~/.hidden, and enter the following
```
Documents
Music
```

Save the file, refresh nautilus, and the Documents and Music folders should now be hidden (press Ctrl+H to see them). Edit/remove .hidden to make them visible by default again.

Unfortunately, this isn't a very ideal solution since .hidden doesn't accept wildcards.

---

### Post by TeoBigusGeekus on 2011-04-16
> **WorMzy said:**
> 
Unfortunately, this isn't a very ideal solution since .hidden doesn't accept wildcards.

Didn't know that, thanks.

---

### Post by giuspen on 2011-04-17
> **WorMzy said:**
> The only way I know of is to manually add the name of every .pyc file to the .hidden text file (if you don't have one, you can create one).

e.g. Create ~/.hidden, and enter the following
```
Documents
Music
```

Save the file, refresh nautilus, and the Documents and Music folders should now be hidden (press Ctrl+H to see them). Edit/remove .hidden to make them visible by default again.

Unfortunately, this isn't a very ideal solution since .hidden doesn't accept wildcards.

That made it, thanks.
Sad that wildcards do not work.

---

