---
title: "suppress stderr in a bash script"
date: 2010-01-02
forum: General Help
---

### Post by Andreas1 on 2010-01-02
hi,

i have a bash script that in some cases will print out error messages from various commands like ls, grep, head, tail. currently i see the following options:

-supplement each single one of those commands with "2>/dev/null"       <--doing that currently
-tell the people who use the script to invoke it with "2>/dev/null"
-build (otherwise unnecessary) tests for files and directories to prevent errors
-have confusing error messages printed to the user

but i was wondering if there was some kind of global setting for that, to the same effect as invoking the script itself with "2>/dev/null", maybe like a silent argument in the "#!/bin/bash" line or something? hope i am making sense...

---

### Post by shylent on 2010-01-02
If you really think, that the errors are going to be confusing to the users, then you shall use tests before calling external commands to prevent errors.

Otherwise, let the users see the errors.

Anyway, from what I've observed (in the scripts, that are a part of the system, like the initscripts), the common practice is to test before calling, unless it is desired to show the possible stderr output to the user.

---

### Post by buschi on 2010-01-02
i agree that supressing all errors by default is not the best way to go; something like
```

#!/usr/bin/env bash

func ()
{
    ls thisfiledoesnotexist
}

coproc func 2> /dev/null

```
should work though.

---

### Post by John Bean on 2010-01-02
An easy kludge to make the redirect of stdout global to the script is to turn the whole script into a conditional that's always true and redirect the conditional block. Something like this:

```
#!/bin/bash

if [ true ] ; then

# script goes here:

echo hello world
ls nofile
 
# end if-block and redirect:
fi 2>/dev/null

```

---

### Post by buschi on 2010-01-02
> **John Bean said:**
> ... redirect the conditional block.

that's a nice idea! you even don't need a conditional; just a block, i think:

```

{
    ls strangefile
} 2> /dev/null

```

---

### Post by John Bean on 2010-01-02
> **buschi said:**
> that's a nice idea! you even don't need a conditional; just a block, i think

Absolutely; a block is a block is a block... 

I'm so used to using "if [ true/false ]"  for execution control while debugging I used it here purely from habit ;-)

---

### Post by rnerwein on 2010-01-02
hi - try this
#!/bin/bash
if [ ! $MY_DEBUG ]  # if not set -> every time true :-)
then
exec 2>/dev/null      # true for the whole script
fi
ls file_does_not_exist  # no output if MY_DEBUG is not set
ls file_exists               # output
exit 0
call your script "./my_script" will cause no output on stderr
call your script "MY_DEBUG=1 ./my_script" will cause error output on /dev/tty
MY_DEBUG=1 is set in front of your script means that the value is pased to your shell but not exported (i think that's useful).
if you want your stderr output back on any place insert: exec 2>/dev/tty  
ciao

---

