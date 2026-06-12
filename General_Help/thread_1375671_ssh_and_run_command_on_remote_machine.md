---
title: "ssh and run command on remote machine"
date: 2010-01-08
forum: General Help
---

### Post by zeezam on 2010-01-08
I have made a shortcut on desktop and want that one to ssh from machineA to machineB and run a command.
I have fixed the .pub file so I can ssh without password.

This is what I want to do
[PHP]ssh -X user@machineB && start-the-program[/PHP]

..but it seems to not run the command after "&&".
How can I do to make it automaticly run a command after it has connected over ssh?

---

### Post by KeLa on 2010-01-08
Try without &&
like this:
```
ssh -X user@machineB start-the-program
```

---

### Post by zeezam on 2010-01-08
> **KeLa said:**
> Try without &&
like this:
```
ssh -X user@machineB start-the-program
```

It seems it tries to run that all together. I don't get connect with ssh.

---

### Post by KeLa on 2010-01-08
Ok,

Next try this```

ssh -X user@machineB 'start-the-program'
```At least someone has using it so.

---

### Post by zeezam on 2010-01-08
> **KeLa said:**
> Ok,

Next try this```

ssh -X user@machineB 'start-the-program'
```At least someone has using it so.

That worked! Thanks!

---

### Post by asdel on 2010-01-08
> **zeezam said:**
> 
This is what I want to do
[PHP]ssh -X user@machineB && start-the-program[/PHP]


This is a unix command prompt/shell script thing.

Command1 && Command2 

means execute command 1 and if it succeeds, execute command 2.


However, SSH is special, in that it creates a new shell/login environment on the remote host, and has the option to execute a commend there.

So ssh host2 cmd1

will log into host2 just long enough to execute command1 and return.

On the other, ssh host2 && cmd1, you'll log into host1 with a regular terminal, but cmd1 won't run. If you type 'exit', on host1, you'll return to the host you typed your command on, and execute the command locally.

---

