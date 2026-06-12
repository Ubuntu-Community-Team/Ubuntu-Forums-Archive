---
title: "bollocks"
date: 2006-05-12
forum: General Help
---

### Post by anubix on 2006-05-12
i accidentally exploded a tar file on my desktop so no i've got 2000+ .nasl files on my desktop w/o write permission
i try "rm *.nasl" even "rm *.*" and it tells me "too many arguements"

is there like a "safe mode" or something i can boot into and actually get this crap off my desktop?

thx

---

### Post by RavenOfOdin on 2006-05-12
[QUOTE=anubix]i accidentally exploded a tar file on my desktop so no i've got 2000+ .nasl files on my desktop w/o write permission
i try "rm *.nasl" even "rm *.*" and it tells me "too many arguements"

is there like a "safe mode" or something i can boot into and actually get this crap off my desktop?

thx[/QUOTE]

Would that by chance be for Nessus?

I did that too once :p but it was in a folder on my desktop for downloads.

Try recovery mode.

---

### Post by Resurrection on 2006-05-12
Couldn't you just do a sudo chmod on the whole Desktop folder to change the permissions?  As long as you make it recursive, it would do all the files in that folder.  Then I would think you could just do a rm *.nasl to get rid of all the files?  I know you tried rm, but you don't have permission, so maybe that is the problem.

Let me lookup the code just to see what the syntax should be, but in the meantime read "man chmod".

Someone else needs to double check me but:

To change the files and folder permissions from your user home directory for the Desktop folder:
```
sudo chmod -R a=rwx Desktop
```

then:
```
sudo rm -rf /Desktop/*.nasl
```

Edit:  Wait you may not have to do a chmod, read the rest of the thread first.

---

### Post by Mustard on 2006-05-12
I've had this issue before with trying to delete a large number of files.  I ended up deleting them by picking subsets with similar names and deleting a subset of the total with the relevant wildcard argument.  Eventually I got the number of files down to a point where I could finish the rest of with a single rm command.

---

### Post by henriquemaia on 2006-05-12
[QUOTE=anubix]i accidentally exploded a tar file on my desktop so no i've got 2000+ .nasl files on my desktop w/o write permission
i try "rm *.nasl" even "rm *.*" and it tells me "too many arguements"

is there like a "safe mode" or something i can boot into and actually get this crap off my desktop?

thx[/QUOTE]

Try:

```
sudo rm *.nasl
```

ps: This post is redundant. Just ignore it.

---

### Post by Resurrection on 2006-05-12
Yeah now that I think about it, sudo should take care of the permissions problems.  You shouldn't have to do a chmod.  Silly me.:-D

---

### Post by anubix on 2006-05-12
i got it off freenode it was like
 sudo cd ~/Desktop -exec rm *

sillys

---

