---
title: "CD permissions"
date: 2010-01-08
forum: General Help
---

### Post by Cardale on 2010-01-08
I was trying to use some of the labs in a java book that I bought you might know of it _Objects First with Java A Practical Introduction to using BlueJ_ I was trying to copy the projects off the cd and it wont allow me to do this.  I get an error permission denied.  I ended up using the terminal to copy the files over and then changing the permissions once they were copied over, but I wanted to know is how can I give my default user complete permission in Nautilus to copy these files over?  I opened Nautilus in root and it still wouldn't let me copy files over so this isn't a solution.

---

### Post by Lars Noodén on 2010-01-08
> **Cardale said:**
> ... I opened Nautilus in root

That is almost guaranteed to cause very big trouble.  

Where you able to see the contents of the CD at all with Nautilus?
Did you use Nautilus to *copy* or try to transfer the files from the CD?

---

### Post by Cardale on 2010-01-08
I was able to see all the files and they didn't have that little lock symbol on it either, but I just couldn't copy it over to my hard disc.

Opening natilus  with gksudo is bad?

---

### Post by Lars Noodén on 2010-01-08
> **Cardale said:**
> I was able to see all the files and they didn't have that little lock symbol on it either, but I just couldn't copy it over to my hard disc.

It may be trying to move, not copy, the files.  

> **Cardale said:**
> 
Opening natilus  with gksudo is bad?

Not necessarily bad or good, just fairly dangerous.  gksudo lets you run as root.  As root you have no helmet, no seat belt, no goggle, etc. and the programs still do exactly as you tell them to do, not what you think you tell them to do.  Best if it is reserved for rare occasions.

---

