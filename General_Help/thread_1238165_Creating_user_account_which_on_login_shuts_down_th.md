---
title: "Creating user account which on login shuts down the computer"
date: 2009-08-12
forum: General Help
---

### Post by lgp171188 on 2009-08-12
I want to create an unprivileged user account, say 'shutdown', which can be used only to shutdown the system. I followed the instructions in [http://www.cyberciti.biz/tips/shutdown-account-to-shutdown-linux-server.html](http://www.cyberciti.biz/tips/shutdown-account-to-shutdown-linux-server.html). But when I login into the system, I get this error 'Cannot execute /usr/bin/sudo /sbin/shutdown -h now: No such file or directory'.

These are the configurations that I did

/etc/sudoers:

```

shutdown localhost=/sbin/shutdown -h now

```

/etc/passwd:
```

shutdown:x:999:0:shutdown:/sbin/:/usr/bin/sudo /sbin/shutdown -h now

```

I guess the shutdown binary and/or the /sbin folder is out of access for the shutdown user. How am I to get it right?

Thanks in advance.

---

### Post by regala on 2009-08-12
> 
/etc/passwd:
```

shutdown:x:999:0:shutdown:/sbin/:/usr/bin/sudo /sbin/shutdown -h now

```


in /etc/passwd, you can't have such "shell" as a complete command line, you must put an simple executable with no argument.
When you login, the system runs it with various arguments depending on the type of login (-i for interactive login, etc...)
you can't put anything you want here, because it's not as simple as "when the user logs in, he executes this command"

yet, I don't understand why you don't use the shutdown button, it's there for that and what you suggest is a weird way of doing it =)

---

### Post by lgp171188 on 2009-08-12
> **regala said:**
> in /etc/passwd, you can't have such "shell" as a complete command line, you must put an simple executable with no argument.
When you login, the system runs it with various arguments depending on the type of login (-i for interactive login, etc...)
you can't put anything you want here, because it's not as simple as "when the user logs in, he executes this command"

yet, I don't understand why you don't use the shutdown button, it's there for that and what you suggest is a weird way of doing it =)

I want to do it that way because the machine I am trying to do this is a Blade server machine without GUI. And there are operators who need to properly shutdown the servers during power outage before the UPS backup drains out.

---

### Post by regala on 2009-08-13
> **lgp171188 said:**
> I want to do it that way because the machine I am trying to do this is a Blade server machine without GUI. And there are operators who need to properly shutdown the servers during power outage before the UPS backup drains out.

you, then, just need to allow them to run shutdown from their shell (sudo is enough) or configure your ups backup to do it automatically (with apcupsd or nut, etc...) via USB or serial port. and use rssh if you want to provide them with an ultra-restricted shell that only let them exec this very command.

Else, you can create a shell script that sudo shutdown -h now, and configure the shell of shutdown user to be that script. Personally, I think that going that way is digging a big security hole.

---

### Post by lykwydchykyn on 2009-08-13
This could be handled by creating a script containing this:

```

/usr/bin/sudo /sbin/shutdown -h now

```

Save that script as, say, /usr/local/scripts/shutdown_script.sh (I wouldn't put it in a "bin" folder because you really don't want/need it in the default PATH), then make that script the user's shell.

But I agree that this is not typically the best approach.  I would create a group called "shutdown" and give the group sudo permissions to the shutdown command (or a script containing the exact shutdown command I wanted them to run).  Then add your operators to the group.  Such a solution makes security easier to maintain over the long run.

---

