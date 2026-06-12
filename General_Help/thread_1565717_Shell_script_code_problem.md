---
title: "Shell script code problem"
date: 2010-09-01
forum: General Help
---

### Post by snyderm on 2010-09-01
Hello all, I am trying to make a simple shell script that will establish an FTP download every set amount of time.  At this point it is just an academic exercise, but It is bugging me that it doesn't work and I don't know why.
---------------------------------------------------------
#!/bin/bash
HOST="blah.blah.com"
PORT='21'
PASSWD="blah"
USER="blah"
FILE='wtt.csv'

while [ 0 -eq 0]
do
    
    ftp -n $HOST $PORT << END_SCRIPT
    quote USER $USER
    quote PASS $PASSWD
    cd /public_html
    get $FILE
    quit
    END_SCRIPT

    sleep 100

done


---------------------------------------------------------

when I run this, it says "end of file unexpected".
If I comment out the while loop, the ftp transaction works.  If I comment out the ftp transaction, the while loop works.  When I put them both together, however, I get the above message.

Can anyone see why this isn't working?

---

### Post by wesleybailey on 2010-09-01
I tried your script, and I think the problem might be a missing space in your while loop

i.e
doesn't work
```
while [ 0 -eq 0]
```

works
```
while [ 0 -eq 0 ]
```

Latest tutorial: How to [convert uif to iso]("http://wesleybailey.com/articles/uif-to-iso-converter") with Linux or Windows

---

### Post by snyderm on 2010-09-01
I don't think it is that...

Making the change you suggested doesnt make any difference.  I can substitute something different instead of the FTP connection, and the while loop operates normally.  It is only the while loop when combined with the ftp connection that gives me a problem.  Either one by themselves doesn't oddly.

---

