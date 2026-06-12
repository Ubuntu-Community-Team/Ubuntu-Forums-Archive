---
title: "Quick SUDO question"
date: 2010-01-23
forum: General Help
---

### Post by ripeart on 2010-01-23
Hi,

This little question has been irking me for some time. I know that there is a difference between SUDO -i and SUDO su. 

Which sudo command actually changes your prompt to a root prompt and thereby executes commands is if it were root? Additionally, which sudo command allows a user to execute a command as themselves however with root privileges?

Or am I looking at this the wrong way?

Thanks

---

### Post by Brandon Williams on 2010-01-23
Both 'sudo -i' and 'sudo -s' will give you a root prompt. The difference between them is related fundamentally to environment initialization.

If you need to launch a root shell and then run a bunch of interactive commands within that shell, then run 'sudo -s'. This is equivalent to running 'su' on its own, except that 'sudo -s' will run the shell specified by your SHELL environment variable and 'su' will run the shell specified in /etc/passwd for the target user.

If you need to launch a root shell with the environment fully re-initialized as if the root user had just logged in, then run 'sudo -i'. This is equivalent to running 'su -l'.

There isn't much point to running 'sudo su', since sudo on its own provides the same functionality as su already. The command line 'sudo su' will do the same as running 'sudo -s', with the one exception noted above. If you want 'sudo -s' to run the target user's configured shell, then just do 'unset SHELL; sudo -s'

The permissions model requires you to run the command as the user whose priveleges you want in order to get those priveleges. I'm not aware of any way to run a command with one user's effective ID but some other users priveleges.

---

### Post by aysiu on 2010-01-23
I would highly recommend against using *sudo -s*, since it runs with root privileges but using the user's environment, which can result in accidental change in ownership of certain configuration files from user to root (resulting in certain applications not behaving properly).

If you want a persistent root prompt, use ```
sudo -i
```

---

### Post by ripeart on 2010-01-23
Thanks for the explanations and responses. I understood about half of that lol. Could you please provide a quick example of scenarios when one would use sudo -s vs sudo -i? What is the suggested reading for the SUDO command?

Additionally, the SHELL variable? The shell in /etc/passwd? When would I need to worry about these settings?

I am using Karmic KDE for day to day however I do have a Ubuntu karmic server running CLI only on a Thinkpad in another room.

Thanks again.

---

### Post by aysiu on 2010-01-24
I can't think of a single advisable scenario to use *sudo -s*.

Use ```
sudo -i
``` Fewer potential problems.

---

### Post by VCoolio on 2010-01-24
> **aysiu said:**
> I would highly recommend against using *sudo -s*, since it runs with root privileges but using the user's environment, which can result in accidental change in ownership of certain configuration files from user to root (resulting in certain applications not behaving properly).

If you want a persistent root prompt, use ```
sudo -i
```

If sudo -s runs with user environment, how come files can change ownership to root? I would expect that sudo -s extends the users privileges, not change user to root while using user environment. But the latter is the case?

So (really not useful example, but anyway) if I would do:
sudo -s; nano ~/.someconfig; edit and save: that would change ownership of that file to root? But with
sudo -i; nano ~/.thatsameconfig; edit and save: that also happens?

---

### Post by aysiu on 2010-01-24
The issue is that *sudo -s* uses the user environment (and, hence, the user configuration files) but as the root user.

```
sudo -i
``` uses the root environment (and the root configuration files) as the root user.

In both cases, you are operating as the root user. But if you make changes to user configuration files as root, it's possible ownership of those files might change to root ownership. If you make changes to root files as root, it doesn't matter, because those files are owned by root anyway.

---

### Post by Brandon Williams on 2010-01-24
If you use sudo to perform operations on files that already exist, then the permissions and ownership on those files after the operation will be the same as the permissions and ownership were before the operation (assuming that the operation is not intended to change ownership or permissions, e.g. chmod or chown). If a file is created as a result of the sudo operation, then the new file will be owned by the user who you become for sudo purposes.

If what you want is an interactive shell session, then the safest thing to do is use 'sudo -i' to get a root prompt, since this makes it less likely that you will unintentionally modify files in your own home directory or create files in your user home directory that you will not be able to access later due to permissions. It's also a good idea to close the shell with the root prompt as soon as you are done with the operation that you opened it for. Leaving it open makes it more likely that you will forget it's a root prompt and do something as root that you didn't intend to do.

The most common use of 'sudo -s' is when you want to run a complicated shell command line as root and need variables from your environment or your own customized config files in order to make it work. A contrived example would be:
```
sudo -s 'find $HOME/Images > /tmp/$SUDO_USER-home-Images.out'
```
I need the value of $HOME from my user environment but I want the resulting file to be owned by root. I need the -s switch so that the command line will be correctly interpretted, since it contains special shell simbols like '>' for redirection.
It's a good idea to use 'sudo -s' only for one-line shell expressions and only when you are absolutely certain that you need to preserve your user environment.

---

