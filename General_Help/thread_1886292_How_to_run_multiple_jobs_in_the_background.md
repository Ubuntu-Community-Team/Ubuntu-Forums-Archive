---
title: "How to run multiple jobs in the background?"
date: 2011-11-24
forum: General Help
---

### Post by AncientPC on 2011-11-24
So, you can run a program in the background using `./binary &`.  However, this prevents you from chaining commands such as `./binary &; ./app`.  Is there a way to run multiple commands in the background?

---

### Post by alquery on 2011-11-24
On [http://stackoverflow.com/questions/161252/bash-start-multiple-chained-commands-in-background]("http://stackoverflow.com/questions/161252/bash-start-multiple-chained-commands-in-background"), it says you can do:

```
for command in $commands
do
    command &
done
```

It's not the answer to the question that was asked there, but it should do for you.

---

### Post by frostyfrog2 on 2011-11-24
> **AncientPC said:**
> So, you can run a program in the background using `./binary &`.  However, this prevents you from chaining commands such as `./binary &; ./app`.  Is there a way to run multiple commands in the background?

./binary & ./app &

That should work :D

Edit: heh, alquery you beat me. :) Anyways, both commands should work, although I would suggest turning alquery's suggestion into a script like this:
```

#!/bin/bash
for command in "$@"
do
    command &
done

```

---

### Post by AncientPC on 2011-11-24
Thanks to both replies.  Looking to stay away from using a for loop since I just want to chain a few commands working in terminal.  I was stuck trying different combinations of ; && and || with &.

---

