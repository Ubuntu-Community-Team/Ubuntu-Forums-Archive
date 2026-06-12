---
title: "what does -z mean?"
date: 2009-10-23
forum: General Help
---

### Post by dandeliondream on 2009-10-23
Hi,

I saw this statement

if [ ! -z "$1"]

or 

if [ -z "$findStr" ] 

what does -z mean?

It is possible to search -z in the manual? i've tried $ man -z but yields no result.

---

### Post by Bachstelze on 2009-10-23
```
test -z "$string"
```

Will return true if $string is empty, and false otherwise.

```
[ -z "$tring" ]
```

is a synonym for it.

[http://linuxcommand.org/wss0090.php#test](http://linuxcommand.org/wss0090.php#test)

---

### Post by dandeliondream on 2009-10-23
> **dandeliondream said:**
> Hi,

I saw this statement

if [ ! -z "$1"]

or 

if [ -z "$findStr" ] 

what does -z mean?

It is possible to search -z in the manual? i've tried $ man -z but yields no result.

> **Bachstelze said:**
> ```
test -z "$string"
```Will return true if $string is empty, and false otherwise.

```
[ -z "$tring" ]
```is a synonym for it.

[http://linuxcommand.org/wss0090.php#test](http://linuxcommand.org/wss0090.php#test)

thank you for the explanation! :popcorn:

---

