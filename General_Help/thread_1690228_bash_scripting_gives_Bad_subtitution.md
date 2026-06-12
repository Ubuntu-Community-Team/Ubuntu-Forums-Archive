---
title: "bash scripting gives Bad subtitution"
date: 2011-02-18
forum: General Help
---

### Post by kios on 2011-02-18
Hey. i'm trying to get the substring of a string in bash. Here is the code

```
#! /bin/bash

LOCAL_HOSTNAME=$(hostname)
echo $LOCAL_HOSTNAME
INDEX_OF=`expr index "$LOCAL_HOSTNAME" 1`
echo $INDEX_OF
SERVER_HOSTNAME=${LOCAL_HOSTNAME:0:INDEX_OF}
echo $SERVER_HOSTNAME
```

It's supposed to get the current hostname, assign it to variable LOCAL_HOSTNAME, get the first occurrence of "1" from hostname and assign value to INDEX_OF, the get the substring from variable LOCAL_HOSTNAME (starting at index 0 through INDEX_OF) and asign it to SERVER_HOSTNAME. 

No matter how much i've tried it keeps throwing Bad substitution error at the substring. I've searched and it says it has to be bash... but it is bash, both the sh script and the running shell.
The LOCAL_HOSTNAME and INDEX_OF variables are ok. Here is the output
I've also tried to get the substring without the INDEX_OF but it gives the same error: SERVER_HOSTNAME=${LOCAL_HOSTNAME:0}

```
host1
5
test.sh: 7: Bad substitution
```

---

### Post by sisco311 on 2011-02-18
Your script should work in bash. Are you running it in another shell. like:
```
sh ./script
```?

Anyway, this should work in both sh (dash) and bash:
```
SERVER_HOSTNAME="${LOCAL_HOSTNAME%%1*}1"
```

---

### Post by kios on 2011-02-18
Thanks for your help. As it turns out... I'm a moron :D I was using sh test.sh instead of bash test.sh

---

