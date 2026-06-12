---
title: "lynx web browser -- what does it consider a binary file?"
date: 2010-09-27
forum: General Help
---

### Post by jejones3141 on 2010-09-27
I want to retrieve a file--it's a compressed tar file, and I can get to it via a certain URL (with a query, so it's of the form <URL>?<search options>). If I go there via Firefox, I get a prompt to download the file. Lynx documentation says that if a file is binary, rather than displaying it it will give me the option of downloading it. (Which of course I will pick; I will use the option to save the commands I type, and then when I want to run it from a script give lynx the option telling it to retrieve and use those saved commands.)

The problem: this compressed tar file, which you'd think would be recognizable as a binary file, isn't; lynx displays a page of garbage and asks me whether I'd like another.

So, my question is: how does lynx decide what it thinks is a binary file? I have grabbed the sources, and will search them, but a pointer or suggestion would be greatly appreciated.

---

### Post by luigi_mb on 2010-09-27
Highlight the file you want and press "d" (download), etc. 

/luigi

---

