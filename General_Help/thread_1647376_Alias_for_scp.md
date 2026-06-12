---
title: "Alias for scp?"
date: 2010-12-17
forum: General Help
---

### Post by Tiit_Helimut on 2010-12-17
I know this is a relatively simple problem but no matter what combination I try for my alias, I don't seem to be able to get it right!

All I want to do is scp a file from my current folder to a location on the network:

```
scp filename username@computername:/folder1/folder2
```This is the usual layout of the command that I use, so I thought that to save time, I would create an alias or even a function which did this for me, so all I had to type was
```
scp101 filename
``` and it would copy it to the set folder on the remote computer...

My attempt at an alias looks like:

```
alias scp101='scp !* username@computername:/folder1/folder2'
```and I have also attempted a function:

```
scp101()
{
    scp "$1" username@computername:/folder1/folder2
}

```The alias tells me that filename is not a directory, which I assume means that I have some of the syntax wrong in the alias but I did a google search and I can't seem to find a decent example of what I'm trying to do. When I load up a terminal, I get an error message about the "(" of the scp101 function - so I've obviously can't get the syntax of that right either...

Could anyone help correct my alias or function?

Thanks!

---

### Post by Tiit_Helimut on 2010-12-17
Never mind. I seem to have found the root of the problem.

It wasn't liking the numbers in the alias scp101 for some reason. No guide I have read seems to point this out.

Does anyone know why numbers in an alias cause Ubuntu to throw a wobbler?

Thanks!

---

### Post by gmargo on 2010-12-17
Your alias syntax is invalid.  No substitutions are allowed in **bash** shell aliases. (The asterick probably gets expanded, but not substituted as you expect.)

Try this function syntax.  Changed your $1 to $@, so you can specify multiple files, and added trailing slash to make sure destination is interpreted as a directory, and added -p since you should always use -p to maintain the permissions and modification time:
```

scp101()
{
    scp -p "$@" username@computername:/folder1/folder2/
}

```And there's nothing wrong with numbers in an alias name.  This works just fine:
```

alias ls101='ls -l'

```

---

