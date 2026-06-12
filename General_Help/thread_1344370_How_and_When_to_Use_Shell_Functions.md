---
title: "How and When to Use Shell Functions"
date: 2009-12-02
forum: General Help
---

### Post by Ubuntist on 2009-12-02
Looking at [FONT=System]man bash[/FONT] to remind myself how to define aliases, I noticed a passage to the effect that shell functions are preferable to aliases for almost all purposes.  The trouble is, I couldn't figure out how to define a shell function.  The man page seems to explain the syntax, but I kept getting error messages when I tried.

So, my questions are:

[LIST=1]
[*]How *do* you define a shell function?  For example, what is the shell-function equivalent of [FONT=System]alias l=ls -F[/FONT] [FONT=Arial]?[/FONT]
[*][FONT=Arial]Why are shell functions better than aliases?
[/FONT]
[/LIST]

---

### Post by amingv on 2009-12-02
1. That would be 'function l { ls -F $1; }'

```
$ function l { ls -F $1; }
$ l Deskt*
DesktopItem1 DesktopItem2 DesktopItemN
```

The basic structure is
```
**function** *<name_of_function>* { command; }
#OR
*<name_of_function>* **()** { command; }
```

The function may span many lines, e.g.:

```
function update { sudo aptitude update; sudo aptitude safe-upgrade; sudo -k }
```

Could be written as:

```
function update {
    sudo aptitude update
    sudo aptitude safe-upgrade
    sudo -k
}

```

2. I wouldn't say they're better, but they have some things that might be useful for shell scripting like declaring local variables, yielding custom return codes and recursion.
Also I think for some shells alias can't handle arguments.
None of these things are generally needed in the scope of what aliases do, so if you just want to create a custom command then an alias is more than enough.

---

### Post by raktarok on 2009-12-02
I am not an expert on shell scipting, but here's how you create a function in a script:
```
#!/bin/bash
l () { ls -F; }
l

```
OR
```
#!/bin/bash
l () { 
  ls -F }
l

```

Note the call ```
l
``` at the end, it executes the commands inside the function. It is behaving like an alias, and if you add the second line of the above sript in .bashrc (like you normally do for aliases), it would work too.

As to the second question, I do not have an exact answer (I have just started learning stuff like these) but from what I have gathered so far, functions are certainly more powerful than aliases. For instance, it can return status (whether the call succeeded or failed). And its easier to incorporate if, while statements or a list of commands in a shell function syntax.(and functions are an elegant way of doing things too, I might add.) I don't know if this is a precise answer, but hope this helped!

Edit: oh I see you already have a better reply!

---

### Post by Ubuntist on 2009-12-03
Thank you both.  I see now why I couldn't define a shell function earlier: I had omitted the semicolon and did not place spaces before and after the braces.

---

