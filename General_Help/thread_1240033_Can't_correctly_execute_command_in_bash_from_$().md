---
title: "Can't correctly execute command in bash from $()"
date: 2009-08-14
forum: General Help
---

### Post by itmozart on 2009-08-14
I'm trying to execute a command in bash, using a variable, but couldn't manage to do it.

The command is:

**mysql  -e "SHOW SLAVE STATUS\\G"**

So I type:

**kmd='mysql  -e "SHOW SLAVE STATUS\\G"'**

But then I run:

**$(kmd)**

I get the mysql help.
When I try to run a command like 'echo "pizza"', everything works fine.

Why is this happening?

Thanks

---

### Post by Brandon Williams on 2009-08-15
You want:
```
$(eval $kmd)
```
The '$' is required to get variable substitution and eval is required to get the shell to interpret the embedded quotes.

---

