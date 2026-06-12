---
title: "How to use ssh to execute such kind of script"
date: 2010-03-10
forum: General Help
---

### Post by mythmgn on 2010-03-10
Hi, all,

I have such kind of problem recently.

I need to run a command in the remote machine.

The script's first line contains "source profile.xxx"

#!/bin/sh
. ${CONF_XXX}/profile.perf


Therefore, when I run it this way:

ssh root@pprh4 /scratch/pa/pa701/path/1.2/bin/plcclient.sh -s

it says "profile.xxx No such file or directory"

And another one is how can I use a specific file for storing my password so that I don't have to type it?

Thank you in advance!

---

### Post by makingtheswitch on 2010-03-17
I'm not sure about your first questions, but I think you would need to copy the script to the remote machine before you ssh into it, then run it.

As for your second question, I'd recommend reading the man page for ssh-keygen or searching for RSA SSH key.  There are plenty of guides.

---

### Post by n0dix on 2010-03-17
To copy the file remotely use scp.
For more info do:
```
$ man scp
```
After you copy the file, you can be able to use ssh to connect and run the script.

---

### Post by n0dix on 2010-03-17
<deleted>

---

