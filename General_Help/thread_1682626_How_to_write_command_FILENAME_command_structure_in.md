---
title: "How to write command FILENAME command structure in bash"
date: 2011-02-06
forum: General Help
---

### Post by whatthefunk on 2011-02-06
How do you write code to make your own shell command that has the form
```
command FILENAME
```For example, find has this structure
```
find FILENAME
```

---

### Post by Stephen Morgan on 2011-02-06
You could write a shell-script to do it, or put a function or alias in your ~/.bashrc, which one you use depedns on what you need it to do and your preferences.  Say you wanted to read the contents of a file and use the less pager, you could put:  ```
 contents () { cat $1 | less } 
``` in ~/.bashrc, the $1 being the variable for the first argument passed to the command. A script would be similar, but I don't think aliases can use arguments. With the above example typing contents FILENAME into bash would page the content for you.

---

### Post by whatthefunk on 2011-02-06
> **Stephen Morgan said:**
> You could write a shell-script to do it, or put a function or alias in your ~/.bashrc, which one you use depedns on what you need it to do and your preferences.  Say you wanted to read the contents of a file and use the less pager, you could put:  ```
 contents () { cat $1 | less } 
``` in ~/.bashrc, the $1 being the variable for the first argument passed to the command. A script would be similar, but I don't think aliases can use arguments. With the above example typing contents FILENAME into bash would page the content for you.

Thanks for the reply!  So if I wanted to use a command to move a named file to a specific directory, how would I do that?  I played around with your structure a bit but keep getting unexpected end errors.

---

### Post by Vaphell on 2011-02-06
alias is a simple text substitution
let's say you have an alias
grep='grep --color'
when you run the command ```
grep 'pattern' *
```
grep from your input is replaced by grep --color so in reality the following is executed
```
**grep --color** 'pattern' *
```

you can say that in some cases alias is sort of able to use parameters - but only when the executed command accepts them at the end. In any other case where the parameter needs to do something in the middle of the executed code, shell function/script located in the dir that is in PATH variable is the way to go.

edit:
you need something like
```
movefile PARAMETER(s)
```
where destination folder is set in stone?

```
movefile() { mv -t "/some/destination/dir/" "$@" }
```
or with alias
```
alias movefile='mv -t /some/destination/dir/'
```

---

