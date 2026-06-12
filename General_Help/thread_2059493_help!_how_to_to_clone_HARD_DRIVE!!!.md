---
title: "help! how to to clone HARD DRIVE!!!"
date: 2012-09-18
forum: General Help
---

### Post by tomaberts on 2012-09-18
i need your help!! how can i clone my hard drive is there any tutorial that can i follow to clone my hard drive!!thanks

---

### Post by SlugSlug on 2012-09-18
depending on format

boot up clonezilla, or acronis if you can get it

or dd..

```
sudo dd if=/dev/sda of=/dev/sdb
```**this will destroy /dev/sdb and overwrite it with data on sda !**

---

### Post by dcstar on 2012-09-18
> **tomaberts said:**
> i need your help!! how can i clone my hard drive is there any tutorial that can i follow to clone my hard drive!!thanks

Yeah, there are probably over 1,000 tutorials if you go to this thing called "Google" and search for them.

Probably over 100 in these forums if you bother to search here.

---

### Post by tomaberts on 2012-09-18
thanks for your help!!!

---

### Post by tomaberts on 2012-09-18
is there any link that can i download the application?

---

### Post by Mark Phelps on 2012-09-18
> **tomaberts said:**
> is there any link that can i download the application?

One link? NO

Each of the apps suggested is free.  You will need to download a version that you can burn to CD or write to USB -- as you can't clone a drive while you're using it.  Any version you download from the Software Center is probably only going to install INSIDE Ubuntu -- which won't do you any good.

So, you have to figure out which one you want to use, go to their website, and download the app.

---

### Post by tomaberts on 2012-09-21
i already have a clonezilla application how can i write it on my flash drive?

---

