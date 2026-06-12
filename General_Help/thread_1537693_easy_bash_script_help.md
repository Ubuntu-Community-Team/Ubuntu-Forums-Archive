---
title: "easy bash script help"
date: 2010-07-23
forum: General Help
---

### Post by v1ad on 2010-07-23
its been a 2 years since i wrote a bash script and i forgot almost everything and on this simple script i am getting an error.

can you show me the errors of my ways.

error is 
./conky1: line 5: [5: command not found
Conky is not running

```



#!/bin/bash

i=$(ps -ef | grep conky | wc -l)

if [$i -gt 1]; then 

    echo "Conky is running."

else

    echo "Conky is not running"

fi

exit 0 


```

---

### Post by ghostdog74 on 2010-07-23
```

$ ps -ef|grep -qi conk[y] && echo "ok" || echo "not ok"


```

```

if ps -ef|grep -qi conk[y]; then
  ....
fi

```

---

### Post by v1ad on 2010-07-23
main reason i want to make this script work is because i will be later on putting different variables into the if statements.


o ill try that.

---

### Post by v1ad on 2010-07-23
also any reason why that didn't work?

also that always returns true got to think of something else.

---

### Post by ghostdog74 on 2010-07-24
> **v1ad said:**
> also any reason why that didn't work?

put space between the square brackets and quote your variables
```


if [ "$i" -gt 1 ];then
 ..
fi

```

of you can use [[ ]] syntax
```

if [[ $i > 1 ]] ;then
fi

```

please see my sig for learning bash (again)

---

### Post by prodigy_ on 2010-07-24
> **ghostdog74 said:**
> ```
conk[y]
```
May I ask what's the significance of the square brackets here?

---

### Post by v1ad on 2010-07-24
this is my final result and is working would i have to put a & into it to run it in the background.
also the square brackets eliminated the result of the search. so i was happy with that.
```

#!/bin/bash
i=$(ps -ef | grep conk[y] | wc -l)

if [[ "$i" -gt 2 ]] ; then 

   exit 0 

else

    sleep 15
    /usr/bin/conky

fi

exit 0 


```

also this will run conky on startup with a timeout. 

for some reason when declaring i and declaring it posts the wc @ 2

---

### Post by bodhi.zazen on 2010-07-24
> **prodigy_ said:**
> May I ask what's the significance of the square brackets here?

It is a "regular expression". I am not sure it is needed.

---

### Post by v1ad on 2010-07-24
there completed and working.

```



#!/bin/bash
i=$(ps -ef | grep conk[y] | wc -l)
if [[ $i -gt 2 ]] ; then 

   echo $i >> /home/vlad/Desktop/conky_output
   exit 1
else

    sleep 15
    /usr/bin/conky 
fi

exit 0

```

---

### Post by ghostdog74 on 2010-07-24
> **prodigy_ said:**
> May I ask what's the significance of the square brackets here?

just so you don't have to grep -v grep the "grep" process

---

### Post by prodigy_ on 2010-07-24
> **ghostdog74 said:**
> just so you don't have to grep -v grep the "grep" process
A neat trick, thanks! :-)

---

### Post by bodhi.zazen on 2010-07-24
> **ghostdog74 said:**
> just so you don't have to grep -v grep the "grep" process

Interesting, does not work here :

> $ ps -ef | grep  firefox             07/24/10  9:14 AM
bodhi     2593     1  0 08:34 ?        00:00:00 /bin/sh /usr/lib64/firefox-3.6/run-mozilla.sh /usr/lib64/firefox-3.6/firefox
bodhi     2610  2593 10 08:34 ?        00:04:14 /usr/lib64/firefox-3.6/firefox
bodhi     3273  3010  0 09:15 pts/0    00:00:00 grep firefox

$ ps -ef | grep  firefo[x]           07/24/10  9:15 AM
zsh: no matches found: firefo[x]

nevermind, it works in bash but not zsh

---

### Post by ghostdog74 on 2010-07-27
> **bodhi.zazen said:**
> 
nevermind, it works in bash but not zsh
Problem is with the quotes. you have to quote it
```

ps -ef | grep "firefo[x]"


```

---

### Post by bodhi.zazen on 2010-07-27
> **ghostdog74 said:**
> Problem is with the quotes. you have to quote it
```

ps -ef | grep "firefo[x]"


```

I should have guessed that, thanks for the tip.

---

