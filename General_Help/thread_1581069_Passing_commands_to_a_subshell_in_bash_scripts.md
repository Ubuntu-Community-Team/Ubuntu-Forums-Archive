---
title: "Passing commands to a subshell in bash scripts"
date: 2010-09-24
forum: General Help
---

### Post by pierolinux on 2010-09-24
Hello everybody,
    I was reviewing some scripts written by a person that does not work with us anymore and I found a chunk of code I'd like to know more about.

```
mycli <<! >> /var/myprogram.log
command_1
command_2 
...
command_n
!
```
mycli starts the Command Line Interface (that waits for specific commands to be executed) of a software of ours. Commands are passed to the CLI using the code between the two exclamation marks and the output is redirected to a file for log purposes.

I have a fair knowledge of bash scripting, but I was not aware of the construct above. Can anybody explain me how that work more in detail (what other possibilities it gives, what are the alternatives and so on) and where I can find more documentation?

Thank you

---

### Post by gyre007 on 2010-09-24
Hi im not sure if what you wrote here is regarded as "passing the commands to subshells"...
the code snippet you just wrote shows some basic shell functionality...
as you know >> redirector tells to append the stderr/stdout to some file while the "opposite" sign like << is
does (in a very general meaning) "append the input (or rather pass one input parameter after another) to the stdin of the particular program UNTIL you'll see the string following the << redirector, then finish passing/appending those argument"

So in shortcut you can see that "<<" Accepts text on the following lines as standard input
You can do something like this for example to see what I mean

```
gyre@gyre-laptop:~$ cat << TRAM
> TAKJT
> TAKJTK
> DSFSDU
> TRAM
TAKJT
TAKJTK
DSFSDU
gyre@gyre-laptop:~$ 
```

in the above I was passing several parameters to cat UNTIL TRAM word - that terminated the passing and caused cat to print everything to stdout.
Don't know if that answers your question though...

WIth this in mind you can see that your mycli program accepts command1, command2 etc one after another until ! sign is passed to it (as was denoted on the first line with << ! ). The output is redirected to /var/myprogram.log

---

### Post by pierolinux on 2010-09-24
AAARGH!
    Simpler than I thought! I was ok with everything... What puzzled me was the use of the exclamation point delimiting the code to append. I knew the function of << in general terms (i.e. append commands), but I did not know you could send more command and delimit the list with a keyword. The use of a special char as delimiter did not help ;-)

I also found a nice example in the Advanced Bash Scripting guide (example 16-48 and 49).

Thank you!

---

