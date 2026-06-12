---
title: "BASH script parameters"
date: 2011-02-15
forum: General Help
---

### Post by TomAndJerry01 on 2011-02-15
hi all,

I was wondering if anyone could help me with little problem. I'm learning bash and trying to pass parameters into script, which works fine since my script has a+x set. But what is I need to run script via bash -x .../myScript.sh. I cannot just pass parameters as before. Can anyone help me please. Many thanks for replies.

---

### Post by DaithiF on 2011-02-15
why not?  it should work just the same.

from **man bash**:

ARGUMENTS
       If  arguments  remain after option processing, and neither the -c
       nor the -s option  has  been  supplied,  the  first  argument  is
       assumed  to  be the name of a file containing shell commands.  [B]If
       bash is invoked in this fashion, $0 is set to  the  name  of  the
       file,  and  the  positional  parameters  are set to the remaining
       arguments.[/B]  Bash reads and executes commands from this file, then
       exits.  Bash's exit status is the exit status of the last command
       executed in the script.  If no commands are  executed,  the  exit
       status  is  0.   An attempt is first made to open the file in the
       current directory, and, if no  file  is  found,  then  the  shell
       searches the directories in PATH for the script.

---

### Post by TomAndJerry01 on 2011-02-15
ok, thx for reply. It there must be something 'ugly' in the rest of my script ...

---

### Post by Habitual on 2011-02-16
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

