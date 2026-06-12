---
title: "Executing the result of a command"
date: 2009-07-10
forum: General Help
---

### Post by PsyCowboy on 2009-07-10
I'm not sure to post in the right place...

I was wondering if somebody knows a simple way to execute the output of a command; something like:[INDENT]*echo ls |* *command*
[/INDENT]

---

### Post by sisco311 on 2009-07-10
Hi and welcome to the forums!


Command substitution allows the output of a command to replace the command name.  There are two forms:

```
`echo ls`
$(echo ls)
```

for more info read the man page:
```
man bash
```

---

### Post by PsyCowboy on 2009-07-10
Thanks a lot for this quick and sympathetic answer.

What you said to me works well but still don't do exactly what I expect because this don't work well with several pipelined commands. Let say I create several commands to execute by using some pipelined commands, something like:

[INDENT][I]fgrep KEYWORD */*.cc | sed -e \'s/cc:.*$/o;/;s/^.*\//rm build\/debug\//\' | uniq
[/I][/INDENT]
this returns something like that:

[INDENT]*rm build/debug/Application.o;*
*rm build/debug/World.o;*
*...*
[/INDENT]Your answer suggest to add a ` prefix and suffix, but this don't work in my case.
How can I execute directly this output without passing into a file?

PS: my life don't depend on the answer, but I was just wondering if this is possible or not...

---

### Post by sisco311 on 2009-07-10
try something like:
```
fgrep KEYWORD */*.cc | sed -e \'s/cc:.*$/o;/;s/^.*\//build\/debug\//\' | uniq | xargs -0 -d '\n' rm
```

---

### Post by geirha on 2009-07-10
Here's one that should be safe with regards to special characters in pathnames. It also recurses through all subdirectories
```

find . -type f -name "*.cc" -exec grep -q KEYWORD {} \; -exec bash -c 'rm -v "${@/%.cc/.o}"' _ {} +

```

---

### Post by PsyCowboy on 2009-07-10
Wow, xargs is exactly what I'm looking for! A new command to add in my vocabulary!

Thanks a lot,
I really appreciated your help!

---

### Post by t4thfavor on 2009-07-10
God I wish I was better at this stuff, I have been trying to get a better handle on these types of commands for a while, and now that there are more people trying to write code under Ubuntu there seems to be more of these types of questions.

Im thinking of a new forum category for noob (linux) programmers. I know the people on the real developers forum would answer these questions, but they would do it while laughing (silently) at you. We need a place to post really basic questions without bothering people who have real problems to work out.

General is a great place to post these now, as it is fairly active, and has alot of intelligent folks willing to help. 

What do you all think? 

Noob Developers Forum?

or 

Keep it the same as it is now?

---

