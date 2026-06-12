---
title: "When using sudo PATH changes to &quot;...:/bin:/usr/X11R6/bin&quot;"
date: 2012-02-22
forum: General Help
---

### Post by scwizard on 2012-02-22
When I use sudo my path becomes "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

This is strange because there isn't even a X11R6 folder on my computer.

Why does my PATH get changed here? How can I make it so the path here is set to the value of ENV_SUPATH in /etc/login.defs?

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> When I use sudo my path becomes "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

This is strange because there isn't even a X11R6 folder on my computer.

Why does my PATH get changed here? How can I make it so the path here is set to the value of ENV_SUPATH in /etc/login.defs?
That is because the root user has more access.
The root user needs those in it's path; normal users don't have it because they aren't powerful enough.
Just leave it that way.
More info:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by scwizard on 2012-02-22
You're completely misunderstanding my question.

By DEFAULT (defaults I've changed), the super user gets this path:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
And normal users get this path:
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

This is configured in /etc/login.defs (which I've changed!!!)

However I'm getting a third path when using the sudo command:
"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

My question is "where is this configured so I can change it" not "why is the path set to this."

EDIT: Also I'm not going to "just leave it that way." Even if I was a complete newbie, telling newbies to not touch the default settings because they don't know what they're doing is the wrong approach. They should be taught to first understand why the default settings are the way they are, and then shown how they can change them. Linux is wonderful because of how configurable it is.

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> You're completely misunderstanding my question.

By DEFAULT (defaults I've changed), the super user gets this path:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
And normal users get this path:
/usr/local/bin:/usr/bin:/bin:/usr/local/games:/usr/games

This is configured in /etc/login.defs (which I've changed!!!)

However I'm getting a third path when using the sudo command:
"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

My question is "where is this configured so I can change it" not "why is the path set to this."
Just modify /root/.bashrc
Issue:
```

sudo nano /root/.bashrc

```
on the last line, insert:
```

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

```
This'll add the /usr/local/sbin and /usr/local/bin paths to the PATH var.

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> Just modify /root/.bashrc
Issue:
```

sudo nano /root/.bashrc

```
on the last line, insert:
```

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

```
This'll add the /usr/local/sbin and /usr/local/bin paths to the PATH var.
EDIT: removed derp

Yeah that will work. Only for bash scripts though. Do you have a more general solution?

EDIT: Unless sudo calls bash each time it runs?

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> EDIT: removed derp

Yeah that will work. Only for bash scripts though. Do you have a more general solution?

EDIT: Unless sudo calls bash each time it runs?
IIRC: sudo calls bash to execute the commands; bash will read .bashrc first

Try:
```

sudo echo \$PATH

```

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> Just modify /root/.bashrc
Issue:
```

sudo nano /root/.bashrc

```
on the last line, insert:
```

export PATH=$PATH:/usr/local/sbin:/usr/local/bin

```
This'll add the /usr/local/sbin and /usr/local/bin paths to the PATH var.
Ok basically this doesn't work.

If I put:
export PATH="/mydir"

At the end of /etc/bash.bashrc
Or /root/.bashrc

Then when I type: "sudo program" I still get not found.

After all if bash's environment variables were being inherited like expected then where would "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin" even come from?

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> IIRC: sudo calls bash to execute the commands; bash will read .bashrc first
Pretty sure you're completely wrong. This would be nonsensical.

> Try:
```

sudo echo \$PATH

```
I get the "correct" path that way.

However if I call a bash script that is:
```
#!/bin/bash
echo $PATH
```
With: sudo /mydir/myprogram

I still get this unchanging: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin

More importantly when I type in "sudo myprogram" I get "command not found."

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> Ok basically this doesn't work.

If I put:
export PATH="/mydir"

At the end of /etc/bash.bashrc
Or /root/.bashrc

Then when I type: "sudo program" I still get not found.

After all if bash's environment variables were being inherited like expected then where would "/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin" even come from?

Have a look at /etc/environment

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> Have a look at /etc/environment
It consists of: PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

Which is a completely different PATH than:
"/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin"

I doubt changing this would do anything.

EDIT: Tested it just in case. Changing it doesn't do anything.

---

### Post by roelforg on 2012-02-22
I just realized something.
Why does is matter that there's an extra path?

---

### Post by scwizard on 2012-02-22
> **roelforg said:**
> I just realized something.
Why does is matter that there's an extra path?
Because it means when I type in "sudo myprogram" I get "command not found."

For organization purposes I would like to be able to put admin scripts in a special directory /admin. Then call them like "sudo myscript"

Now I really hope you don't start trying to convince me I shouldn't want to do such a thing...

---

### Post by roelforg on 2012-02-22
> **scwizard said:**
> Because it means when I type in "sudo myprogram" I get "command not found."

For organization purposes I would like to be able to put admin scripts in a special directory /admin. Then call them like "sudo myscript"

Now I really hope you don't start trying to convince me I shouldn't want to do such a thing...
I parsed your question as a request to get rid of the /usr/X11R6/bin from the path.
I think we had a communicational error.

---

### Post by scwizard on 2012-02-22
The env_reset option of sudo is responsible for this behavior.

This behavior can be configured in the sudoers file naturally.

---

