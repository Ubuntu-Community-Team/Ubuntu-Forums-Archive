---
title: "how can i Change  the shell"
date: 2010-01-02
forum: General Help
---

### Post by Creative Lad on 2010-01-02
[FONT=Arial][COLOR=DimGray]
[/COLOR][/FONT][CENTER][FONT=Arial][SIZE=2][COLOR=DimGray][B]hi all body

i have bourne shell i want  to Change  this shell to korn shell but a don't know :(

how can i Change  the shell?

Please  Step by step

thank for all
[/B][/COLOR][/SIZE][/FONT][/CENTER]

---

### Post by |Porsche on 2010-01-02
Check out your /etc/passwd file.
Those line are in the following format:
```
account:password:UID:GID:GECOS:directory:shell
```

Change the portion after the last colon ```
:
``` from /bin/sh to /bin/ksh or which ever shell you want to use.

I hope it helps.

---

### Post by falconindy on 2010-01-02
**Do not directly edit these files!!** There are always utilties to edit them for you! In this case:
```
chsh -s /bin/ksh
```
Or the path to whatever other shell you'd like to switch to. Of course, you'll need to relog for changes to take effect.

---

### Post by Leppie on 2010-01-02
if the shell is installed on your system and you only want to switch temporarily, just type "ksh" (without the quotes) at the cli to switch to the korn shell.

---

### Post by audiomick on 2010-01-02
hallo.
Your question got me curious, so I thought I would try it and see. I seem to have the shell you want installed now. I did the following:

In synaptic package manager
system> administration> synaptic package manager
search for "korn"
This turns up "ksh", which is described as "the original AT&T korn shell"
I installed this. I was prompted to restart, which I did.
It didn't add anything to the applications menu, so I opened the terminal and discovered what Leppie suggested, i.e. if you do
```
ksh
```
in the terminal, the prompt changes, i.e. it opens the korn shell instead of bash.

---

### Post by Leppie on 2010-01-02
and type "exit" to return to your bash shell (or bourne shell in Creative Lad's case) ;)

---

### Post by audiomick on 2010-01-02
> **Leppie said:**
> and type "exit" to return to your bash shell ;)

Thanks! I did
```
bash
```
which also seems to work, or does that leave ksh running?

---

### Post by Leppie on 2010-01-02
> **audiomick said:**
> Thanks! I did
```
bash
```
which also seems to work, or does that leave ksh running?

exactly, you will now have 2 bash shells and 1 korn shell running.

---

### Post by audiomick on 2010-01-02
> **Leppie said:**
> exactly, you will now have 2 bash shells and 1 korn shell running.

Thanks. Learn something every day...;)

---

### Post by Leppie on 2010-01-02
> **audiomick said:**
> Thanks. Learn something every day...;)
you're welcome.
anyways, if you issue the exit command twice, you should only have your initial bash shell.

---

### Post by sisco311 on 2010-01-02
> **Leppie said:**
> and type "exit" to return to your bash shell (or bourne shell in Creative Lad's case) ;)

Ctrl+d works as well.

---

### Post by |Porsche on 2010-01-02
> **falconindy said:**
> **Do not directly edit these files!!** There are always utilties to edit them for you! In this case:
```
chsh -s /bin/ksh
```
Or the path to whatever other shell you'd like to switch to. Of course, you'll need to relog for changes to take effect.

a + b = b + a

---

### Post by sisco311 on 2010-01-02
> **|Porsche said:**
> a + b = b + a

If you really want to edit the passwd file manually, then you should use *sudo vipw*.

chsh 
- allows a user to change his/her login shell in a secure way;
- it's setuid root, so you don't have to authenticate yourself as an admin to change your own login shell;
- it checks if the shell is a valid login shell.

---

### Post by Creative Lad on 2010-01-02
> **|Porsche said:**
> Check out your /etc/passwd file.
Those line are in the following format:
```
account:password:UID:GID:GECOS:directory:shell
```Change the portion after the last colon ```
:
``` from /bin/sh to /bin/ksh or which ever shell you want to use.

I hope it helps.

I did not understand the most elaborate

---

### Post by audiomick on 2010-01-03
The command that falconindy posted
```
chsh -s /bin/ksh
```
makes the change that |Porsche suggested.

|Porsche suggested to change the contents of the file /etc/passwd.

Here is one line from that file on my computer. The line below explains it's format
```
mick:x:1000:1000:Michael Kennedy,,,:/home/mick:/bin/bash
account:password:UID:GID:GECOS:directory:shell
```

This file has many lines, and |Porsche did not say which to change (although I think he meant the one I copied to here), and sisco311 says in post #13 that the suggestion from falconindy is more secure.

I would suggest using the command from falconindy.

---

