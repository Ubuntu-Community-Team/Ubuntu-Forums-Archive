---
title: "How to remove all software not list in Ubuntu Software Center?"
date: 2011-11-24
forum: General Help
---

### Post by tctvn on 2011-11-24
how to remove all software not list in Ubuntu Software Center? :guitar:
My english is not good :(

---

### Post by raja.genupula on 2011-11-24
Hi man , i am unable to get your question .

do you want to remove installed pkg's or anything else ?

---

### Post by salemhouda on 2011-11-24
So it not easy to do this.
So try to write a script that search all installed softwares and verify if it's in ubuntu software center
[code]$dpkg --list
[\code]

---

### Post by raja.genupula on 2011-11-24
Now got the question but why you wanna do this ? 

because dependencies of a pkg is not going to list in software center ,  you should get them from synaptic . 

so dont do that man.

---

### Post by whoop on 2011-11-24
Maybe you want to run the computer janitor application?

---

### Post by MG&amp;TL on 2011-11-24
```
dpkg --get-selections
```

will return a list of packages you _can_ (but exercise caution, nobody's going to help if you remove the kernel):


```
apt-get remove
```

Or, alternatively, you can
```
sudo apt-get install synaptic
```

Which will install a GUI package manager.

---

### Post by tctvn on 2011-11-24
Thank you

 Do I usually try to install applications from different sources form the internet!

 The software is installed from the Ubuntu Software Center is easy to find and remove it! But the software installation manual (eg pcsxr, Stepmania,...) is not easy to find it

---

