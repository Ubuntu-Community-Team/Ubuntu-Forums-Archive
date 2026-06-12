---
title: "Ln Directory Results in &quot;Too many levels of symbolic links&quot;"
date: 2012-03-30
forum: General Help
---

### Post by Shadow21 on 2012-03-30
I downloaded a program that is cross-platform (it didn't need anything to be installed) so I put it in my Dropbox folder to sync it across my computers. The program creates the folder .jCodeCollector in the home directory so I moved it into my Dropbox folder and used the command

```
ln -s .jCodeCollector ~/.jCodeCollector
```

to create a symbolic link to the file so that I can keep the folder synced.

When I try to use the symbolic link it gives me the error "Too many levels of symbolic links".

Did I use the wrong command or something?

---

### Post by brainwash on 2012-03-30
You should navigate to your Dropbox folder first (working directory) or add the path information in your command:
```
ln -s ~/Dropbox/.jCodeCollector ~/.jCodeCollector
```

---

### Post by Shadow21 on 2012-03-30
I figured it out. 

When I used: 

```
ln -s /home/nicholas/Dropbox/Programs/jCodeCollector/.jCodeCollector/ ~/

```

it worked.

---

