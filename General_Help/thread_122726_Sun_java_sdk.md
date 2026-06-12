---
title: "Sun java sdk"
date: 2006-01-28
forum: General Help
---

### Post by flyingfrog on 2006-01-28
Hi everybody!
I'm having some issues installing the sun java sdk 1.5.

That's not all real, i'm using ubuntu 5.10, and after the main installation i had the GNU virtual machine installed... I don't know the name but it's the one with gij/gcj .

Now, i don't want this, i just want sun-j2sdk1.5. So I installed it through synaptic. 
But now, typing java -version gives me:
```
barto@PortatileUbuntu:~ $ java -version
java version "1.4.2"
gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)

Copyright (C) 2005 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```.

Trying to uninstall gij or gcj doesn't seem to be the bast way, 'cause it forces me to uninstall every java-based application, even OpenOffice!!

How can I enable sun jdk and disable gij??

Thanx

---

### Post by nikosft on 2006-01-28
run

sudo update-alternatives --config java

and choose which virtual machine to use

---

### Post by flyingfrog on 2006-01-28
Great!!

Just two more little questions.
a) Changes are permanent?
b) I can move only the * symbol, while it keeps a + symbol on the previous alternative, what does that mean?

By the way, thanks again for the reply!!!!

---

### Post by nikosft on 2006-01-28
For me at leat the changes were permanent. I do not really know what these sympols mean, may be somebody else with grater experience may help us!

---

