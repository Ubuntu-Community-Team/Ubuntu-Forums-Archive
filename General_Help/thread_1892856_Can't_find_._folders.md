---
title: "Can't find . folders"
date: 2011-12-08
forum: General Help
---

### Post by The Linux Newb on 2011-12-08
In my home folder, there should be "." files (.minecraft and another folders that start with "." )

But I can't see them!
I know they exist though, as my minecraft says its located at /home/jay/.minecraft (I want to be able to access the .minecraft folder to install mods/textures) 

Also, when I was saving a Python program, and showed all the folders in my /home folder, it showed a bunch of folders I normally don't see - all starting with "." (including my elusive .minecraft folder) 

I went into terminal and typed 

cd ~/.minecraft
It works, and I can navigate through the .minecraft folder

But is there anyway to open it 'normally'?
Or is the only way to access the .minecraft folder through terminal?
If its the second scenario, how do I add files into folders in there?
Like if I have a texturepack zip file in my Downloads folder, how to I put that in .minecraft/texturepacks through terminal? 

Sorry I'm completely new to Linux operating systems (I only installed Ubuntu a few days ago), I'm used to Windows which is a lot different. 

note: The version of the OS is 11.10 64-bit

---

### Post by Jay Car on 2011-12-08
I may be misunderstanding your dilemma, but I think, after opening your Home folder, if you use Ctrl+h those hidden folders will be visible.

---

### Post by The Linux Newb on 2011-12-08
> **Jay Car said:**
> I may be misunderstanding your dilemma, but I think, after opening your Home folder, if you use Ctrl+h those hidden folders will be visible.

Wow, that was a lot simpler than I thought!
Thanks! 
*feels stupid*

---

### Post by killermist on 2011-12-08
```
ls -h
``` on the console will display hidden directories and files too.

---

### Post by Jay Car on 2011-12-08
> **The Linux Newb said:**
> Wow, that was a lot simpler than I thought!
Thanks! 
*feels stupid*

Please, never, ever, ever feel stupid. Seriously, a lot of us get help here and it's always better to ask a question when you get stuck. Sometimes it's the simplest things that cause the most frustration. Plus it's just nice to have a little help sometimes. 

:)

---

