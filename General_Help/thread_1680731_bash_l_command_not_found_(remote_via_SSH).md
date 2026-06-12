---
title: "bash: l: command not found (remote via SSH)"
date: 2011-02-03
forum: General Help
---

### Post by LoneWolfJack on 2011-02-03
hello community,

I have this strange problem that I could use some help on.

when I log in to my ubuntu machine through ssh and user/pass and then try to use the command "l", everything works.

now when I log in to that same machine through ssh but via the public key, I get "bash: l: command not found"

in both cases, the user is root, so apparently, root has different privileges when logging in by using the public key.

now the question is: how would I go about getting this to work properly?

thanks in advance.

---

### Post by Brandon Williams on 2011-02-03
Take a look at your /root/.ssh/authorized_keys file on the machine you're connecting to. Is there a command specified for the key you're using? That's the only place in the config that I can think of that might be driving one type of login to use a different command than another.

---

### Post by LoneWolfJack on 2011-02-03
it says

ssh-rsa <key>

in the file; to the best of my knowledge, this should be correct. funny enough, the command "ls" works.

---

### Post by CharlesA on 2011-02-03
'l' is an alias.

```
alias l='ls -CF'

```

---

### Post by LoneWolfJack on 2011-02-03
well, you're probably not posting this without a clue, but:

l gives
```

drwx------  9 root root 4096 2011-02-04 01:52 ./
drwxr-xr-x 20 root root 4096 2010-06-02 09:56 ../
drwx------  2 root root 4096 2009-02-18 09:15 .autoinstaller/
-rw-------  1 root root 9716 2011-02-04 01:52 .bash_history
drwxr-xr-x  2 root root 4096 2008-06-07 00:20 bin/

```

ls -CA gives
```

.autoinstaller/  .bash_history  bin/

```

I've read through the list of ls parameters, but it doesn't appear to be possible to get an output like with l.

also, why would the alias not work when logged in with the public key?

---

### Post by LoneWolfJack on 2011-02-03
ok, never mind, google is really helpful at times; one can get a list of aliases by just typing "alias" on the shell.

```
l = ls -alF
```

but still, why would aliases not work with the public key?

---

### Post by CharlesA on 2011-02-03
They are dependent on what aliases are enabled on the remote machine.

---

### Post by LoneWolfJack on 2011-02-03
right, but why would aliases by different for the same user depending on the login type?

besides, I do have the right "l" in the alias list, but it's still saying command not found unless I log in with username/pass instead of the public key.

---

### Post by CharlesA on 2011-02-03
Ok. Are you logging in as root via password, or as yourself then switching to root?

The environment is different depending on how you login.

---

### Post by LoneWolfJack on 2011-02-04
when I log in normally via user/pass, everything works (ssh root@ip on the shell).

when I log in with a keyfile, I just noticed that the alias list is empty (I probably mixed up my open shell windows yesterday), so l of course doesn't work.

in both cases, I'm logging in as root (yeah, bad practice, but it's only for testing).

I can live with the aliases not being available, but I'd like to know why this happens. can you provide a pointer to a document or a term I should use on google?.

---

