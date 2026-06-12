---
title: "sudo shutdown bite me"
date: 2010-03-24
forum: General Help
---

### Post by marsters256 on 2010-03-24
Why on earth is there no example in man shutdown 

this is driving me crazy.

Literally just wanna shut my computer down in half an hour

sudo shutdown -p 14:30

could somebody give me a clue as to what this pedantic w*nk of a command is ? 

and don't even get me started on the 'at' command

why does it lock up a terminal but let you type things and seem to do nothing!? It could at least clue me in as to what it's doing... -.-

at 14:00 shutdown -s             - windows shell command. 

Please help me to not throw linux out of the window

---

### Post by realzippy on 2010-03-24
```
sudo shutdown -h +30
```

shuts down in 30 minutes.If you want  specific time:

```
sudo shutdown -h 20:30
```

---

### Post by rahilm on 2010-03-24
the shutdown command has always confused me. That's why i used poweroff command.  the manual says that shutdown brings the computer down.. what does that mean?? it cannot be *THE* standard shutdown because then there are those -h, -H, and -P flags that say that they will power off the computer.

---

### Post by cjhabs on 2010-03-24
> **marsters256 said:**
> Why on earth is there no example in man shutdown 

this is driving me crazy.

Literally just wanna shut my computer down in half an hour

sudo shutdown -p 14:30

could somebody give me a clue as to what this pedantic w*nk of a command is ? 

and don't even get me started on the 'at' command

why does it lock up a terminal but let you type things and seem to do nothing!? It could at least clue me in as to what it's doing... -.-

at 14:00 shutdown -s             - windows shell command. 

Please help me to not throw linux out of the window

The man page is not great.
"shutdown --help" is much more helpful.

---

### Post by marsters256 on 2010-03-24
Thanks all that was brilliant I'm back in the game best forum response ever.

---

