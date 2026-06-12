---
title: "and spooky songbird disappeared right infront of me..."
date: 2009-11-23
forum: General Help
---

### Post by camaron1 on 2009-11-23
That is exactly what happened just now. I was playing music with songbird, I added some items to the library, I did this at the exact time when the last item of the current play list finished, songbird closed, I tried to reopen it from AWN but wouldn't open, tried with the main apps. menu, the icon wasn't there, looked at usr/bin, it wasn't there, checked synaptic and said it wasn't installed so  installed it again and right now is playing away no problem.

[SIZE=4]How could this happen???[/SIZE]

---

### Post by NoaHall on 2009-11-23
This happened to me too, yesterday...

---

### Post by camaron1 on 2009-11-23
> **NoaHall said:**
> This happened to me too, yesterday...
Seriously, with Songbird too? can you risk any explanation?

---

### Post by NoaHall on 2009-11-23
> **camaron1 said:**
> Seriously, with Songbird too? can you risk any explanation?

Well, perhaps a built in update caused it to crash(for one of the plugins) or caused it to delete /usr/bin/songbird.

---

### Post by camaron1 on 2009-11-23
Well, never mind I guess, It's working now.

---

### Post by wilee-nilee on 2009-11-23
programs that seem to close and don't open again can be killed with htop or using the right click kill in system monitor. If you run into this situation it seems best to look in the system monitor to see if it is still on.

---

### Post by NoaHall on 2009-11-23
> **wilee-nilee said:**
> programs that seem to close and don't open again can be killed with htop or using the right click kill in system monitor. If you run into this situation it seems best to look in the system monitor to see if it is still on.

That isn't the problem at all. The problem was that the binary file for songbird disappeared.

---

### Post by camaron1 on 2009-11-23
> **wilee-nilee said:**
> programs that seem to close and don't open again can be killed with htop or using the right click kill in system monitor. If you run into this situation it seems best to look in the system monitor to see if it is still on.
I forgot to mention that I did check the system monitor and it wasn't there either. As Noahall says the binary was totally gone, it literally disappeared.

---

### Post by wilee-nilee on 2009-11-23
> **camaron1 said:**
> I forgot to mention that I did check the system monitor and it wasn't there either. As Noahall says the binary was totally gone, it literally disappeared.

Strange behavior, you might also install htop from the command line or synaptic it is a pretty good monitor that allows removal or killing of a program. Not complete removal from the OS but from functioning within it during use.

---

### Post by camaron1 on 2009-11-23
> Strange behavior, you might also install htop from the command line or synaptic it is a pretty good monitor that allows removal or killing of a program. Not complete removal from the OS but from functioning within it during use.

Thanks for the tip, I'm going to check htop out

---

### Post by camaron1 on 2009-11-23
Just for the interested.

I also typed **locate songbird** in terminal and it did locate the binary although it wasn't actually there...

---

### Post by NoaHall on 2009-11-23
> **camaron1 said:**
> Just for the interested.

I also typed **locate songbird** in terminal and it did locate the binary although it wasn't actually there...

I also did that, but I first updated the database, and it said it wasn't there.

---

### Post by camaron1 on 2009-11-23
> I also did that, but I first updated the database, and it said it wasn't there. 	

That is a good one: how do you update the database? I'd like to know that one...

---

### Post by lisati on 2009-11-23
It almost sounds like some kind of conflict in your systems that lets one thing see something (possibly a note in a cache somewhere) and blocks it from being seen by another.

---

### Post by NoaHall on 2009-11-23
> **camaron1 said:**
> That is a good one: how do you update the database? I'd like to know that one...

sudo updatedb

---

### Post by gali98 on 2009-11-23
```
sudo updatedb
```
This is very strange....
Kory

---

### Post by camaron1 on 2009-11-23
> sudo updatedb
Thanks, another tip to take with me tonight> 
[QUOTE]It almost sounds like some kind of conflict in your systems that lets one thing see something (possibly a note in a cache somewhere) and blocks it from being seen by another.

Do you mean that the binary was actually there but wasn't seen by the system?

---

### Post by wilee-nilee on 2009-11-23
When you look in system monitor it is a good idea to have all processes and dependencies showing as well, there might be a stuck dependency that is keeping it from opening.

---

### Post by camaron1 on 2009-11-23
> **wilee-nilee said:**
> When you look in system monitor it is a good idea to have all processes and dependencies showing as well, there might be a stuck dependency that is keeping it from opening.
That sounds OK for pretty specialized work with computers, but I suppose if you are running a home desktop a quick check on ram consumption or the odd killing of a rebellious app. is usually enough. Problem in this case still is that the binary for some reason was delated (or so it seems...). This is pretty estrange behavior. I doubt I'll ever know how this happened but I do fell really curious about what could cause such a thing.

---

