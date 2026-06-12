---
title: "Terminal question"
date: 2009-12-01
forum: General Help
---

### Post by skipsbro on 2009-12-01
I'm making an evil router with openWRT. Is there a way I change change what the error messages say? For example, if I try to run a command that doesn't exist, can I make my router return: 

```
"I'm sorry \u, I'm afraid I can't do that"
```

instead of the usual :

```
-bash: blah: command not found
```

---

### Post by Megafag on 2009-12-01
> **skipsbro said:**
> I'm making an evil router with openWRT. Is there a way I change change what the error messages say? For example, if I try to run a command that doesn't exist, can I make my router return: 

```
"I'm sorry \u, I'm afraid I can't do that"
```instead of the usual :

```
-bash: blah: command not found
```

That made me laugh

sadly i dont know how to do such a thing.

---

### Post by mo.reina on 2009-12-01
```
exec 2> >(while read line; do echo "blah blah blah"; done)
```

---

