---
title: "SHA hashing program"
date: 2012-01-29
forum: General Help
---

### Post by Tony1337 on 2012-01-29
Is there a package that gives you a command-line interface to easily hash a string? For example, something like

sha "hello world"

should output the SHA hash of "hello world". I'm not looking for one that takes a filename as an argument and hashes the entire file; all I want to do is just hash a string.

---

### Post by conradin on 2012-01-29
type sha 
then tab at the command line.
you should see a whole bunch show up. like:
sha1sum  
sha256sum 
sha512sum 
shasum    
sha224sum
sha384sum 
shadow  
sharesec

---

### Post by Sazhen86 on 2012-01-30
Most of those programs will read from standard input if no file is specified so you could use:

echo "Hello World" | sha256sum

to get the result you want.

Hope that helps.

---

### Post by amauk on 2012-01-30
Just FYI
echoing stuff into a hashing program takes care

echo by default adds a newline character to the end of the string
use the -n switch to turn off the trailing newline

```
echo -n "some string" | sha1sum
```

This is especially useful if you're manually updating a password hash field in a database, for example

---

### Post by Sazhen86 on 2012-01-30
Hi

A very good point!  Thanks for pointing it out.

---

