---
title: "non-interactive ssh evironment variables"
date: 2010-08-24
forum: General Help
---

### Post by strycat on 2010-08-24
I'm having the same problem as described in:

[http://ubuntuforums.org/showthread.php?t=346300](http://ubuntuforums.org/showthread.php?t=346300)

To the remote system's sshd_config I've added 
PermitUserEnvironment yes

If I do something like

ssh -X server123 "export FOO=1; env"

I see that FOO has indeed been set to 1.

However if I do something like

ssh -X server123 "export FOO=1; programWithBuggyBehaviorifFooIsntSet"

The program behaves as if I haven't set FOO.

Now I can something like 

ssh -X server123
[user@server123] export FOO=1; programWithBuggyBehaviorifFooIsntSet

And this works just fine.

So what might I be doing wrong?

Thanks in advance.

---

### Post by clrg on 2010-08-24
Have you

```
sudo service ssh restart
```

after the configuration change?

For your variables, check out the directive

```
AcceptEnv LANG LC_*
```

you could add the desired variables to that list.

---

