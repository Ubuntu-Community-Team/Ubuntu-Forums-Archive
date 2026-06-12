---
title: "Opening script in shell"
date: 2010-08-22
forum: General Help
---

### Post by sandyd on 2010-08-22
How can I open a script in a shell (konsole/terminal) with one command?

---

### Post by amauk on 2010-08-22
how do you mean?
Open to edit, or open to run

---

### Post by sandyd on 2010-08-23
> **amauk said:**
> how do you mean?
Open to edit, or open to run

open to run.

---

### Post by amauk on 2010-08-23
first, make sure it's marked executable
Right click file > Properties > Permissions
Check the box "allow executing as a program"

Then just double click the file,
and select "Run in terminal"

---

### Post by Dayofswords on 2010-08-23
if it doesn't have execute permission, give it to it
```
user@host:~$ chmod +x /path/to/script.sh
```
execute it with
```
user@host:~$ /path/to/script.sh
```
or use a relative path ( ./script.sh ( "." is current working directory)) for either command

---

### Post by sandyd on 2010-08-23
> **amauk said:**
> first, make sure it's marked executable
Right click file > Properties > Permissions
Check the box "allow executing as a program"

Then just double click the file,
and select "Run in terminal"

i meant how can I issue an command to open a script in a terminal. im using C++ system calls, so I dont have the terminal open by default.

---

### Post by gradinaruvasile on 2010-08-23
Like 

gnome-terminal -e scriptname

?

Or something equivalent for konsole.

Edit: It seems to be 

konsole -e scriptname

[http://www.digipedia.pl/man/doc/view/konsole.1/](http://www.digipedia.pl/man/doc/view/konsole.1/)

---

