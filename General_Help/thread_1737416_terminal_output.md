---
title: "terminal output"
date: 2011-04-23
forum: General Help
---

### Post by mabzki on 2011-04-23
is it possible to log the command output's history that are previously printed messages in the terminal to a file? that is the first command output when i first opened terminal through the last command.

---

### Post by Paddy Landau on 2011-04-23
Do you mean a history of the commands that you typed, or a history of the output from the commands?

For a history of the commands, use the [FONT=Courier New]history[/FONT] command ([FONT=Courier New]man history[/FONT] for a description). While in a terminal, you can press Ctrl-R and start typing in order to search your history for a command.

If you mean a history of the output from the commands, sorry, this is not possible. You can, however, explicitly direct output from a command to a file. For example:
```
# Redirect the output to file.lst. If it already exists, overwrite it.
# Errors will display on the terminal.
echo 'One' >file.lst

# Redirect to file.lst. If it already exists, append to it.
echo 'Two' >>file.lst

# Redirect to file.lst. Redirect error messages to file.err.
echo 'Three' >file.lst 2>file.err

# Redirect to file.lst, including error messages.
echo 'Four' &>file.lst

# Redirect error messages to "nowhere" (/dev/null). Normal messages go to the terminal.
echo 'Five' 2>/dev/null
```For more information on redirection, [FONT=Courier New]man bash[/FONT] and search for REDIRECTION.

---

### Post by mabzki on 2011-04-23
yes im referring to the history of the outputs of the command not the command itself. in my case the history output of the *yum install*. is there anyway?

---

### Post by DaithiF on 2011-04-23
Hi, no, its not possible after the fact.  If you know beforehand that you want to log all activity (input and output) within a terminal session then you can use the script command.

you invoke it like:
[B]script mylogfile
[/B]and then it records every command you input, and the output from that command, until you end the session by issuing the command:
**exit**
at which point the filename you chose (e..g mylogfile) will contain the log of your session.

---

### Post by mabzki on 2011-04-23
Thanks it works. Just the one i has looking for. :D

---

### Post by Paddy Landau on 2011-04-24
> **DaithiF said:**
> script mylogfile
Hmm, I learn something every day. Thanks for that.

---

