---
title: "renicing script with PS and AWK commands"
date: 2010-03-18
forum: General Help
---

### Post by pczafer on 2010-03-18
Trying to get the script to identify the <PID> if it is fed with a process name only and do the renicing for a given nice number.

i know its simple but couldn't get it the worked. need to do this with ps and awk commands. thanks in advance

---

### Post by DaithiF on 2010-03-19
Hi, something like:
```
pid=$(ps -ef | grep <processname> | grep -v grep | awk '{print $2}')
renice -n <priority> -p $pid

```

---

### Post by pczafer on 2010-03-21
i want to script works for Any Given process name and change thet process priority with Givin nice number.
<Process name> <Priority>
??

---

### Post by geirha on 2010-03-21
Here's something you can build on. Using pgrep to get the pids.
```

#!/bin/bash

if (($# != 2)); then    # if number of args is not 2
    echo "Usage: ${0##*/} NAME PRI" >&2
    exit 1
fi

if ! pids=( $(pgrep "$1") ); then
    echo "No processes matching '$1' found" >&2
    exit 2
fi

for i in "${!pids[@]}"; do
    read -n1 -p "Renice '$(ps -ocmd= -p "${pids[i]}")' with pid ${pids[i]} to priority $2? [yN] "
    echo
    if [[ $REPLY != [yY] ]]; then
        unset "pids[i]"
    fi
done

if (( ${#pids[@]} > 0 )); then
    renice "$2" "${pids[@]}"
fi

```

---

### Post by pczafer on 2010-03-21
trying to meke very simple.

ps -ef | grep $1 | grep -v grep | awk '{print $2} | xargs renice $2

this script finding and renicing the process with given name but not renicing to givin nice number?
its always renicing to '0'

what im doing wrong??????

---

### Post by pczafer on 2010-03-23
nobody want to help??

---

### Post by geirha on 2010-03-23
ps -ef gives human-readable output. Not really meant to be parsed. That's why there's pgrep.
```
renice "$2" $(pgrep "$1")
```

---

### Post by pczafer on 2010-03-30
> **geirha said:**
> ps -ef gives human-readable output. Not really meant to be parsed. That's why there's pgrep.
```
renice "$2" $(pgrep "$1")
```

This command did not worked for me i even tried with pidof command but still not workin. its saying changed but not changing anything???????????????????????????????????

---

