---
title: "man export - no man pages, how come?"
date: 2009-10-10
forum: General Help
---

### Post by jzacsh on 2009-10-10
hello,

why are there no man pages for export in Ubuntu? maybe there are, and turned off or something? specifically, how come I get this result:
```
/home/jzacsh$ man export
No manual entry for export

```

yet here's proof there *is* indeed a man page for it:
[http://public.research.att.com/~gsf/man/man1/export.html](http://public.research.att.com/~gsf/man/man1/export.html)

just curious :) wondering if there's a specific reason (couldn't find it even googling: site:ubuntuforums.org "man export").

---

### Post by delcypher on 2009-10-10
Export is a shell builtin (i.e. it's part of the shell - bash) therefore it has no man page.

To find info on the bash command export run
```
help export
```

To find out if a program is shell builtin or a standalone program run
```
type export
```

```
type tar
```
If you've not run tar before in the current shell it will just give it's location, if it has run tar before it will tell you it's hashed (not sure what that means)

Hope that helps

---

### Post by jzacsh on 2009-10-10
> **delcypher said:**
> Export is a shell builtin (i.e. it's part of the shell - bash) therefore it has no man page.

To find info on the bash command export run
```
help export
```

To find out if a program is shell builtin or a standalone program run
```
type export
```

```
type tar
```
If you've not run tar before in the current shell it will just give it's location, if it has run tar before it will tell you it's hashed (not sure what that means)

Hope that helps

Hey, thanks for the reply. I had indeed done a 'type export' and found out it was a shell builtin. but if you 'type echo', you'll see its also a shell builtin, yet it has a man page. why is that?

is the reason 'man export' brings back nothing, because: shell builtins don't have man pages? (*I just googled it, finding a few results saying yes*)
-if so, how come echo brings one back?

---this isn't urgent, just curious.

---

### Post by delcypher on 2009-10-10
I'm afraid I have no idea about that. You'll need to ask someone who knows more about the man pages than I do.

---

### Post by diesch on 2009-10-10
The manpage for echo belongs to /bin/echo, not the bash builtin echo

---

### Post by louieb on 2009-10-10
A search of [Linux Man Pages]("http://www.linuxmanpages.com/") for export shows no separate man page. 
What i could find was found by 
```
man bash-builtins
```

And one las bit of trivia:  I use zsh for my shell and the command **help export** gives zsh: command not found: help

> ---this isn't urgent, just curious. 	
guess I got to much time on my hands today too.

---

### Post by diesch on 2009-10-10
> **louieb said:**
> And one las bit of trivia:  I use zsh for my shell and the command **help export** gives zsh: command not found: help


help is a bash builtin. In zsh you can use run-help or <ESC> h to display the corresponding  manpage.

---

