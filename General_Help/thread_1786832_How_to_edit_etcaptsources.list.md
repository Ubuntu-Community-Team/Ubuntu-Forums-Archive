---
title: "How to edit /etc/apt/sources.list"
date: 2011-06-20
forum: General Help
---

### Post by Spae on 2011-06-20
I know this is simple but confusing for me :)

Also when it says to add a line to that file, I'm guessing it doesn't matter where in the file that I add it? (assuming it's not a blank file)

\

---

### Post by collisionystm on 2011-06-20
> **Spae said:**
> I know this is simple but confusing for me :)

Also when it says to add a line to that file, I'm guessing it doesn't matter where in the file that I add it? (assuming it's not a blank file)

```

nano /etc/apt/sources.list
```


It doesn't matter where you add the new line. Although Generally you add it at the bottom or the very top that way you can keep track of your custom entries. You don't want to muck up your list with random things everywhere. Its hard to keep track of

---

### Post by haqking on 2011-06-20
> **collisionystm said:**
> ```

nano /etc/apt/sources.list
```
It doesn't matter where you add the new line. Although Generally you add it at the bottom or the very top that way you can keep track of your custom entries. You don't want to muck up your list with random things everywhere. Its hard to keep track of


he might be better using gksudo gedit /etc/apt/sources.list

nano can be confusing for the uninitiated, but if your comfortable with it then most editors will do the job ;-)

---

### Post by Spae on 2011-06-20
I actually figured it out :).

Only thing is, when i go to save it says error writing /etc/apt/sources.list permission denied

won't let me un-solve my thread now..

---

### Post by fballem on 2011-06-20
The replies beg the question, "Why do you wish to edit the sources list in the first place?"

The reason that I ask is that it is generally safer to use the repository editors in either Update Manager or Synaptic. This page might provide some help:

[https://wiki.ubuntu.com/fballem/Software](https://wiki.ubuntu.com/fballem/Software)

Regards,

---

### Post by darkdawn on 2011-06-20
> **collisionystm said:**
> ```

nano /etc/apt/sources.list
```


It doesn't matter where you add the new line. Although Generally you add it at the bottom or the very top that way you can keep track of your custom entries. You don't want to muck up your list with random things everywhere. Its hard to keep track of

I would like to add to what collisionystm said, and that is that before the PPA that you want to add, its a good habit to add a comment explaining what that PPA or repository is for,  like :

```
#This is a PPA for Pidgin
```

Its easier for later edit, especially when you have many repositories added, this way by adding the comment, you can easily identify what that repository is for!

EDIT: 
try :

```
sudo nano /etc/apt/sources.list
```

You needed root permission to edit the file, that's all :)

---

