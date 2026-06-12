---
title: "Builtin source . (dot) command"
date: 2010-11-23
forum: General Help
---

### Post by EnigmaticCoder on 2010-11-23
Whenever I compile Dreamcast games, I must source a certain .sh file before running make. I like to use the Netbeans IDE, so I must run these commands in a terminal

```

$ source environ.sh 
$ "/usr/local/netbeans-6.9.1/bin/netbeans"

```

However, this forces me to run netbeans from the terminal when I'd like to run netbeans from a launcher or alt + f2. This method forces me to keep the terminal open when I run netbeans. The problem is, source is a shell builtin command and cannot be run from a launcher (as far as I know). Is there an equivalent to source that I can run from a launcher? How else can I solve this problem?

---

### Post by EnigmaticCoder on 2010-11-24
Bump

---

### Post by amauk on 2010-11-24
you can add
```
source environ.sh
```
to the end of your ~/.bashrc file

This will source the file at every login
and any programs you run will have access to the environment variables

---

### Post by EnigmaticCoder on 2010-11-25
That lets me not source the file before I run Neatbeans, but I still have to run the IDE from a terminal for my Dreamcast game to compile. Otherwise, if I just run Netbeans from the launcher, the game won't compile.

---

### Post by asmoore82 on 2010-11-25
Create a shell script of your `source` and `netbeans`
and call this new script from a custom launcher:
```
#!/bin/bash

source *<path>*/environ.sh
/usr/local/netbeans-6.9.1/bin/netbeans

#End of File
```

I would put this in either "$HOME/bin" or "$HOME/.local/bin" so that if you simply run `netbeans` it runs this as well. Make sure your personal bin is included at the end of your "$HOME/.profile" ...
```
if [ -d "$HOME/.local/bin" ]; then
    PATH="$HOME/.local/bin:$PATH"
fi
```

---

### Post by EnigmaticCoder on 2010-11-27
Thank you :)

My bottom panel is now decluttered, and I know a little bit more about Linux. I have a new technique if I encounter similar problems in the future.

---

