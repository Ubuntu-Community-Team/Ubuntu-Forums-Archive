---
title: "Beginner: using set command"
date: 2011-07-03
forum: General Help
---

### Post by edwards.aus on 2011-07-03
Ubuntu Version: 11.04

Hello,

I want to set my history to 23. Hence I use the command  on the terminal
[PHP]set history = 23[/PHP]However, when I echo history by typing:
[PHP]echo -n $history[/PHP]Nothing is printed.

I checked whether the history is set by typing history, and I can see 900 history items.

It appears that the set command has not worked. 
Has anyone come across this before?
How do I resolve this issue?

Thanks,

Edwards

---

### Post by sam_delta on 2011-07-03
append the line "HISTSIZE=23" into .bashrc file. 

to do this, open a terminal and do the following
open the file with
```
gedit .bashrc
```

go to the end of the file, and add "HISTSIZE=23" in a new single line. 

Save the file and re-open your terminal.

sam

---

### Post by edwards.aus on 2011-07-03
> **sam_delta said:**
> append the line "HISTSIZE=23" into .bashrc file. 

to do this, open a terminal and do the following
open the file with
```
gedit .bashrc
```go to the end of the file, and add "HISTSIZE=23" in a new single line. 

Save the file and re-open your terminal.

sam

Thanks for your reply Sam.

I followed your instructions and edited the following commands in .bashrc to successfully set the history size:

[PHP]HISTSIZE=23
HISTFILESIZE=23[/PHP]Cheers,

Edwards

---

### Post by sam_delta on 2011-07-03
no problem, glad it work'd

sam

---

