---
title: "Where did flashplayer-mozilla go?"
date: 2006-03-23
forum: General Help
---

### Post by kwaanens on 2006-03-23
By accident I removed flashplayer-mozilla, and now I can't view shockwave flash anymore?
Where did it go, and how do I get it back?

I have flashplugin-nonfree version 7.0.63.1-build1 installed, and that's still in the repos.

- Ketil

---

### Post by gord on 2006-03-23
make sure you have [enabled extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) and 
```
sudo apt-get install flashplayer-mozilla
```

---

### Post by kwaanens on 2006-03-25
[QUOTE=gord]make sure you have [enabled extra repositorys](http://help.ubuntu.com/starterguide/C/faqguide-all.html#addinguniverse) and 
```
sudo apt-get install flashplayer-mozilla
```[/QUOTE]

I have, and it's not there.
It was installed on my system, but I removed it by accident.

- Ketil

---

### Post by Perfect Storm on 2006-03-25
try first with a 
```
sudo apt-get update
```

and see if it helps.

---

### Post by kwaanens on 2006-03-25
[QUOTE=Artificial Intelligence]try first with a 
```
sudo apt-get update
```

and see if it helps.[/QUOTE]

Tried with an apt-get update. (I update and upgrade every day)
No cigar :(

- Ketil

---

### Post by Perfect Storm on 2006-03-25
Try with

```
sudo apt-get install libflash-mozplugin
```

---

### Post by int on 2006-03-25
[QUOTE=Artificial Intelligence]Try with

```
sudo apt-get install libflash-mozplugin
```[/QUOTE]

Work's fine..


That's the new packaged?

---

### Post by kwaanens on 2006-03-25
[QUOTE=int]Work's fine..


That's the new packaged?[/QUOTE]

Nope, and it doesn't work fine here either. The package I'm asking about is Macromedia's own, I think.
Your suggestion makes my Firefox crash, and I remember it being troublesome with Breezy and Hoary as well.

- Ketil

---

### Post by int on 2006-03-25
[QUOTE=kwaanens]Nope, and it doesn't work fine here either. The package I'm asking about is Macromedia's own, I think.
Your suggestion makes my Firefox crash, and I remember it being troublesome with Breezy and Hoary as well.

- Ketil[/QUOTE]

Ya.. the packaged change name..

```
sudo apt-get flashplugin-nonfree
sudo /usr/sbin/update-flashplugin
```

---

### Post by kwaanens on 2006-03-25
[QUOTE=int]Ya.. the packaged change name..

```
sudo apt-get flashplugin-nonfree
sudo /usr/sbin/update-flashplugin
```[/QUOTE]

That did the trick!

How did you know you had to issue that command?

And, also, this package isn't new, I had it installed since I first set up 
Dapper, but then flashplayer-mozilla was also present.

- Ketil

---

