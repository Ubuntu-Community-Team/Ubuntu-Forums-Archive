---
title: "piping question"
date: 2011-05-13
forum: General Help
---

### Post by tapi0n on 2011-05-13
So,

I'm making these two small scripts.

```
#!/bin/sh

PATH=/home/testfolder/nagioslogging

/bin/date >> $PATH/user/dailylog.log | /bin/grep -w 'Syscom' /usr/local/nagios/var/nagios.log >> $PATH/user/dailylog.log
```and

```

#!/bin/sh
PATH=/home/testfolder/nagioslogging

/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log | /bin/cat /dev/null > $PATH/user/dailylog.log
```
The second one just doesn't work. The content of *dailylog.log *doesn't get added to *generallog.log* but it's content (*dailylog.log*) does get overwritten by [I]/dev/null > file.

[/I]Now I noticed that when running the first script. The first part of the pipe (*/bin/date >> $PATH/user/dailylog.log*) gets added to the file behind the second part of the script.

So, say this is the input (talking about the first script):
-
some input 
some more input
-


I'd expect the output of running the first script to be:

timestamp
-
some input
some more input
-

As instead, this shows up:

-
some input
some more input
-
timestamp





So, this leads me to believe that when using the second script i'm encountering the same problem. I think it runs *cat /dev/null > file *before the content of the file is copied.

Has anyone encountered a similar problem of any sort? 


Cheers,

---

### Post by tapi0n on 2011-05-13
I'm not a big fan of this, but since I'm despret for an answer and can't find one. Bump

---

### Post by matt_symes on 2011-05-13
Hi

Try this for the script.
[FONT=monospace]
[/FONT]```
#!/bin/sh 
PATH=/home/testfolder/nagioslogging  
/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log **&&** /bin/cat /dev/null > $PATH/user/dailylog.log
```Not quite sure why you were using a pipe there. Try it with && instead. You also my want to use #!/bin/bash

Kind regards

---

### Post by tapi0n on 2011-05-13
> **matt_symes said:**
> Hi

Try this for the script.
[FONT=monospace]
[/FONT]```
#!/bin/sh 
PATH=/home/testfolder/nagioslogging  
/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log **&&** /bin/cat /dev/null > $PATH/user/dailylog.log
```Not quite sure why you were using a pipe there. Try it with && instead. You also my want to use #!/bin/bash

Kind regards

Sweet, got it working. Thanks a million mate. Didn't know about the && :) 

This is actually the first time I'm working with these kinds of things. So why would you use bash instead of sh?

---

### Post by matt_symes on 2011-05-13
Hi

> **tapi0n said:**
> Sweet, got it working. Thanks a million mate. Didn't know about the && :) 

This is actually the first time I'm working with these kinds of things. So why would you use bash instead of sh?

A couple of points. 
[FONT=monospace]
[/FONT]```
/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log && /bin/cat /dev/null > $PATH/user/dailylog.log

```

What you have in effect here is two commands. So you could have written your script like this and it will have worked.

```
#!/bin/sh  
PATH=/home/testfolder/nagioslogging
/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log
/bin/cat /dev/null > $PATH/user/dailylog.log
```

It will always run /bin/cat $PATH/user/dailylog.log >>  $PATH/syscom/generallog.log and after it will always run /bin/cat  /dev/null > $PATH/user/dailylog.log even if either fail.

The && command is the logical boolean 'and' command. What this will do is run the first command

```
/bin/cat $PATH/user/dailylog.log >> $PATH/syscom/generallog.log
```

and if, and only if, that completes successfully it will run the second  command 

```
/bin/cat /dev/null > $PATH/user/dailylog.log
```

What you were trying to do with the pipe will not work. Read up on pipes, redirection and subshells and you will understand why.

There are two very good links to bash scripting at the bottom of my signature.

As for referencing #!/bin/bash directly, #!/bin/sh is a symbolic link on most systems to a default shell.

```
matthew@matthew-laptop:~$ ls /bin/sh -l
lrwxrwxrwx 1 root root 4 2011-05-08 22:35 /bin/sh -> dash
matthew@matthew-laptop:~$ 
```

On Ubuntu the shell is dash but on other systems it can be other shells. Many systems use the Bourne (POSIX compliant) shell. You are not doing so in the script you have written, but if you use commands that are for a specific shell then you want to reference that specific shell otherwise you will get errors.

The most portable way to specify a shell is like this

```
#!/usr/bin/env bash
```

Kind regards

---

### Post by tapi0n on 2011-05-13
ok seriously appreciate the input mate. 

I'll definitly read up on that bash guide as soon as some spare time opens up.

Cheers.

---

