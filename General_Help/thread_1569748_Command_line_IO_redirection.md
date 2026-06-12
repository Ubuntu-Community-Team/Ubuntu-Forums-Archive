---
title: "Command line I/O redirection"
date: 2010-09-07
forum: General Help
---

### Post by Sabir_101 on 2010-09-07
Hi Guys,

I'm writing a script that executes bash commands for me, but I want to suppress any errors coming back from a bad command and write my own error message.

So far I have this to redirect the error from the command:

```
[some_faulty_command] 2>/dev/null
```Which works fine as it suppresses the errors. But if I redirect the error stream whilst reading input from a file to a command I still get the error stream on the screen:

```
[some_command] < [some_file_that_does_not_exist] 2>/dev/null
```This still prints the error to the screen :-(

Try running for example:
```
tac < some_file_that_does_not_exist.txt 2>/dev/null
```And you'll still get the errors output to the screen.

Anyone know how to make it suppresses the errors in this situation?

---

### Post by surfer on 2010-09-07
your example works for me... i do not get any output on the shell.

not that i understand why it does not work for you...

---

### Post by Bachstelze on 2010-09-07
This is because in this case, the error message is printed by the shell, not by the command, so it is not redirected.

YOu could make a shell script with your command, run tthat script and redirect its output. Since the error message will be printed by the script, redirection will work.

---

### Post by Sabir_101 on 2010-09-07
I see, thanks, I've verified with this, assuming "log.txt" does NOT exist:

```
tac < log.txt 2>/dev/null
```bash: log.txt: No such file or directory

```
tac log.txt
```tac: cannot open `log.txt' for reading: No such file or directory

```
tac log.txt 2>/dev/null
```(No errors displayed)

I'm getting the error from bash rather than tac, so suppressing tac's error still gives me bash's error. Any way of suppressing bash's error too? I'm scripting with PHP CLI (...Yeah I know).

---

### Post by Sabir_101 on 2010-09-07
Solved with:

```
(tac < log.txt) 2>/dev/null
```

---

### Post by DaithiF on 2010-09-07
Hi, just to add (at the risk of stating the obvious), you could also check for the existence of the file (or for other likely error-causing conditions) before executing the command.  If the file doesn't exist, report that fact as you wish and then no need to execute the command. 

with the current approach I guess you're examining the return code to determine success or failure -- but then in the event of failure you're pretty much guessing as to why it failed since you've discarded the error output.

---

