---
title: "$* not working"
date: 2009-08-26
forum: General Help
---

### Post by m1rjj00 on 2009-08-26
I'm sure that this is something really simple but I'm missing it. In my .bashrc I have a line 
 
alias ll='ls -ls $* | more'
 
unfortunately, the $* is not being handled as I would expect, namely if I input a directory the substitution doesn't happen. I have another line
 
alias vw='view $*'
 
which works perfectly so what the heck am I missing/forgetting?
 
Thanks!!

---

### Post by DaithiF on 2009-08-26
Hi,
bash aliases can't do substitution like this.  they don't take parameters, instead they just do a simple textual substitution.
You need a function instead
```
ll() { ls -ls $* | more }
```your view alias 'seems' to work but not for the reason you think :)
if you type:
```
vw something

```the alias substitution results in:
```
view $* something
```and the shell then expands $* to nothing, leaving your command as
```
view something
```which works!

and just for clarity, to contrast that with the ls example:
you enter:
ll something
alias substitution expands it to:
ls -ls $* | more something
which the shell then expands to:
ls -ls | more something
which would run ls on the current directory, pass the result to more, but since you're also supplying more with an argument it will ignore the piped stdin and instead try to do more on <something>, which will give either give you a listing of a file (if something = a file), or complain that something is a directory if its a directory.

---

