---
title: "bash history behavior"
date: 2012-05-17
forum: General Help
---

### Post by glushkov on 2012-05-17
Hi guys, I am wondering why ~/.bash_history updates on Ubuntu only when a new terminal is opened? And where is the command history saved in the meantime? Here is my simple test:

== On terminal 1:
```
glushkov@UbuntuVM:~$ cat .bash_history | wc -l
117
glushkov@UbuntuVM:~$ ls
Desktop    Downloads         Music     Public     Videos
Documents  examples.desktop  Pictures  Templates
glushkov@UbuntuVM:~$ cat .bash_history | wc -l
117
glushkov@UbuntuVM:~$ exit
```

== Opening new one
```
glushkov@UbuntuVM:~$ cat .bash_history | wc -l
121
glushkov@UbuntuVM:~$
```

Regards,
Ivan

---

### Post by codemaniac on 2012-05-17
Are you sure there atenot any crons or scheduled jobs getting fired ?

However 'exit' command also gets placed in history ;)

---

### Post by glushkov on 2012-05-17
I am not sure in anything :) I just installed Ubuntu after 5 being away from Linux, and I discover that this simple thing does not work. What do you exactly mean? What should I look for? And yes, exit also gets in history, so what? It is supposed to go there.. But I still don't understand why the file was not updated already after the ls command..

---

### Post by drs305 on 2012-05-17
I can't answer your question, but thinking about it brought me to the following:

As long as the terminal is open, all the commands are available, so there wouldn't be a need to reference the history.

Once the terminal closes, and you might need past history, it's been updated. It would minimize writing to disk, but other than that I don't know why it was designed the way it was.

---

### Post by codemaniac on 2012-05-17
> **glushkov said:**
> I am not sure in anything :) I just installed Ubuntu after 5 being away from Linux, and I discover that this simple thing does not work. What do you exactly mean? What should I look for? And yes, exit also gets in history, so what? It is supposed to go there.. But I still don't understand why the file was not updated already after the ls command..

you need a ```
PROMPT_COMMAND="history -a
```
in your bashrc ,to have bash append to the history file each time it prints the prompt.

After setting PROMPT_COMMAND , try checking .bash_history , you should be having the updated snapshot .

---

### Post by glushkov on 2012-05-17
> **drs305 said:**
> 
As long as the terminal is open, all the commands are available, so there wouldn't be a need to reference the history.

...it was designed the way it was.

Not really true.. If you have issued 30 times slightly different commands, you would like to grep search through the .bash_history file, not pressing the arrow thirty times.

And it was NOT designed like this. It is Ubuntu specific change. The default behavior is the one I was expecting :)

---

### Post by codemaniac on 2012-05-17
> **glushkov said:**
> Not really true.. If you have issued 30 times slightly different commands, you would like to grep search through the .bash_history file, not pressing the arrow thirty times.

And it was NOT designed like this. It is Ubuntu specific change. The default behavior is the one I was expecting :)

You can use ctrl+r feature also to search though history for a specific command .

---

### Post by glushkov on 2012-05-17
> **codemaniac said:**
> You can use ctrl+r feature also to search though history for a specific command .

True, but having a file is much more flexible (for example using grep -v)

---

### Post by glushkov on 2012-05-17
> **codemaniac said:**
> you need a ```
PROMPT_COMMAND="history -a
```
in your bashrc ,to have bash append to the history file each time it prints the prompt.

This hack works, thanks. I still don't know where the history of the current terminal is stored, but I guess that's not that important.

---

### Post by JKyleOKC on 2012-05-17
> **glushkov said:**
> I still don't know where the history of the current terminal is stored, but I guess that's not that important.It's kept in RAM as part of the process's data, and appended to ~/.bash_history when the process ends. If you have multiple terminal processes going, their histories will be appended in the order that you close them.

I've found that the command "history -c" followed by a CTRL-D to close the terminal will clear the RAM copy, so that there's no change to the file on disk. I'd like to make this an alias so that I could do it with a single keystroke, to avoid cluttering up the history file with diagnostic commands and routine junk...

---

