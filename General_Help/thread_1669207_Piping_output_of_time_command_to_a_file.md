---
title: "Piping output of time command to a file"
date: 2011-01-17
forum: General Help
---

### Post by Rodayo on 2011-01-17
I'm trying to write the output of the time command to another file that I can then play around with..

Now I tried the following:
```
time sleep 1 > tmp
(time sleep 1) > tmp

```

In both cases tmp ends up empty. I read about the -o option for an output file so I tried:
```
time -o tmp sleep 1 > tmp
-o: command not found
```

But as you can see I get that error...not sure what else I can try

---

### Post by gmargo on 2011-01-17
Try this:
```

(time sleep 1) 2> tmp

```Also note that you are playing with the time command built into the bash shell.  There is also a **/usr/bin/time** command, documented in the **time(1)** man page, which is much fancier time command, and includes your -o option.

---

### Post by sisco311 on 2011-01-17
[http://mywiki.wooledge.org/BashFAQ/032](http://mywiki.wooledge.org/BashFAQ/032)

---

### Post by Rodayo on 2011-01-17
> **gmargo said:**
> Try this:
```

(time sleep 1) 2> tmp

```Also note that you are playing with the time command built into the bash shell.  There is also a **/usr/bin/time** command, documented in the **time(1)** man page, which is much fancier time command, and includes your -o option.

Fantastic. Worked perfectly...but what does the '2' mean?

---

### Post by sisco311 on 2011-01-17
**2>** redirects the command's stderr to a file.


See:
[http://mywiki.wooledge.org/BashGuide/InputAndOutput](http://mywiki.wooledge.org/BashGuide/InputAndOutput)
and of course the man page:
```
man bash | less +/"^REDIRECTION"
```

BTW, did you check out the link I posted? I would run time in a block instead of a subshell:
```
{ time comamnd; } 2> file
```

---

