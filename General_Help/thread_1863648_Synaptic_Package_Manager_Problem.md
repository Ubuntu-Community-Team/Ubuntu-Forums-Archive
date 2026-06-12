---
title: "Synaptic Package Manager Problem"
date: 2011-10-18
forum: General Help
---

### Post by southwest777 on 2011-10-18
Hello i added:

deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <maverick> 

to the software sources, but then i click reload and i got this error:


E: Malformed line 61 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I should have done: deb     [http://deb.torproject.org/torproject.org](http://deb.torproject.org/torproject.org) <maverick> main

I am trying to install tor for Ubuntu, but now since i added that software source i can't access the Synaptic Package manager anymore, or the Ubuntu software center. Synaptic shows that error and then i press close and it closes, and wont let me access the program and Ubuntu software center won't even load. What should i do? Be specific because i am new to the terminal (if your response has anything to do with the terminal).

Thanks!

I got everything from:
[https://www.torproject.org/docs/debian.html.en](https://www.torproject.org/docs/debian.html.en)

---

### Post by mikewhatever on 2011-10-18
You just have to correct the error.
Open the file with admin privileges:
```
gksudo gedit /etc/apt/sources.list
```

edit the line, save and exit.

The correct line should look like this: 
```
deb http://deb.torproject.org/torproject.org maverick main
```

---

