---
title: "cp command log output"
date: 2011-11-08
forum: General Help
---

### Post by Michel_VZ on 2011-11-08
Hello, 

This is what im trying to do:

I want to use the cp command in the terminal of ubuntu to copy one folder to the next while logging its actions to a textfile. I want the option to log the files transferred succesfully and the ability to log any errors occured. I'd like to log these two things independently into two files.

Im using this command right now: cp -r -v /var/log /home/client > /home/client/logfile

Wich seems to come close to what im trying to do. But for some reason the entry's that show up in the logfile also show up as "Permission Denied" in the terminal.

Any help is greatly appreciated.

---

### Post by WorMzy on 2011-11-08
You can redirect errors (STDERR) with "2>", just like you can redirect output (STDOUT) with ">".

e.g.

```
cp -r -v /var/log /home/client > /home/client/logfile 2> /home/client/logfile-errors
```

---

### Post by matt_symes on 2011-11-08
Hi

Is /home/client owned by root or a different user than the one you are trying to run the command under ? Are you trying this under your user ?

I.E are you the user 'client' ?

Do you (client) have the permissions to copy the files and read the log files ?

Kind regards

---

### Post by Michel_VZ on 2011-11-08
Thanks Wormzy! very helpful.

@ Matt

I understand why the error is occuring. Im just wondering why its showing up when i run the command as > cp -r -v /var/log /home/client > /home/client/logfileinstead of >2. I would think this is an error and therefore would not log with just ''>''. But i guess its called output for a reason. So my next question would be: is there a way to only show succesfull file transfers without errors?

---

### Post by WorMzy on 2011-11-08
Sure, redirect STDERR to /dev/null

e.g.

```
cp -r -v /var/log /home/client 2> /dev/null
```

---

