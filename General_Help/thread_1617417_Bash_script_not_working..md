---
title: "Bash script not working."
date: 2010-11-09
forum: General Help
---

### Post by ooolongT on 2010-11-09
Ok, I have given myself a little project, and I am hoping that it will teach me about some things that will make me a better Linux user.  

The first step of my project is to figure out what music files are in my Music folder.

Here is the beginning of my script. If I put the script in the Music folder, it works and generates my 'catalog' file.  However, if I put the script in a different directory (say, my Scripts directory), I don't get any errors, but I also get no 'catalog' file.

```


#!/bin/bash
##find /usr/src -not \( -name "*,v" -o -name ".*,v" \)
find /home/XX/Music -type f -print -name '*.mp3' > catalog

```

So I guess my question is, why do I not get my 'catalog' file if I place the script in a different directory?

---

### Post by iponeverything on 2010-11-09
> **ooolongT said:**
> Ok, I have given myself a little project, and I am hoping that it will teach me about some things that will make me a better Linux user.  

The first step of my project is to figure out what music files are in my Music folder.

Here is the beginning of my script. If I put the script in the Music folder, it works and generates my 'catalog' file.  However, if I put the script in a different directory (say, my Scripts directory), I don't get any errors, but I also get no 'catalog' file.

```


#!/bin/bash
##find /usr/src -not \( -name "*,v" -o -name ".*,v" \)
find /home/XX/Music -type f -print -name '*.mp3' > catalog

```

So I guess my question is, why do I not get my 'catalog' file if I place the script in a different directory?

add a complete path to catalog and make sure that the owner of the process has write priv's for that directory.

---

### Post by DaithiF on 2010-11-09
when you run a script there are TWO locations that are important:
1. The location of the script
2. The location you are in when you run the script (the 'current working directory')

It is the second of these that influences where relative-path output from that script is written, NOT the location of the script itself.

So, if your script is located in (for example):/home/you/scripts/, but you are located in /home/you when you run it, then the catalog file will get written to /home/you, and NOT /home/you/scripts

So check the directory you are in for the catalog file.

---

### Post by ooolongT on 2010-11-09
Excellent, I knew it was something simple!  I changed the code to:
```

#!/bin/bash
##find /usr/src -not \( -name "*,v" -o -name ".*,v" \)
find ~/Music -type f -print -name '*.mp3' > ~/Music/catalog

```

And it worked!  I will be back with more questions, I am sure, but thank you guys for the help!

---

