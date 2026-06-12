---
title: "can't get location of searched file"
date: 2012-02-20
forum: General Help
---

### Post by Jonatello on 2012-02-20
(i'm sure this had been brought up before, and i have been trying to find the answer in forum search, google, etc...no real luck though)

I love ubuntu, but this is the first time i've ever been really annoyed by it. I search for a file in nautilus, result comes up, and because i need to find what folder its in, i right-click>properties, only to see that the location is cut off with three dots...

how in the world do i just find out what folder this file is in?

this should be super obvious

---

### Post by ajgreeny on 2012-02-20
In terminal ```
find -name fliename.xxx
```Make sure you get the case of the name correct or use ```
find -iname fliename.xxx
``` if you're not sure of case.

---

### Post by Leppie on 2012-02-20
To get the location of a file, use the command "locate":
```
locate <filename>
```

---

