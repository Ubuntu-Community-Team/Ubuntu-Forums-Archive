---
title: "Trying to delete directory"
date: 2010-03-16
forum: General Help
---

### Post by junderbr on 2010-03-16
I removed a user account from my installation of 9.10 however that does not remove the users home directory, which I also want to do.  I emptied the directory as as best I can tell, that is  *ls* returns nothing in the directory.  However when I run 

sudo rmdir joseph

I get

rmdir: failed to remove `joseph': Directory not empty

What do I need to do to get this directory deleted?

---

### Post by n0dix on 2010-03-16
Did you try with ls -la to see if it is really empty?
Also to delete the directory you can do:
```
rm -r joseph
```
or
```
 rm -rf joseph
```

---

### Post by wojox on 2010-03-16
Try:

```
sudo rm -rf /joseph
```

From the terminal in /home

---

### Post by blur xc on 2010-03-16
> **n0dix said:**
> Did you try with ls -la to see if it is really empty?
Also to delete the directory you can do:
```
rm -r joseph
```or
```
 rm -rf joseph
```

In this instance it probably doesn't matter, but if your are entering a longer path after rm -r or worse, rm -rf and accidentally hit enter before you are done entering your path, you could hose your system.  It's safer to enter "rm /your/long/path -rf" so if you hit enter on accident earlier, nothing happens since it can't remove directories w/o the -r option.

BM

---

### Post by blur xc on 2010-03-16
> **wojox said:**
> Try:

```
sudo rm -rf /joseph
```From the terminal in /home

You probably mean

```
sudo rm /home/joseph -rf
```

Case in point, say your entered "sudo rm -rf /home<enter on accident>"

It'd make for a bad day...

BM

---

### Post by junderbr on 2010-03-16
Thanks!  Problem solved.

---

### Post by n0dix on 2010-03-16
@blur xc, I know the risk but the user have to be careful of what is doing. 
Btw, thanks for the tip. I didn't know that.

---

### Post by blur xc on 2010-03-16
> **n0dix said:**
> I know the risk but the user have to be careful of what is doing. 
Btw, thanks for the tip. I didn't know that.

I don't forget this one, because I'm a notorious for accidentally hitting enter...

BM

---

### Post by n0dix on 2010-03-16
> **blur xc said:**
> I don't forget this one, because I'm a notorious for accidentally hitting enter...

BM

Yes, i thought you had a serious problem with this, that's why you are so careful. Thanks again for the tip. First time i read this.

---

