---
title: "sshd and environment variables"
date: 2009-11-10
forum: General Help
---

### Post by karlson on 2009-11-10
May be I am not searching right for the answers, but here goes:

I need for sshd and rshd to source /etc/profile when executing a remote command.  Currently it is not being done.

I have solved the problem with SSH by putting:

```

SendEnv BASH_ENV *

```
into /etc/ssh/ssh_config

and
```

AcceptEnv BASH_ENV *

```
into /etc/ssh/sshd_config

if BASH_ENV=/etc/profile it will source the file when remote command is attempted.

Can't seem to do the same thing for rshd.

Also it seems that /etc/environment does get sourced whenever bash starts whether in ssh or rsh, but has no effect on sourcing /etc/profile even if the appropriate variable is set, which suggests that it is sourced by the started shell.

Does anyone have any suggestions on resolving this?

---

### Post by karlson on 2009-11-11
bump?

---

### Post by Giblet5 on 2009-11-11
I'm not sure why you're tweaking the system config vs your own private config, but it's your system.

I presume that you have configure ssh to always use protocol 2... SendEnv only works with protocol 2 sessions.

It is a mistake to send the entire environment as there is no guarantee that the environment on box A will be dandy-swell on box B. Choose the explicit values needed, verify that they'll work on both systems, and send just those variables. eg,

SendEnv PATH

---

### Post by karlson on 2009-11-11
> **Giblet5 said:**
> I'm not sure why you're tweaking the system config vs your own private config, but it's your system.


Multiple Users on the system need to run commands that require certain environment variables to be set and there is more then one variable to be set.

> 
I presume that you have configure ssh to always use protocol 2... SendEnv only works with protocol 2 sessions.


I am.

> 
It is a mistake to send the entire environment as there is no guarantee that the environment on box A will be dandy-swell on box B. Choose the explicit values needed, verify that they'll work on both systems, and send just those variables. eg,

SendEnv PATH

Sending Entire Environment is precisely what I am trying to avoid.  The environment during the remote command run should be sourced via /etc/profile not by sending it through the SendEnv/AcceptEnv mechanism.

Setting environment in .ssh/environment also wouldn't work in our case the number of users is not 1 or 2 and maintaining this across more then 5 hosts would be a problem.

The behavior I am describing (source /etc/profile) is actually done by default in RHEL 4 and RHEL 5.  At the moment I don't have a system to put Fedora on to dissect whether this is a bash compile or configuration.

So at the moment I am still at a loss for a solution. :(

---

### Post by karlson on 2009-11-12
> **Giblet5 said:**
> It is a mistake to send the entire environment as there is no guarantee that the environment on box A will be dandy-swell on box B. Choose the explicit values needed, verify that they'll work on both systems, and send just those variables.

Reading your post I think may misunderstand the purpose of BASH_ENV.  It's not the environment settings themselves but the name of the file that provides them.  on Ubuntu it's set to /etc/profile.

---

