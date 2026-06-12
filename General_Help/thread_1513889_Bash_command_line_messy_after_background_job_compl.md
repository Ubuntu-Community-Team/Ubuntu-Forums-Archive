---
title: "Bash: command line messy after background job completes"
date: 2010-06-20
forum: General Help
---

### Post by mandar.mitra on 2010-06-20
When a background job running under bash finishes, I get a line like the following:
 
<my prompt>$ [1]+  Done                    /usr/bin/xterm<newline>
 
 So, when I write the next command, it appears *under* the prompt, rather than next to it. This would not be too much of a problem, but if after writing something that is longer than the prompt, I run the readline command kill-whole-line, then the part that is under the prompt remains unerased. This can be confusing when I start retyping the command.
 
 Is there any way that I can get bash to print a command prompt after the status line so this doesn't happen? Like so:
 
 <my prompt>$ [1]+ Done /usr/bin/xterm<newline>
 <my prompt>$ |<---- I start writing the next command from here.
 
If I recall correctly, this is how tcsh behaves.

---

### Post by NCLI on 2010-06-20
I don't know how to change Bash's default behavior, but you can use this command to clear it up:
```
clear
```

---

