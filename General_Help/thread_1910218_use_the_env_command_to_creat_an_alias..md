---
title: "use the env command to creat an alias."
date: 2012-01-16
forum: General Help
---

### Post by conradin on 2012-01-16
Hi All,
Im in a linux class and Im stuck on a problem:
Using the env command, create an alias for grep that runs grep in a
modified environment. For the modified environment, create a new environment variable named
GREP_OPTIONS that has a value of --color. For your answer, give the command.

Im not trying to cheat, I just dont know how to do it, normally when I create an alias I use the alias command or just edit the .bashrc file. Ive had a look online, and in some books and I just cant figure it out. 

I tried editing env by appending, it with ```
echo GREP_OPTIONS=--color >> env
``` but that did nothing. Can anyone give me some pointers?

---

### Post by conradin on 2012-01-16
Ok So I think I got it, But Im not sure if this counts as an alias.
```

GREP_OPTIONS='grep --color=always'
export GREP_OPTIONS

```
Then to test it, I used my home directory, with the list command:
```

ls -a | GREP_OPTIONS me

```
and I got all the strings including the set "me" in them. 
Then I checked env to verify my modified environment.
```
env | sort | less 
```
There I saw the environmental variable I created. So this works like an alias, but doesn't show up if I use the alias command.

---

### Post by Serpher on 2012-01-16
Student to student, RTFM:

[http://www.lmgtfy.com/?q=linux+env+tutorial](http://www.lmgtfy.com/?q=linux+env+tutorial)

---

### Post by conradin on 2012-01-17
yeah thanks bud, but despite reading multiple articles I still dont get it. 
my conclusion is that env wasnt made for bash. in tcsh, 
```
alias grep env GREP_OPTIONS=--color grep
```
That code works. but the syntax confuses me, and in bash, I cant seem to make it work. So if someone can explain that to me, I would be elated. Or if someone has some can explain this operation in bash, that would be great.

---

### Post by sisco311 on 2012-01-17
The syntax of the alias builtin command in Bash is:
```
alias [-p] [name[=value] ... ]
```

For example:
```
alias ls='ls --color'

```

BASH checks the first word of every simple command to see whether it's an alias, and if so, it does a simple text replacement. Thus, if you type:
```
ls /tmp
```
BASH acts as though you had typed:
```
ls --color=auto /tmp
```

---

