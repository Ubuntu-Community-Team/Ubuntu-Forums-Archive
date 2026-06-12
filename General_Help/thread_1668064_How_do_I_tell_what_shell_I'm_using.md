---
title: "How do I tell what shell I'm using?"
date: 2011-01-15
forum: General Help
---

### Post by terminator14 on 2011-01-15
I wrote a script a while back that is supposed to be run in bash. It includes a hashpling (#!/bin/bash). Some people who are using the script are having problems with it however because they are forcing it to run in sh. They are doing things like:

```
sh script.sh
```

and 

```
cat script.sh | sh
```

which ignores the hashpling and runs the script in sh, making the script fail half way through.

How do I make my script determine the shell it's being run in and stop running if it's in /bin/sh?

PS:

No, it's not

```
echo $SHELL
```

which has nothing to do with the shell you are currently in.

No it's not

```
echo $0
```

which can be used in an interactive shell but does not work the same way in a script.

No it's not 

```
ps -p $$
```

as this will not work inside of a script the same way as it does in an interactive shell either.

Those are the 3 methods that people keep describing when searching for the answer on google, and none of those works for what I need. Any suggestions?

---

### Post by WorMzy on 2011-01-15
```
ps ch -o %c $$
```
?

Personally, I'd just say in the readme to run with bash, not sh. If your users can't follow simple instructions, then why should you have to bend over backwards for them?

---

### Post by Smart Viking on 2011-01-15
I this is kind of funny because it doesn't work in dash, but anyway, your users can't be stupid enough to not understand this! :)
```

#!/bin/bash
echo "Are you running this script in bash?"
select result in Yes No
do
    if [ $result = "Yes" ]; then
        break
    fi
    if [ $result = "No" ]; then
        exit
    fi
done
echo "omgomg"

```

---

### Post by terminator14 on 2011-01-15
> **WorMzy said:**
> ```
ps ch -o %c $$
```

This again experiences the same problem as some of the other solutions - it works in a terminal but as soon as you put it in a script your result is the script name. This appears to be caused by $$ giving the PID of the script and not the shell when the command is executed from within a script. Is there a more reliable way to get the shell name?

> **WorMzy said:**
> Personally, I'd just say in the readme to run with bash, not sh. If your users can't follow simple instructions, then why should you have to bend over backwards for them?

The readme does say that the script was written in bash, and if the users aren't sure, they can always check the first line of the script for the hashpling (like I do if I'm curious, not that I have to since the hashpling automates things anyway as long as you run the script properly). Users tend to not read instructions however and complain when running the script using /bin/sh doesn't work. 

Normally I'd agree that if I can spend hours or days writing a complex script for users to use for free, it would be nice if the users could at least have the knowledge of the 2 lines that it takes to run a script properly. In a perfect world, that would be the case, but since some user's can't run scripts correctly, and I get responses stating the script doesn't work, I have to do what I can to make it (I hate to say this...) idiot proof.

> **Smart Viking said:**
> I this is kind of funny because it doesn't work in dash, but anyway, your users can't be stupid enough to not understand this! :)
```

#!/bin/bash
echo "Are you running this script in bash?"
select result in Yes No
do
    if [ $result = "Yes" ]; then
        break
    fi
    if [ $result = "No" ]; then
        exit
    fi
done
echo "omgomg"

```

That is definitely something I can do, and is easy enough to implement but I was hoping for something that could determine if it was running in the right environment automatically. Users can simply ignore this and continue without reading or thinking about it. I figured it would be easy enough to check which shell the script is running in, and from there it would be easy enough to display a message and exit only in the case of the wrong shell being used. It appears that checking which shell the script is running in is not as easy as I thought though. The only thing I can think of (that may or may not work) is doing some complex trickery with PPID of current PID. There must be an easier and more reliable way...

---

### Post by efflandt on 2011-01-16
Almost there:

```
#!/bin/bash
ps ax | grep $$ | grep bash > /dev/null || exit "Wrong shell, see README"
echo Running bash
``````
efflandt@natty-ssd:~/bin$ **shelltest**
Running bash

efflandt@natty-ssd:~/bin$ **sh shelltest**
exit: 2: Illegal number: Wrong shell, see README
```

Or maybe you can find something that bash can do that dash cannot in a way that can pump out a useful error message (in case sh is bash on that system)

---

### Post by WorMzy on 2011-01-16
> **terminator14 said:**
> This again experiences the same problem as some of the other solutions - it works in a terminal but as soon as you put it in a script your result is the script name.

I've had a bit more of a play around with this, and this seems to work fine: ```
ps h -o cmd $$ | awk '{print $1}' | sed 's/\/bin\///'
```

[IMG]http://img402.imageshack.us/img402/7659/20110116144450404x265sc.png[/IMG]

---

### Post by terminator14 on 2011-01-16
> **efflandt said:**
> Almost there:

```
#!/bin/bash
ps ax | grep $$ | grep bash > /dev/null || exit "Wrong shell, see README"
echo Running bash
``````
efflandt@natty-ssd:~/bin$ **shelltest**
Running bash

efflandt@natty-ssd:~/bin$ **sh shelltest**
exit: 2: Illegal number: Wrong shell, see README
```

Or maybe you can find something that bash can do that dash cannot in a way that can pump out a useful error message (in case sh is bash on that system)

This was a good one, but the "exit: 2: Illegal number: " part bugged me a bit so I modified it slightly. The main idea is the same however so thanks a lot for that.

> **WorMzy said:**
> I've had a bit more of a play around with this, and this seems to work fine: ```
ps h -o cmd $$ | awk '{print $1}' | sed 's/\/bin\///'
```

[IMG]http://img402.imageshack.us/img402/7659/20110116144450404x265sc.png[/IMG]

This is an excellent way and works great. Thanks.

So here are three ways for people still looking for a solution:

```
ps ax | grep $$ | grep bash > /dev/null || { echo Wrong shell; exit 1; }
```

Thanks to efflandt for that one,

```
ps h -o cmd $$ | awk '{print $1}' | sed 's/\/bin\///'
```

Thanks WorMzy for that one, and

```
[[ "1" -eq "1" ]] 2>/dev/null || { echo not bash; exit 1; }
```

This one just occurred to me a minute ago. It seems to work pretty good as well.

---

### Post by terminator14 on 2011-01-16
Accidental double post deleted.

---

