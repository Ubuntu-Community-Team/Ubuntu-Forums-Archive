---
title: "transfering files between machines"
date: 2012-05-10
forum: General Help
---

### Post by marjenni on 2012-05-10
I have two machines, machine A and machine B.
 
I currently have a cron running on machine B that periodically SCPs a file to machine A.
 
I want to change this so that machine A connects to machine B, and pulls down the required files.
 
Would I use wget? how would I do this?
 
Many thanks for your help

---

### Post by lukeiamyourfather on 2012-05-10
Just use scp the other way around. Am I missing something? Another way to do it would be to share a directory on one machine and simply mount that directory on the other so they effectively would be working from the same data without having to copy it back and forth first.

---

### Post by codemaniac on 2012-05-10
If i understand your requirement clearly you need the SCP scon entry in machine A that would get the files from machine B .
Why exactly you need this way around when you have a working solution ?

---

### Post by LemursDontExist on 2012-05-10
More info about your exact requirements and reasons for wanting to do this would be helpful.  There are dozens of ways to do what you want, and without more info it's hard to say which is best!

To make lukeiamyourfather's answer clearer scp can work either way so from Machine A you can run

```
scp user@machineB:remote_file local_folder/
```

to pull a file.  The syntax is generally just

```
scp target destination
```

---

### Post by marjenni on 2012-05-11
Ah yes thank you. I suppose it is obvious, but I had only used scp to push files, of course it can be used to pull as well.

Thank you

---

