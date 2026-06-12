---
title: "Program cannot create files/folders"
date: 2011-07-01
forum: General Help
---

### Post by Parhelion on 2011-07-01
I am running the new Natty install of Ubuntu.  I always seem to have this particular problem, particularly with any ubuntu/kubuntu installs, but not other distros.

Basically, I'm trying to run a program -- a text-based game server.  The server needs to be able to create new folders and write and delete files within its own directories in order to work.  

However, no matter what I try to set in permissions, the program always spits out errors saying it was denied.  I have set the directories so that any user/program can write/delete in them, and it still doesn't work.

I'm pretty new to ubuntu in general, so if someone can tell me how to fix the problem and why it exists in the first place, that would be great.  :)

---

### Post by Azdour on 2011-07-01
Hi,

When the program says denied does it give you the path it is trying to create?

In which directory is this game server installed?

---

### Post by Parhelion on 2011-07-01
Hi, thanks for the response.

It's installed in my home directory.

So, for me, 

/home/sarah/game

It needs access to everything inside 'game'

---

### Post by Azdour on 2011-07-04
Hi,

Thats strange it should have access to that directory as that is in your home directory.

Can you open a terminal and type:
```
ls -la
```

In the list that gets displayed should be the game directory, can you post that line.

Can you then:
```

cd game
ls -la
```
Can you post the listing you get, just checking the permissions of the game directory and any sub directories it contains.

By the way how did you install the game?

---

