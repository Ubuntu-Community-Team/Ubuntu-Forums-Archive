---
title: "loading files/programs into cache space."
date: 2009-11-07
forum: General Help
---

### Post by lavinog on 2009-11-07
I was curious if there was a way to load a program into cache memory without actually starting the program.

example:
I turn on my computer, and walk away...I would like my computer to preload firefox when my computer sits idle for a specific amount of time.  This way when I come back to my computer, if I decide to start firefox, it will startup quicker.

I understand that the preload program does this automatically, but I am looking for more control over what is loaded and at what times.

Also is there a way of checking if a program is loaded into the cache?

---

### Post by lavinog on 2009-11-09
I figured out how to load a program into cache by opening the file and reading it with python.

Now I just need to find out what files are loaded already.

---

### Post by DeMus on 2009-11-09
> **lavinog said:**
> I figured out how to load a program into cache by opening the file and reading it with python.

Now I just need to find out what files are loaded already.

Can you tell us what you did? This way others who like to do the same can benefit from it. Just saying you figured it out doesn't help much.

---

### Post by lavinog on 2009-11-09
I used python:
```

#! /usr/bin/env python
import os

def loadfile(file):
    if os.access(file, os.R_OK):
        f=open(file)
    
        while f.read(1024):
            pass
        f.close()

```
It's pretty crude at the moment.

Also lsof looks like the command I can use to get a list of files already cached.

I am experimenting with my own preloader.
My goals are:
Be able to select which apps to preload.
Preload files only when idle, and memory is available.
Ensure as much free memory is used.

Example:
I turn on my desktop and log in.
I start firefox, do some surfing, then walk away.
The preloader will then load other apps such as the gimp or blender.  Later if I want to use the gimp, it should startup quicker.

This could have gone in the programing forum, but I was looking to see if there was a command to already do this.

---

### Post by Ferux on 2010-04-26
Hey lavinog,

Any news about your preloader? I tried to use the script, but with no succes. How should I call it?

I tried
$ sudo python yourscript filename

but with no result.

---

### Post by lavinog on 2010-04-26
The script was kind of an example.  It provides a function loadfile() to read a file's contents, which will be cached in memory for quicker access later.
I haven't messed with the preloader much.  Once Lucid is released I might have some time to mess with this idea again.

---

