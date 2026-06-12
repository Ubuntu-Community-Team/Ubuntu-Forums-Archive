---
title: "awk and counting"
date: 2010-10-20
forum: General Help
---

### Post by SpinningAround on 2010-10-20
I'm working on a bash script and now I want to check the number of rules that match 'eth0'. I tried working with a simple variable but I get 6 as result even if there is only one rule that match.

```
sudo ufw status numbered | sed 's/]/ ]/' | awk '/eth0/ {print $2}{count++}END{print "abc " count}'

```
Result
```
1
abc 6
```

---

### Post by gmargo on 2010-10-20
The segment {count++} is an action for the default null pattern, so you count the six lines of input.

Change "{print $2}{count++}" to "{print $2; count++}".

---

### Post by SpinningAround on 2010-10-20
> **gmargo said:**
> The segment {count++} is an action for the default null pattern, so you count the six lines of input.

Change "{print $2}{count++}" to "{print $2; count++}".

Solved it :)

---

