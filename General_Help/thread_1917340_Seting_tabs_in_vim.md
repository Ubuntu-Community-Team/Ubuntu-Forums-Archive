---
title: "Seting tabs in vim"
date: 2012-01-29
forum: General Help
---

### Post by conradin on 2012-01-29
hi All, 
I want to set the tabs in a file where I know the line numbers.
I think the command should go something like this:
```
:s/lineNumber/^I
```
but I dont know how to specify the actual line number.

---

### Post by TeoBigusGeekus on 2012-01-30
If you mean adding a tab at the beginning of a specific line, say line 5, try with this:
```
:5s/^/\t
```
Sorry if that's not what you wanted.

---

### Post by conradin on 2012-01-30
Yes, that is what Im talking about.
But how to I do a range of numbers?
I tried:

```
:[0-9]s/^/\t
```
but that gave me an error.
Any ideas?

---

### Post by TeoBigusGeekus on 2012-01-30
> **conradin said:**
> Yes, that is what Im talking about.
But how to I do a range of numbers?
I tried:

```
:[0-9]s/^/\t
```
but that gave me an error.
Any ideas?

```
:0,9s/^/\t
```

---

### Post by conradin on 2012-01-30
woot! I just got it on my own, and at the same conclusion!
Thanks TeoBigusGeekus!!!! I really appreciate the help!:KS

---

### Post by TeoBigusGeekus on 2012-01-30
You're welcome mate; don't forget to mark the thread as solved.

---

