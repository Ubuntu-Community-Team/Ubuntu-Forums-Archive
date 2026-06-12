---
title: "Location of mednafen .sav files?"
date: 2012-06-17
forum: General Help
---

### Post by oneguy on 2012-06-17
I've searched the mednafen documentation high and low, as well as the forums here and elsewhere. I'm fairly novice in terminal use. Keeping that in mind, where can I find the .sav files in order to copy them/back them up? Any special procedure for restoring them or applying them to mednafen on a different system? Thanks.

---

### Post by oneguy on 2012-06-17
Okay, here are the commands I entered to navigate to mednafen's save files:
```
cd ~/.mednafen

cd sav

```

Then I listed them by inputting: 
```

ls

```

I am such a novice, I forgot how to copy and move files, so I'll go look that up elsewhere. Hope this helps someone.

---

### Post by audiomick on 2012-06-17
> **oneguy said:**
> 
I am such a novice, I forgot how to copy and move files, 

The commands are cp for copy and mv for move. Look at the man pages for how to use them. I wont try and explain it, because I don't know it well myself.

```
man cp
```

```
man mv
```

---

### Post by andrew.46 on 2012-06-18
Unless you are dead-keen to use the terminal now you have found your files perhaps simply use nautilus / thunar etc and drag your backup files to the location of your choice? Otherwise give the location you wish to transfer the files to and myself or someone else here can volunteer a sample commandline :)

---

