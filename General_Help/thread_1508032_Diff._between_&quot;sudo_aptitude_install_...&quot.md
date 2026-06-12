---
title: "Diff. between &quot;sudo aptitude install ...&quot; and &quot;sudo apt-get install ...&quot;?"
date: 2010-06-12
forum: General Help
---

### Post by pstein on 2010-06-12
Sorry for the newbie question but what is the difference between the two commands:
 
"sudo aptitude install ..." 
and
"sudo apt-get install ..."
 
Are they the same?
 
Can I install a *.bin file which is already on the local computer as well with such an
apt(itude) command?
 
Or does apt already access a remote repository?
 
Peter

---

### Post by Smart Viking on 2010-06-12
Hi, no they are not the same, but you wont notice the difference.

Before they where a little different, then you used "apt-get" for some things and "aptitude" for other things, but now "apt-get" does basically all that "aptitude" did. Thats also for that reason that aptitude will get removed from ubuntu 10.10, it is more and more a waste of diskspace, but it will be available in the repository.

I hope this helped. :)

---

### Post by dino99 on 2010-06-12
apt-get & aptitude are very closed, use one or the other as you like but not both as they built index in a different way, you dont have to install .bin directly.

more info below

---

### Post by elliotn on 2010-06-12
When I had 20 broken parkages, I tried apt-get install -f it never worked
But aptitute install fixed the parkages even thou I had no net

---

### Post by prodigy_ on 2010-06-12
**aptitude** is still superior to **apt-get**. For example, one can use it interactively.

---

### Post by pstein on 2010-06-14
> **prodigy_ said:**
> **aptitude** is still superior to **apt-get**. For example, one can use it interactively.
 
So why not abolish apt-get and use ALWAYS aptitude?

---

