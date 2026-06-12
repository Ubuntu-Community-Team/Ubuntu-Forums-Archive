---
title: "SSH Configuration"
date: 2012-08-31
forum: General Help
---

### Post by hhaydoura on 2012-08-31
hi, well i'm a new sys admin trainee and my supervisor gave me a virtual ubuntu machine ( only shell ) and asked me to give a user ssh access, in other words i'm supposed to enter that user account from my account, remote access, can anybody tell me what are the steps to do this?  my account is called hassan , server is ubuntu lets say the user account is called "test"

---

### Post by Lars Noodén on 2012-08-31
The shell and what you can do with it is the same whether you are logged in locally via the console or remotely via ssh.  If this is your first time, I would recommend reading [Using the Terminal](https://help.ubuntu.com/community/UsingTheTerminal) from top to bottom and then following some of the links at the end.

Since you're using a virtual machine and using it for experiments, be sure to save a snapshot of the plain, untouched installation.  That way you you can experiment to your heart's content and always be able to go back to a pristine installation by rolling back to the snapshot.

---

### Post by hhaydoura on 2012-08-31
well that wasnt very helpful, all i need is the steps to install and configure the ssh on both accounts, so that i log in to the user "test"

---

### Post by Lars Noodén on 2012-08-31
The answers are often only as good as the original question. ;)   No re-configuration of the ssh server is needed, it should work out of the box for all basic needs.

If you want to connect to a remote computer via SSH then all that is needed is that you install the package [openssh-server](apt://openssh-server) on the remote machine. 


Then to connect you can use any number of built-in SSH or SFTP clients.  In Nautilus you can press ctrl-L and then enter a URL for a SFTP connection:
```

sftp://user@10.101.102.5

```

Or you can go via [sftp](http://manpages.ubuntu.com/manpages/precise/en/man1/sftp.1.html) in the shell.

```

sftp user@10.101.102.5

```

If you want an interactive shell then you can use [ssh](http://manpages.ubuntu.com/manpages/precise/en/man1/ssh.1.html).  The shell you will get will give you the same level of control that you would have if you were logged in locally via the console.

```

ssh user@10.101.102.5

```

Substitute the actual username and IP number for your remote machine.

---

