---
title: "One-way file sync"
date: 2009-07-30
forum: General Help
---

### Post by Warthaug on 2009-07-30
I feel kinda dumb for asking this, but the help page on rsync isn't clear on this point.

What I am looking for is an app which I can use to synchronize my laptop with our server at work.  I want to do a "sort-of" 1-way sync, as in I would like all new files in my work directory on my laptop to be transfered to my directory on the server.  I would like all old versions of files on the server replaced with the new (modified) versions on the laptop.  And I want nothing to be transfered from the server to laptop.  

As far as I can tell rsyc/grsync does all of the above.  

But what cannot happen - and what I'm not sure about rsync, is that I don't want anything to be removed from the server.  I frequently remove things from my laptop that are then stored only on the server.  Deleting that would be bad...

Is rsync/grsyn what I want for this, or am I looking for something else?

thanx

Bryan

---

### Post by The Cog on 2009-07-30
rsync is fine for this. I would suggest using "rsync -av ..." for now. If you wanted to remove files from the server that don't have corresponding files on the laptop, you would also need to use the --delete flag - it's not somethig that you are likely to do by accident.

I've never looked at grsync, but since I think it is just a GUI wrapper round rsync, I guess it will have much the same capabilities.

---

### Post by The Cog on 2009-07-30
P.S.
If you don't also use a -u or --update flag, rsync will happily overwrite files on the server that are newer than on the laptop. -u prevents overwriting of newer versions with older ones. It's down to you usage requirements as to which behaviour you want.

Personally, I use the -u, and use the server as a common repository, and rsync in both directions to several client PCs so an update on one PC gets propogated via the server to the other clients eventually. But then that's just the way I choose to use it.

---

### Post by Warthaug on 2009-07-30
Thanx, that is exactly what I was looking for.

You are right - grsync is just a GUI, but for a relative linux newbie it makes things easier...

Bryan

---

