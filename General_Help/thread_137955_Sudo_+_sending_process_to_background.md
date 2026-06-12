---
title: "Sudo + sending process to background"
date: 2006-03-01
forum: General Help
---

### Post by ivanhelguera on 2006-03-01
Hi, 
I met a problem. I assume it is laughably simple for all you geeks out here, but  it interested me nonetheless. I wanted to update the slocate database, and I wanted the process to happen i the backround (which seems only natural). However, typing
 ```
 sudo updatedb& 
```
did not do the trick, as the process of asking for input for the password was in the backbround
```

marcinek@ubuntu:~$ sudo updatedb&
[1] 7251
marcinek@ubuntu:~$ Password:
mypassword
bash: mypassword: command not found

[1]+  Stopped                 sudo updatedb
```
I understand there are simple ways of getting away with that, but what would be the *genuine* solution - ie a simple command that would ask for the pwd, and then execute the command  
Thanks, 
iH

---

### Post by RAOF on 2006-03-01
You could just start it up in the foreground, enter the password, and press "Ctrl-z" to pause it, then "bg" to run it in the background.

Failing that, what does man sudo have to say...
Yup.  Seems that "sudo **-b** updatedb" will do what you're after.

---

### Post by ivanhelguera on 2006-03-12
thanks, the -b option seems to do the job
ih

---

