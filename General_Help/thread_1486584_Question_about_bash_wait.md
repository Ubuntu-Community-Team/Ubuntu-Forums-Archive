---
title: "Question about bash wait"
date: 2010-05-18
forum: General Help
---

### Post by elliottb on 2010-05-18
Hi,

This may be a super easy question.  I can't seem to find an answer.  I know bash's built in wait takes can take a list of pid's and will wait until all are done.  But what if you wanted to take a list of pid's and wait until the first of them finished.  Is that possible?  I know I could do this with some kind of sleep/while loop combination (and that's probably what I'll end up doing), but I guess I don't understand wait really well, so I thought I'd throw this out.

Sorry for the boring post!

Elliott

---

### Post by rnerwein on 2010-05-18
hi
try this:
#!/bin/bash
set -mb  #   SIGCHLD will be handeled by trap
trap "echo huuuuuuuuuuuuuuuuuch;set -mb; exec ./z" SIGCHLD # will execute z when the [COLOR=Blue]first[/COLOR] child exit 
./x 5&  # sleep 5 seconds
./x 6&  # sleep 6 seconds
wait
echo "first is done" # never reached - own shell is overlayed.

have fun
ciao

---

### Post by elliottb on 2010-05-18
Dude,

Thanks.  That will probably fix it.

---

