---
title: "Alias to use 'find' won't work"
date: 2011-09-08
forum: General Help
---

### Post by Pithikos on 2011-09-08
I want an alias to search the whole system for any file containing a string. Usually for this task I have to type ```
sudo find / -iname "*something*"
```Now I dug into making an alias but I have a hard time to make it work. This doesn't work:
```
alias f="sudo find \/ -iname '*$1*'"
```Though this will work(but it's not what I want):
```
alias f="sudo find \/ -iname $1"
```My guess is that the argument $1 has it's own apostrophes but then I am not sure on how to get around this :/

---

### Post by sisco311 on 2011-09-08
Aliases cannot take arguments. See: [http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases)

Use a function:
```
f (){
    sudo find / -iname \*"$1"\*
}
```

---

### Post by Pithikos on 2011-09-08
> **sisco311 said:**
> Aliases cannot take arguments. See: [http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases](http://mywiki.wooledge.org/BashGuide/CompoundCommands#Aliases)

Use a function:
```
f (){
    sudo find / -iname \*"$1"\*
}
```

Thanks for the answer. Though if that is true, then how come does this work?:
```
alias a="echo $1" 
```

---

### Post by sisco311 on 2011-09-08
> **Pithikos said:**
> Thanks for the answer. Though if that is true, then how come does this work?:
```
alias a="echo $1" 
```

a is simply replaced by **echo $1** and

$1 is usually unset, but not always:
```

[sisco@acme xtmp]$ echo $1

[sisco@acme xtmp]$ bash -c 'echo $1' 

[sisco@acme xtmp]$ bash -c 'echo $1' foo bar 
bar

```

```
$ alias a='echo $1 foo'
$ a bar
foo bar
```

---

### Post by Wayne_V on 2011-09-08
try "set -x" and then run the commands and then you'll see what is happening.

---

