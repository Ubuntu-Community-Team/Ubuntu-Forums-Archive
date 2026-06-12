---
title: "What is wrong with this script?"
date: 2011-02-07
forum: General Help
---

### Post by reddogut on 2011-02-07
Below is my shell script

```
#!/bin/bash                                                                                                                                                                                                                                   

# Report disc space usage script                                                                                                                                                                                               
if [ $# -lt 1 ]
then
    echo "You must pass at least one username to the $0 script."
    exit
fi

cd /home/$1

SPACE='du -s'

echo "$1 is using $SPACE of drive space."
```When I enter

./scriptname.sh username

it returns 

username is using du -s of drive space

I am running Ubuntu Server 10.10

---

### Post by gmargo on 2011-02-07
To do command substitution, use $() or backticks:
```

SPACE=$(du -s)
SPACE=`du -s`

```

---

### Post by reddogut on 2011-02-07
Thank you!

---

### Post by Habitual on 2011-02-07
I am a dork. 

n/m this reply. :)

---

