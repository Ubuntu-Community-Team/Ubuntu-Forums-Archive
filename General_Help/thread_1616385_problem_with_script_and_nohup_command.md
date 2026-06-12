---
title: "problem with script and nohup command"
date: 2010-11-08
forum: General Help
---

### Post by mahmoodn on 2010-11-08
I want to use nohup and script command together but they don't work. Normally I use
```
script -c "./run arg1" run-log.txt
```
Then I want to send that command in background with nohup:
```
nohup "script -c \"./run arg1\" run-log.txt" &
```
but I get this error:
```
nohup: ignoring input and appending output to `nohup.out'
nohup: cannot run command `script -c "./run arg1" run-log.txt': No such file or directory

```

---

### Post by babur on 2010-11-08
Try to execute the command by adding "/dev/null"

```
nohup "script -c "./run arg1" run-log.txt" < /dev/null &
```

---

### Post by mahmoodn on 2010-11-08
Didn't work
```

mahmood@localhost:~$ nohup "script -c "./run arg1" run-log.txt" < /dev/null &
[1] 15358
mahmood@localhost:~$ nohup: appending output to `nohup.out'
nohup: cannot run command `script -c ./run ': No such file or directory
^C
[1]+  Exit 127                nohup "script -c "./run arg1" run-log.txt" < /dev/null
mahmood@localhost:~$
```

---

### Post by mahmoodn on 2010-11-08
I found that nohup by default writes everything on terminal to a file called "nohup.out". So I used this command to redirect everything to another file:
```
nohup ./run arg1 > run-log.txt &
```
So there is no need for "script" command? will it redirect **all things** to a file like script command or it will only redirect stderr messages?

---

### Post by trundlenut on 2010-11-08
I found that I had to use the following command to run a script with nohup

```
nohup bash script.sh
```

---

### Post by babur on 2010-11-09
You can just use "nohup" without script command.  The nohup command will redirect all the messages by default to "nohup.out" or to the custom file.

---

