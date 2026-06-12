---
title: "Basic Script"
date: 2011-08-19
forum: General Help
---

### Post by jardineworks on 2011-08-19
I'm almost embarassed to ask this but I'm stuck. I have, within my home directory a directory called work and then with in that my company, and with in there a directory for each project.

$HOME/work/mycompany
                            project-a
                            project-b
                            ...
                            project-n

I've created a script (if you can even call it that!) and put it in my $HOME/bin folder. THe idea is that I will be able to type mycompany project-x from anywhere in the terminal and have my directory location changed to the work directory. My script has this right now ---

```

#!/bin/bash
cd $HOME/work/mycompany

```

.. with the intention of trapping the arguments once I see this working. I put some echo statements in originally to make sure that it was running, which it is, however, I never change location -- the script ends and I am still where I was when I ran it. 

What am I missing -- i know it's something simple but I can't see it.

---

### Post by sisco311 on 2011-08-19
It's because the script runs in a [subshell]("http://mywiki.wooledge.org/SubShell"). 

You can [*source*]("http://mywiki.wooledge.org/BashGuide/Sourcing") the script instead of running it as a child:
```
. yourscript
```

Or you could simply write a little [function or an alias]("http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions") and put it in your ~/.bashrc file.

---

### Post by CrusaderAD on 2011-08-19
Try this: 

```
#!/bin/bash
cd /HOME/work/mycompany
```

---

### Post by jardineworks on 2011-08-19
> **sisco311 said:**
> It's because the script runs in a [subshell]("http://mywiki.wooledge.org/SubShell"). 

You can [*source*]("http://mywiki.wooledge.org/BashGuide/Sourcing") the script instead of running it as a child:
```
. yourscript
```Or you could simply write a little [function or an alias]("http://mywiki.wooledge.org/BashGuide/CompoundCommands#Functions") and put it in your ~/.bashrc file.

That worked. Thanks Sisco311.

---

### Post by AlphaLexman on 2011-08-19
Another elegant solution is to add the appropriate pathname to the variable '**CDPATH**' in your ~/.bashrc file.
```
CDPATH="$CDPATH:$HOME/work/mycompany"
```And, that way you can simply 'cd' into any project directory!

---

