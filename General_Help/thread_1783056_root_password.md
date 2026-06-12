---
title: "root password?"
date: 2011-06-15
forum: General Help
---

### Post by zzdjchris on 2011-06-15
I am not a total noob, but I must admit, I don't know a lot about Ubuntu, or rather one particular part which me saying kinda embarrasses me.
I've notice that since the release of 10.04 LTS that it's not so easy to be a "Super User", or even to set the "root Password" any more. 

How do I do this now, the latter being the more important? I'd like to be able to set the root password again.

Any help please?

DeeJ.

---

### Post by hakermania on 2011-06-15
Well, in a terminal, give
```
sudo su
```
Give your account's login password and then, after you become root, give
```
passwd
```
if you haven't set a root password this will prompt immediately for new root password, if you have set one, you have to retype the old one to let you set a new one.

---

### Post by Dave_L on 2011-06-15
It's explained here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zzdjchris on 2011-06-15
Thanks Heaps [hakermania]("http://ubuntuforums.org/member.php?u=895189"). You taught me a new, and necessary thing THAT WORKED!!!
Thanks A LOT!

---

