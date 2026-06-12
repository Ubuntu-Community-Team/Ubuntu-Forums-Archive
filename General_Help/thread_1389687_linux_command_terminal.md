---
title: "linux command terminal"
date: 2010-01-24
forum: General Help
---

### Post by computerguts on 2010-01-24
Were can I find a complete list of commands for the terminal in ubuntu linux 9.10

---

### Post by infinitejones on 2010-01-24
Here's a [good place to start]("http://ss64.com/bash/")!

---

### Post by jmszr on 2010-01-24
computerguts,

This is a good start: [http://gd.tuwien.ac.at/linuxcommand.org/index.php](http://gd.tuwien.ac.at/linuxcommand.org/index.php)

---

### Post by computerguts on 2010-01-24
what is a website were I can find a complete list of linux commands for the command terminal ?

---

### Post by Shhnap on 2010-01-24
Huh, nobody suggested reading the man or info pages. Just try typing in 'man man' or 'info' in a terminal and the help lies here. Man is for manual pages and info is for info on all programs. :) I hope that helps.

---

### Post by falconindy on 2010-01-24
[www.tldp.org](www.tldp.org) is a good place to start. You also have access to the command line manual "man", which has searching capabilities of its own. If you want to find commands that relate to video, you can type "man -k video" and you'll get a list of programs that deal with video. If you'd like more information about one of them, use "man <command>" to bring up a man page about that program.

---

### Post by malspa on 2010-01-24
How about:

[http://ss64.com/bash/](http://ss64.com/bash/)

or

[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

---

### Post by overdrank on 2010-01-24
Please do not create multiple threads on the same issue. Threads merged.

---

### Post by oldos2er on 2010-01-24
> **computerguts said:**
> Were can I find a complete list of commands for the terminal in ubuntu linux 9.10

Hit Tab twice.

---

### Post by malspa on 2010-01-24
> **oldos2er said:**
> Hit Tab twice.

I think that an equivalent shortcut is alt + ? (holding down the alt key while typing a question mark).

Is there a way to send the results of that to a text file?

---

### Post by malspa on 2010-01-24
Also, I found an interesting bit of info at the following web page:

[http://stackoverflow.com/questions/948008/linux-command-to-list-all-available-commands-and-aliases](http://stackoverflow.com/questions/948008/linux-command-to-list-all-available-commands-and-aliases)


Check this out:

    * "compgen -c" will list all the commands you could run.
    * "compgen -a" will list all the aliases you could run.
    * "compgen -b" will list all the built-ins you could run.
    * "compgen -k" will list all the keywords you could run.
    * "compgen -A function" will list all the functions you could run.
    * "compgen -A function -abck" will list all the above in one go.

So, I tried the following command to send a sorted list of all of those to a text file:

```
$  compgen -A function -abck | sort > listofcommands.txt
```

What do you think, does that include everything?

---

### Post by computerguts on 2010-01-24
thanks

---

