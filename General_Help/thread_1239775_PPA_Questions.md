---
title: "PPA Questions"
date: 2009-08-13
forum: General Help
---

### Post by rcayea on 2009-08-13
How can I save my current ppa's that I have already installed, along with the authentication key so I may use them after I do a fresh install. I like to once in a while, clean my HD by reinstalling for a clean start (something I love about Ubuntu being free). Anyway, I hate having to go back and reinstall all ppas. 

Any suggestions?

Thanks,
Randy

---

### Post by bboston7 on 2009-08-13
Your list of ppas is found at /etc/apt/sources.list

You could
```
cp /etc/apt/sources.list /your/backup/folder
```

this copies the sources list to a backup folder.

I don't know about the keys.

---

### Post by rcayea on 2009-08-13
thanks for the tip. I guess if I at least know what ppas I had, I could always copy/paste into google and the associated key will presumably be mentioned in whatever site I find.

Thanks,
Randy

---

### Post by starcraft.man on 2009-08-13
As already mentioned back up your sources list for the actual repo locations. For keys do the following:

```
sudo apt-key exportall > KeyBackup.asc
```

The first part of command outputs all keys to standard output, > and after puts all the output into a file named keybackup.asc, extension is just so ya remember it's a key.

To import later:

```
sudo apt-key add /path/to/file/keybackup.asc
```

I'd like to note, in first command your making a file in your working directory. If you want, substitute an absolute/relative path to wherever ya like.

After install, restore both sources list and keys, then update aptitude and have fun.

If you also feel like reinstalling all current packages, see this nice tip on page: [http://ubuntuforums.org/showpost.php?p=7647357&postcount=3](http://ubuntuforums.org/showpost.php?p=7647357&postcount=3)

---

### Post by bboston7 on 2009-08-13
Looks like I answered too slow!

---

### Post by starcraft.man on 2009-08-13
> **bboston7 said:**
> Looks like I answered too slow!

Better luck next time. :)

---

### Post by bboston7 on 2009-08-13
> **starcraft.man said:**
> Better luck next time. :)

At least I got the sources.list answer in.  :lolflag:

---

### Post by rcayea on 2009-08-13
> **starcraft.man said:**
> As already mentioned back up your sources list for the actual repo locations. For keys do the following:

```
sudo apt-key exportall > KeyBackup.asc
```

The first part of command outputs all keys to standard output, > and after puts all the output into a file named keybackup.asc, extension is just so ya remember it's a key.

To import later:

```
sudo apt-key add /path/to/file/keybackup.asc
```

I'd like to note, in first command your making a file in your working directory. If you want, substitute an absolute/relative path to wherever ya like.


After install, restore both sources list and keys, then update aptitude and have fun.

If you also feel like reinstalling all current packages, see this nice tip on page: [http://ubuntuforums.org/showpost.php?p=7647357&postcount=3](http://ubuntuforums.org/showpost.php?p=7647357&postcount=3)



Awesome info! Thank you! I love this ubuntu community!  :)

---

### Post by peyu on 2010-02-10
> **bboston7 said:**
> Your list of ppas is found at /etc/apt/sources.list

You could
```
cp /etc/apt/sources.list /your/backup/folder
```

this copies the sources list to a backup folder.

I don't know about the keys.

Well, I want also to backup my ppa list...
I'm using 9.10, and I had a look to /etc/apt/sources.list, but there is only "official" repositories in it... All ppa repositories are under /etc/apt/sources.list.d/, with one text file for each PPA. Do I have to copy all this directory? Or the whole /etc/apt ?

Thanks!

---

