---
title: "Bash history keeps duplicates across sessions"
date: 2010-03-28
forum: General Help
---

### Post by ngmachado on 2010-03-28
Hello all,

For the past two hours I've tried every combination of HISTCONTROL and shopt possible... at no avail:

Settings in the .bashr file:
```

export HISTCONTROL=erasedups:ignoreboth
export HISTSIZE=10000
shopt -s histappend

```

Problem:

```

##### bash session A starts
$> echo 1
$> echo 2
$> echo 1
##### bash session A quits

```

After session A, the bash_history will look like:
```

echo 2
echo 1

```

(Good, erasedups is working!)

```

##### bash session B starts
$> echo 1
$> echo 2
$> echo 1
##### bash session B quits

```

After session B, the bash_history will look like:
```

echo 2
echo 1
echo 2
echo 1

```

(Damn... bash_history has duplicates!!)


Any pointers on how to solve this?

Thank you.

---

### Post by ngmachado on 2010-03-28
No one has any hints on this?

Thanks a lot.

---

