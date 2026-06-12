---
title: "turn a script into a shell utility"
date: 2011-02-11
forum: General Help
---

### Post by FunkyLich on 2011-02-11
Hi,
I would like to know if it is possible to convert a script into a utility like 'ls' or 'grep'. This way I can call it without having to navigate to the directory that contains the script each time.

For example, here is a code that takes its argument and finds a child directory that matches that argument and proceeds to change to that directory. Say, as a utility, I call it 'fndcd' (since the script is named 'fndcd.sh').

```
#!/bin/bash
cd && cd `ls -R | grep $* | grep / | sed 's/://'`
```Right now, in order for a script like this to work I have to use:
```

source /filepath/.../scripts/fndcd.sh Music
```And that takes me to my music folder. But I want this to be a utility so I don't have to navigate to the script every time. Please don't get caught up in the specifics of my script if it's problematic. I just want to know if making a script into a utility is possible, and if it is how. If it's not, why not? Also if not, how would one go about creating a utility for their shell?

---

### Post by i.r.id10t on 2011-02-11
Just put it somewhere in your path, /usr/local/bin would work

---

### Post by FunkyLich on 2011-02-11
Awesome, that's perfect. Thanks.

---

### Post by hawkmage on 2011-02-11
In recent versions of Ubuntu (not sure what versions it is included on but atleast in 10.04 and 10.10) the default ".profile" has the following code in it:
```
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```
This will check for the existence of a directory called bin in your home directory and include it in your path if it is there.  

If you create that directory, place your scripts in there and set the permissions to allow you to execute it you should be good to go.

---

