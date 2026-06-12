---
title: "history command"
date: 2012-08-23
forum: General Help
---

### Post by IAMTubby on 2012-08-23
Hi,
I wrote this to write the output of the history command to a file. But it works for a lot commands except history.


#include<stdio.h>
#include<stdlib.h>

int main(void)
{
 system("history > HistoryLog.txt");

 return 0;
}

It creates a file, but the output is blank. When I replace history with ls or uname -r, it works.


PS : matt_symes , if you are reading this, I tried posting in the programming section. But I couldn't.

---

### Post by lechien73 on 2012-08-23
As far as I know, the history command is only accessible from the command line. It's disabled in scripting by default.

> Unfortunately, the Bash history tools find no use in scripting.

Source: [http://www.tldp.org/LDP/abs/html/histcommands.html](http://www.tldp.org/LDP/abs/html/histcommands.html)

I did read that the following code should allow *history* to be run from within a script:

```
set -o history
```

Perhaps your best option would be to try parse the ~/.bash_history file instead.

---

### Post by ajgreeny on 2012-08-23
Why output to a file; the file is already in existence as **~/.bash_history** in your home folder.  You could simply open that in a text editor and save as a new file if you need to, or simply use ```
cp .bash_history history.txt
```

---

### Post by IAMTubby on 2012-08-23
lechien73, ajgreeny
thank you for your replies. I did the cp .bash_history history.txt and it worked. :)

lechien73, I'm somehow not able to get that command to work. Yes, the command executes, but still shows a blank file.

Thanks.

---

### Post by lechien73 on 2012-08-23
> **IAMTubby said:**
> lechien73, I'm somehow not able to get that command to work. Yes, the command executes, but still shows a blank file.

Thanks.

Glad you have a workaround. I think that the *set* command would have to be somehow issued from inside your program, since it affects *history* on a per-session basis. In all the examples I checked, I never really found an example of it working :)

As we said, though, the .bash_history file is the easiest way to access the history.

If this fixes the issue for you, then could you please use the **Thread Tools** menu and mark it as [SOLVED]?

Thanks

---

### Post by matt_symes on 2012-08-23
Hi

> It creates a file, but the output is blank.I am wondering if you cannot get the history command to work as it's a shell built in command. The others you have tried are not.

```
matthew@matthew-Aspire-7540:~$ command -V history
history is a shell builtin
matthew@matthew-Aspire-7540:~$ which history
matthew@matthew-Aspire-7540:~$ which uname
/bin/uname
matthew@matthew-Aspire-7540:~$ command -V uname
uname is /bin/uname
matthew@matthew-Aspire-7540:~$
```Try another shell builtin and you should also get an empty file i think.
```

matthew@matthew-Aspire-7540:~$ command -V pwd
pwd is a shell builtin
matthew@matthew-Aspire-7540:~$
```Kind regards

---

### Post by IAMTubby on 2012-08-23
Thanks matt, lechien73. I think I'll go ahead with ajgreeny's copy method.
Marking the thread as solved.

---

### Post by lechien73 on 2012-08-23
> **matt_symes said:**
> Hi

I am wondering if you cannot get the history command to work as it's a shell built in command. The others you have tried are not.

Try another shell builtin and you should also get an empty file i think.

Hmmm...I tried writing a test.cpp file, *which* and other built-in commands do work. It seems to be unique to *history*!

---

### Post by matt_symes on 2012-08-23
Hi

> **lechien73 said:**
> Hmmm...I tried writing a test.cpp file, *which* and other built-in commands do work. It seems to be unique to *history*!

which is not a builtin command, lechien73.

```
matthew@matthew-Aspire-7540:~$ command -V which
which is hashed (/usr/bin/which)
matthew@matthew-Aspire-7540:~$
```

Try the command **pwd** or the command **command**

```
matthew@matthew-Aspire-7540:~$ command -V pwd
pwd is a shell builtin
matthew@matthew-Aspire-7540:~$ command -V command
command is a shell builtin
matthew@matthew-Aspire-7540:~$
```

I am interested to know if this is the issue myself.

Kind regards

---

### Post by lechien73 on 2012-08-23
Sorry, my bad. When I create the file to call

```
system("pwd");
```

then it works as expected (printing the current working directory); however if I type:

```
which pwd
```

Then I get a return of:

```
/bin/pwd
```

Interestingly, though, shell builtins for which there is no /bin equivalent do not work. So:

```
system("alias");
```

returns an empty response.

UPDATE: I've now found that not to be true. Running:

```
system("command -V command");
```

Returns a normal response. Running:

```
which command
```

Returns an empty response, showing that it doesn't have a binary equivalent on the system.

---

### Post by matt_symes on 2012-08-23
Hi

[COLOR=Navy]EDIT:
[COLOR=Black]
Try using the *command* command and redirect into the file, lechien73.[/COLOR]

I see you have just done the above[/COLOR]. [COLOR=Navy]Thanks for trying that out. So it fails becuase it's a bash builtin with no stand alone binary equivalent. Nice work[/COLOR] [COLOR=Navy]lechien73[/COLOR]

It seems that *pwd* is a stand alone binary as well as builtin then.

I suspect the *system*() command is using the *pwd* stand alone binary /bin/pwd.

*history* has no stand alone binary equivalent and is only a built in (just like *command*).

I still suspect the code was failing because *history* is a built in shell command only and the *system*() command cannot run builtin shell commands that way, only the stand alone binaries.

I was going to suggest using *echo*, but that is also a builtin and a stand alone.

```
matthew@matthew-Aspire-7540:~$ which echo
/bin/echo
matthew@matthew-Aspire-7540:~$ command -V echo
echo is a shell builtin
matthew@matthew-Aspire-7540:~$
```Maybe using the *command* command would produce an empty file :)

Interesting stuff, lechien73. I am learning something new here :) 

Kind regards

---

### Post by lechien73 on 2012-08-23
The instruction:

```
system("command -V command > output.txt");
```

Produces a file called output.txt containing the text:

```
command is a shell builtin
```

Curiouser and curiouser, said Alice :)

---

### Post by matt_symes on 2012-08-23
Hi

> **lechien73 said:**
> The instruction:

```
system("command -V command > output.txt");
```Produces a file called output.txt containing the text:

```
command is a shell builtin
```Curiouser and curiouser, said Alice :)

LOL. 

Well without looking into it, i'm at a loss then.

I wonder what an strace would reveal.

Sorry, IAMTubby. We have hijacked your thread :D

Kind regards

---

### Post by lechien73 on 2012-08-23
I'm thinking the reason that *history* is empty is because the system() function spawns a new shell, so the history is empty for that shell.

For example, I wrote the following test shell script:

```
#!/bin/bash

history
```

This returned no output whatsoever. When I changed it to:

```
#!/bin/bash

set -o history
history
```

It returned

```
1 history
```

As if it had started with an empty command history. I suppose that's consistent to a) *history* being disabled in shell scripts by default, and b) shell scripts and system() spawning new shell instances with empty histories.

---

### Post by matt_symes on 2012-08-23
Hi

You may have hit the nail on the head, apart from....

```

matthew@matthew-Aspire-7540:~$ cat syst.c 
#include<stdio.h>
#include<stdlib.h>

int main(void)
{
system("history > HistoryLog.txt");

return 0;
}
matthew@matthew-Aspire-7540:~$ gcc syst.c -o syst
matthew@matthew-Aspire-7540:~$ ./syst 
sh: 1: history: not found
matthew@matthew-Aspire-7540:~$ cat HistoryLog.txt 
matthew@matthew-Aspire-7540:~$ 
```

```

matthew@matthew-Aspire-7540:~$ strace ./syst 
execve("./syst", ["./syst"], [/* 44 vars */]) = 0
<snip>
clone(child_stack=0, flags=CLONE_PARENT_SETTID|SIGCHLD, parent_tidptr=0x7fffd89fc840) = 3516
wait4(3516, sh: 1: history: not found
<snip>
matthew@matthew-Aspire-7540:~$ 
```

```
matthew@matthew-Aspire-7540:~$ grep command syst.c
system("command -V command > HistoryLog.txt");
matthew@matthew-Aspire-7540:~$ gcc syst.c -o syst
matthew@matthew-Aspire-7540:~$ ./syst 
matthew@matthew-Aspire-7540:~$ cat HistoryLog.txt 
command is a shell builtin
matthew@matthew-Aspire-7540:~$
```

```
matthew@matthew-Aspire-7540:~$ strace ./syst 
execve("./syst", ["./syst"], [/* 44 vars */]) = 0
<snip>
clone(child_stack=0, flags=CLONE_PARENT_SETTID|SIGCHLD, parent_tidptr=0x7fff0c0a1a00) = 4400
wait4(4400, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0, NULL) = 4400
<snip>
matthew@matthew-Aspire-7540:~$
```
```

matthew@matthew-Aspire-7540:~$ bash --version | grep version
GNU bash, version 4.2.36(1)-release (x86_64-pc-linux-gnu)
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
matthew@matthew-Aspire-7540:~$
```

It would seem it can't find history on my laptop. :confused:

Might look into this when i have more time.

Kind regards

---

