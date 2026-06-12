---
title: "sudo: cd: command not found"
date: 2009-10-14
forum: General Help
---

### Post by t0p on 2009-10-14
Looky here:

```
t0p@deimos:~$ cd /etc/chatscripts
bash: cd: /etc/chatscripts: Permission denied
t0p@deimos:~$ sudo cd /etc/chatscripts
[sudo] password for t0p: 
sudo: cd: command not found
t0p@deimos:~$ sudo -s
root@deimos:~# cd /etc/chatscripts
root@deimos:/etc/chatscripts# 

```

How come **'sudo cd'** doesn't work?

---

### Post by ibuclaw on 2009-10-14
cd isn't a command.

It's a builtin.

Type in
```
help
```
For a list of other builtins that won't work with sudo.

---

### Post by t0p on 2009-10-14
Thanks.

Tell you what though, that does seem to be a bit of a boo boo.  Ubuntu encourages use of sudo rather than logging in as root.  Yet sudo will not work with these builtins.

Why won't sudo work with builtins?  Actually, that should read as: Why don't the writers of sudo want it to work with builtins?

---

### Post by sisco311 on 2009-10-14
> **t0p said:**
> Thanks.

Tell you what though, that does seem to be a bit of a boo boo.  Ubuntu encourages use of sudo rather than logging in as root.  Yet sudo will not work with these builtins.

Why won't sudo work with builtins?  Actually, that should read as: Why don't the writers of sudo want it to work with builtins?

Exactly what would you expect from *sudo cd /root*?

---

### Post by lisati on 2009-10-14
> **sisco311 said:**
> Exactly what would you expect from *sudo cd /root*?

+1
I would have thought that ordinairily something like **sudo cd ...** wouldn't be necessary.

---

### Post by az on 2009-10-14
> **t0p said:**
> Thanks.

Tell you what though, that does seem to be a bit of a boo boo.  Ubuntu encourages use of sudo rather than logging in as root.  Yet sudo will not work with these builtins.

Why won't sudo work with builtins?  Actually, that should read as: Why don't the writers of sudo want it to work with builtins?

As your user, you cannot change into that directory.  As root you can.  Using sudo, you escalate your privileges to be able to do that, but once that command finishes, you are back to your regular privileges.  But as your user with regular privileges you are not allowed to cd there...

The current behavior is correct.

---

### Post by shylent on 2009-10-14
Actually it should read like this: when you do "sudo <whatever>" you are launching an *executable* called " whatever" as another user (that's what sudo does anyway). However, "cd" is not an *executable* - it is a built-in *shell command. *You are NOT launching an executable, you are telling the shell to perform some action, in this case, change the current working directory -> not the same thing! Try "help" - you will see some more of those built-ins.

Anyway, you don't need to log in as root at all. You know, that you can do "sudo sh" to get into a root shell (again, not the same thing as logging in as root at all), right?

---

### Post by sisco311 on 2009-10-14
Well, you can run bult-in commands with sudo :)

```
[sisco@acme xtmp]$ pwd  # admin user
/home/sisco/xtmp
[sisco@acme xtmp]$ sudo -i cd /root  # as root cd to /root
[sisco@acme xtmp]$ pwd  # admin user
/home/sisco/xtmp

```

:evil:

---

### Post by lisati on 2009-10-14
> **tinivole said:**
> cd isn't a command.

It's a builtin.

In MS-DOS-speak, it's a built-in command, not an external command.

---

### Post by g000we on 2009-12-11
Hey,

Try
```

$sudo su -

```
cd command your way back to the desired location, and then cd to the directory of want.

When finished ruining/fixing the system, type "su {username}" to return to your user (without root privileges, where {username} is the username).

g000we

---

### Post by pricetech on 2009-12-11
> **lisati said:**
> In MS-DOS-speak, it's a built-in command, not an external command.

I recall the terms being "internal" and "external"

Just semantics I know.

---

### Post by pricetech on 2009-12-11
> **g000we said:**
> Hey,

Try
```

$sudo su -

```
cd command your way back to the desired location, and then cd to the directory of want.

When finished ruining/fixing the system, type "su {username}" to return to your user (without root privileges, where {username} is the username).

g000we

Or type exit to return to your user account.

---

### Post by Gravidar on 2010-02-14
> **pricetech said:**
> Or type exit to return to your user account.
Agreed, always use "exit" otherwise a *root* session still exists.

As for cd'ing using sudo, it did strike me as counter-intuitive at first which is how I ended up here after getting this "error" myself, however, if you think that you use sudo cd to enter a directory and once the command is finished, your privileges drop again and you're now in a directory you don't have permission to be in, that seems like it could get kind of complicated.

I would tend to sudo su to be owner of the directory (e.g. "sudo su fred"), now that I've found out why you can't sudo cd :)

---

