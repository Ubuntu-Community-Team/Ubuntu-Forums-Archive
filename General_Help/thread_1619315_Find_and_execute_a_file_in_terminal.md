---
title: "Find and execute a file in terminal??"
date: 2010-11-11
forum: General Help
---

### Post by victorhugo289 on 2010-11-11
Hi, how do you 'find and execute' a file in terminal??
I thought I could look for a file in terminal: 
---------find $HOME -iname 'song.mp3'
but if you want to execute it with totem: 
---------find $HOME -iname 'song.mp3' -exec totem"

The 'exec totem' part is not working. Any suggestions?? Thanks.

---

### Post by Vigh on 2010-11-11
just type totem and hit enter, should work

need to run as super user?

sudo totem

need a log, click back on the terminal and copy paste

to run shell scripts- sudo sh yourshellscript.sh

other scripts- ./yourscript

---

### Post by victorhugo289 on 2010-11-11
> **Vigh said:**
> just type totem and hit enter, should work
You mean I have to copy and paste the path to the file after the 'totem' command?? That's exxactly what I'm trying to avoid.

> **Vigh said:**
>   need to run as super user? 
no.

And I don't know how to use shellscripts.

---

### Post by sisco311 on 2010-11-11
> **victorhugo289 said:**
> Hi, how do you 'find and execute' a file in terminal??
I thought I could look for a file in terminal: 
---------find $HOME -iname 'song.mp3'
but if you want to execute it with totem: 
---------find $HOME -iname 'song.mp3' -exec totem"

The 'exec totem' part is not working. Any suggestions?? Thanks.

```
find $HOME -iname 'song.mp3' -exec totem '{}' +
```
Check out:
```
man find | less +/ACTIONS
```

---

### Post by victorhugo289 on 2010-11-11
> **sisco311 said:**
> ```
find $HOME -iname 'song.mp3' -exec totem '{}' +
```Check out:
```
man find | less +/ACTIONS
```

Yeah! Thanks a lot!!

---

