---
title: "Cannot get Bash script for checking 200 OK from webserver to work on Ubuntu"
date: 2011-09-22
forum: General Help
---

### Post by expatsys on 2011-09-22
On Ubuntu 11.04

I cannot get this script to work.. It works just fine under centOS 5, but not on any modern Linux including Ubuntu.

```
#!/bin/sh
$website=somesite
lynx -dump "$website" &> /dev/null
if [[ $? -eq 0 ]]; then
    echo Web Page Exists
else
    echo Web Page Doesnt exist
fi
```

(where somesite is actually a real URL starting with http)

The script is supposed to check for a 200 OK and return web page exists or doesn't exist sort of reply. 

It looks like the new version of lynx does something different.. it outputs an alternative website/page that does exist and completely ignores the method in which I try to do a silent dump... strange.

Any Ideas?

---

### Post by sisco311 on 2011-09-22
Welcome to the forums!

In Ubuntu, /bin/sh is a symlink to [dash]("http://en.wikipedia.org/wiki/Debian_Almquist_shell"). Also, if bash is invoked with the name sh, it tries to mimic the startup behavior of historical versions of sh, while confirming to the POSIX standard. But that's another story...

dash has no [[ command. That's one of the reasons why your script doesn't work in Ubuntu.

Not sure about the exit codes in lynx, but you could use **wget** to check if a page exist. 

**&>** is handy in interactive shells, but is very old syntax and is not part of POSIX. In a script I'd use the **> FILE 2>&1** form.

The syntax of if is:
```
if COMMAND; then COMMANDS; ... fi
```
There is no need to check the exit status of the command with $?

So, you can try something like:
```
if wget --spider "$site" > /dev/null 2>&1; then ...
```

HTH

---

### Post by expatsys on 2011-09-22
Thank you...

The Code worked!
```

if wget --spider "$site" > /dev/null 2>&1; then
    echo Web Page Exists
else
    echo Web Page Doesnt exist
fi


```

---

### Post by sisco311 on 2011-09-22
You are welcome!

---

