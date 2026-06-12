---
title: "Creating a command to open multiple terminal windows that SSH into the same server."
date: 2010-04-07
forum: General Help
---

### Post by jabour on 2010-04-07
Every time I boot up ubuntu I usually open 3 terminal windows and ssh into the same server. I would like to either click a shortcut, or run a single terminal command that will do the equivalent.

I came across the "gnome-terminal" command, but I was unable to get it to trigger an ssh command.

Ideally I would like to have a script that I pass in the number of windows I want to open and the server I would like to ssh into for each window.

Any help, guidance, or suggestions are GREATLY appreciated.

---

### Post by colorlessprism on 2010-04-07
i have no experience with ssh, however you could make a file using pipelines

"gnome-terminal ssh -l T.Bradley | gnome-terminal ssh -l T.Bradley | gnome-terminal ssh -l T.Bradley"

this should open three terminals. you could also go to startup programs and "ADD" this command so your computer would do this for you automatically and no file would be needed

---

### Post by Gunman1982 on 2010-04-07
Well how did you try to execute the gnome-terminal command?

I would suggest creating a shell file like this
```

#!/bin/sh

for i in 1 2 3
do
gnome-terminal -x ssh whatever_your_ssh_host_is
done

```

Don't know how to do a for with variable length atm, but you can google it quickly I guess.
Save that file as whatever you like and set its executable bit (chmod or via gnome)

---

### Post by jobix on 2010-04-07
Building upon Gunman1982's example above:

> #!/bin/sh

for (( i=0; i<$1; i++ ))
do
gnome-terminal -x ssh whatever_your_ssh_host_is
done

$1 is what you would pass as an argument to your script and is the number of windows you want to open. For example, you would call your script like this to open 3 windows:

./your_script 3

Also, if you set up ssh-agent, you won't even have to enter the password for all those windows. Makes life easier.

---

### Post by jabour on 2010-04-07
Thank you all so much for the quick help!

Here is what I ended up doing after I looked at your solutions:

#!/bin/bash

for (( i=0; i<$1; i++ ))
do
    gnome-terminal -x ssh my_host
done

I kept everything that Jobix wrote except I changed the shell to the Bourne-again shell(bash) instead of the Bourne shell (sh). Works like a charm with that change.

Does anyone know why I needed to make the change? 

The error I received when using sh was "4: Syntax error: Bad for loop variable"

Thanks again all for the help. Please let me know if you know why I had to use bash instead of sh.

---

