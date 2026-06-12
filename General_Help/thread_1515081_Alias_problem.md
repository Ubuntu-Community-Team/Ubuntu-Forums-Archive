---
title: "Alias problem"
date: 2010-06-21
forum: General Help
---

### Post by luigi_mb on 2010-06-21
I want to add the following alias in ~/.bashrc

```

alias foldoc='grep -A 20 -i "^$1" foldoc-dictionary.txt'

```

However when calling

```

foldoc usb

```

grep displays the entire file, not the 20 lines of context around "usb" entries.  I must be overlooking some silly detail, but which?

Thank you for your help.

/luigi

---

### Post by sisco311 on 2010-06-22
Write a function:
```
function foldoc ()
{
  grep -A 20 -i "^$1" foldoc-dictionary.txt
}

```

[http://tldp.org/LDP/abs/html/aliases.html](http://tldp.org/LDP/abs/html/aliases.html)
[http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

---

### Post by Ryan Dwyer on 2010-06-22
Yeah, aliases are basically a string replace and don't use variables like $1.

When you run foldoc usb it's actually running this:
grep -A 20 -i "^$1" foldoc-dictionary.txt usb

---

### Post by luigi_mb on 2010-06-22
> **sisco311 said:**
> Write a function:
```
function foldoc ()
{
  grep -A 20 -i "^$1" foldoc-dictionary.txt
}

```

[http://tldp.org/LDP/abs/html/aliases.html](http://tldp.org/LDP/abs/html/aliases.html)
[http://tldp.org/LDP/abs/html/functions.html](http://tldp.org/LDP/abs/html/functions.html)

Good solution, thank you! Thank you also for the references to ABS, which I know, but in this case didn't help. 

I am still curious why my alias 

```

alias='grep -A 20 -i "^$1" foldoc-dictionary.txt'

```

does not quite work as expected. 

/luigi

---

### Post by Ryan Dwyer on 2010-06-22
I explained it above.

---

### Post by luigi_mb on 2010-06-22
> **Ryan Dwyer said:**
> Yeah, aliases are basically a string replace and don't use variables like $1.

When you run foldoc usb it's actually running this:
grep -A 20 -i "^$1" foldoc-dictionary.txt usb

Yes, that's what seems to be happening. 

However, how about this?

```

alias untart='tar tvf $1 | less'

```

I use it all the time, and it works:

```

untart file.tgz

```

/luigi

---

