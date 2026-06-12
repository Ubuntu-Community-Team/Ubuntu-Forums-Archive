---
title: "embedded commands in bash"
date: 2010-04-07
forum: General Help
---

### Post by edpatterson on 2010-04-07
I would like to be able to connect to a machine, list a directory, wait long enough for me to see the results then move on to the next machine.
This is failing:
```

#!/bin/bash
while read line; do
  if [ "$line" != "" ]; then
    ssh $line
    ls -l /etc/squid/lists
    sleep 5
  fi
done < "./machines.txt"

```
I had previously use ssh-copy-id and tested the passwordless (is that a word) connections. /etc/squid/lists is world readable.

I receive -bash: line 1: <machinename>: command not found for each machine in the list. I have tried enclosing in backtics and parins, same result.
I am assuming that the newly opened shell on the remote machine has no way of getting the commands from the calling one. Am I close?

Thanks,
Ed

---

### Post by spibou on 2010-04-07
> **edpatterson said:**
> I would like to be able to connect to a machine, list a directory, wait long enough for me to see the results then move on to the next machine.
This is failing:
```

#!/bin/bash
while read line; do
  if [ "$line" != "" ]; then
    ssh $line
    ls -l /etc/squid/lists
    sleep 5
  fi
done < "./machines.txt"

```
I had previously use ssh-copy-id and tested the passwordless (is that a word) connections. /etc/squid/lists is world readable.

I receive -bash: line 1: <machinename>: command not found for each machine in the list. I have tried enclosing in backtics and parins, same result.
I am assuming that the newly opened shell on the remote machine has no way of getting the commands from the calling one. Am I close?

No you're not close. The shell on the remote machine does have a way to get a command. The general syntax is```
ssh machine command
``` so in your case```
ssh "$line" ls -l /etc/squid/lists
```I don't think you need to put the **ls...** within quotes but you can try it if not using quotes doesn't work.

---

### Post by finite9 on 2010-04-08
```
ssh server "ls -l"
```

works fine for me.

---

### Post by deracled on 2010-04-08
An alternative would be to use **parallel-ssh**, it takes care of the ugly corners of running scripts inside an ssh connection.

Doros

---

