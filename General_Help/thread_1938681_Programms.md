---
title: "Programms????"
date: 2012-03-10
forum: General Help
---

### Post by EpicWorld on 2012-03-10
Weeeeeee so after re-installing windows several times because of a virus i needed to reinstall wubi, now the problem is that i cannot install any programs it always says that <<Installing packages failed>> or something like that so I cannot see any flash content plus I cannot run Java, Wine, PlayOnLinux and many others :(

I tried reinstalling the programs + also reinstalled the OS 3 times D:

Help me please :(

---

### Post by codemaniac on 2012-03-10
Can you please post the exact error messages you are getting while you install packages ?

---

### Post by EpicWorld on 2012-03-10
> **codemaniac said:**
> Can you please post the exact error messages you are getting while you install packages ?

[http://i40.tinypic.com/2hpt668.png](http://i40.tinypic.com/2hpt668.png)

Hope you understand what it says, it is in romanian :/

---

### Post by codemaniac on 2012-03-10
seems like libw* packages are not selected while you are installing PlayOnlinux .Had you done a 
```
sudo apt-get update ; sudo apt-get install playonlinux
```

Ubuntu comes with a default set of packages installed and the package manager track those packages. If you remove a package that is installed by default, it becomes marked as "deselected". This means it was installed previously, but has been removed. In fact any package that you install and then remove becomes marked as "deselected".

---

### Post by EpicWorld on 2012-03-10
I updated everything and it works now, thanks mate :D

---

### Post by codemaniac on 2012-03-10
> **EpicWorld said:**
> I updated everything and it works now, thanks mate :D

wow , good to hear that .In the meantime i have also learnt some bits of Romanian .
popcorn for you .:popcorn:

---

