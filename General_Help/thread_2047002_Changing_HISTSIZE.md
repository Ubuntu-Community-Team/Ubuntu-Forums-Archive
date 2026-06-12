---
title: "Changing HISTSIZE"
date: 2012-08-24
forum: General Help
---

### Post by IAMTubby on 2012-08-24
Hi,
I wanted to change the number of logs displayed by the history command. I referred  the following link and made some changes to my /etc/profile.
[http://ubuntuforums.org/showthread.php?p=9534261]("http://ubuntuforums.org/showthread.php?p=9534261")

The last few lines of my /etc/profile now look like this
```
for i in /etc/profile.d/*.sh ; do
    if [ -r "$i" ]; then
        if [ "${-#*i}" != "$-" ]; then
            . $i
        else
            . $i >/dev/null 2>&1
        fi
    fi
done

unset i
unset pathmunge
export HISTFILESIZE = 2000
export HISTSIZE = 2000

``` 

It works for me also :). As in, even if I close and then open the terminal, it shows more than the default number of commands.

But the only problem is, whenever I login to my shell,
it gives me this kind of warning message.
```
-bash: export: `=': not a valid identifier
-bash: export: `2000': not a valid identifier
-bash: export: `=': not a valid identifier
-bash: export: `2000': not a valid identifier

```

1. Am I adding the code in the right place.
2. The thread mentioned above asks to make changes in 3 files.
/etc/profile, /etc/bash.bashrc, /etc/environment. I have done only to one, as I am getting the right output, and I'm scared to make so may system level changes, especially when something's almost working.


Please advise what to do.

Thanks.

---

### Post by IAMTubby on 2012-08-24
I am sorry. It's solved.
I put a space in between.

It should have been export HISTSIZE=2000.
I accidentally wrote export HISTSIZE = 2000. 

Sorry for the trouble. Marking thread as solved.

---

