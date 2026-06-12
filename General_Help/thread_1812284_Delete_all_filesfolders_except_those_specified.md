---
title: "Delete all files/folders except those specified"
date: 2011-07-26
forum: General Help
---

### Post by aeroman012000 on 2011-07-26
Although I've been using Ubuntu for a while, I haven't really done any scripting thus far, but now find myself needing to do (what I thought was) some fairly simple stuff. However, despite much searching, I have been unable to find a solution to my problem.

I need a script which will delete all of the files/folders from a directory except those I specify. From the command line, I am able to use:

rm -r !(constant|system|*.msh|)

which works fine, deleting everything except the 'constant' and 'system' folders (and everything in them) and any files ending in '.msh'. I have tried to put this into a script file, specifying to use the bash shell, and escaping the required characters, but I just get the message 'cannot find !(constant|*.msh)'.

I have read that using the find command may be a better way of doing it, but so far I have not been able to make the command work in the way which I need (I have easily been able to delete ALL the files/folders in the directory!).

I would be very grateful for any help which anyone could give me.

---

### Post by erind on 2011-07-26
Add '*shopt -s extglob*' at the top of your script:

```
#!/bin/bash
#set -x

[COLOR=Magenta]shopt -s extglob[/COLOR]

rm -r !(constant|system|*.msh)

```

---

