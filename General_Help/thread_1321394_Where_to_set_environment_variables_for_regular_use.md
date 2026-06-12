---
title: "Where to set environment variables for regular user?"
date: 2009-11-10
forum: General Help
---

### Post by LordKelvan on 2009-11-10
Hi:

I've been setting environment variables in the file /etc/environment, which has worked fine.  However, I'd like to stop doing this because I'd like to have all of my settings in my home directory.  

[LIST=1]
[*]Which file (in my home directory) should I set my environment variables in so that they get set whenever I log in?  I presume that the value of a particular environment variable set in my home directory overrides the value set in /etc/environment.  For example, if I set A="foo", would this override A="bar" in /etc/environment?
[*]In the file for the above question, how would I modify an existing environment variable?  For example, how would I append paths to the $PATH variable?
[/LIST]

Thanks,
LK

---

### Post by jocko on 2009-11-10
> **LordKelvan said:**
> Hi:

I've been setting environment variables in the file /etc/environment, which has worked fine.  However, I'd like to stop doing this because I'd like to have all of my settings in my home directory.  

[LIST=1]
[*]Which file (in my home directory) should I set my environment variables in so that they get set whenever I log in?  I presume that the value of a particular environment variable set in my home directory overrides the value set in /etc/environment.  For example, if I set A="foo", would this override A="bar" in /etc/environment?
[*]In the file for the above question, how would I modify an existing environment variable?  For example, how would I append paths to the $PATH variable?
[/LIST]

Thanks,
LK
You can add paths in your ~/.bashrc
```
gedit ~/.bashrc
```If you want to include ~/.bin in your path, add this to the end:
```
if [ -d ~/.bin ]; then
    PATH=~/.bin:"${PATH}"
fi
```You can also add aliases, either directly in ~/.bashrc or in ~/.bash_aliases:
```
alias A='foo'
```I'm pretty sure those aliases set in your ~/.bashrc or ./bash_aliases will override any aliases set anywhere else.

To apply the changes without logging out:
```
source ~.bashrc
```

---

### Post by LordKelvan on 2009-11-10
Sorry, I should have been more clear that 
```

A="foo"

```
was setting the environment variable A to "foo", and not setting up an alias.  

To confirm, I only need to edit ~/.bashrc.  If I wanted to set an environment variable, I would add:
```

A="foo"

```

If I want to append something to an existing environment variable, I would add (omitting the checking code):
```

A="${foo}":/path/to/somewhere 

```

Can I set it anywhere inside ~/.bashrc, or is there a specific place?

One final thing: does Ubuntu first read /etc/environment for system-wide environment variables, and then read ~/.bashrc for user-specific environment variables (i.e., my changes will not be clobbered)?

---

### Post by jocko on 2009-11-10
> **LordKelvan said:**
> Sorry, I should have been more clear that 
```

A="foo"

```was setting the environment variable A to "foo", and not setting up an alias.  

To confirm, I only need to edit ~/.bashrc.  If I wanted to set an environment variable, I would add:
```

A="foo"

```If I want to append something to an existing environment variable, I would add (omitting the checking code):
```

A="${foo}":/path/to/somewhere 

```Can I set it anywhere inside ~/.bashrc, or is there a specific place?

One final thing: does Ubuntu first read /etc/environment for system-wide environment variables, and then read ~/.bashrc for user-specific environment variables (i.e., my changes will not be clobbered)?
Well... if I make the line:```
A="foo"
```at the end of my ~/.bashrc, typing $A in the terminal gives me```
No command 'foo' found, did you mean:
 Command 'xoo' from package 'xoo' (universe)
 Command 'fop' from package 'fop' (universe)
 Command 'fox' from package 'objcryst-fox' (universe)
 Command 'zoo' from package 'zoo' (universe)
 Command 'goo' from package 'goo' (universe)
foo: command not found
```so it seems it works as you want it to.
I don't think it matters where you place it.
bashrc is read when you log in, so any variables in there should replace any variables that were set during boot.

---

