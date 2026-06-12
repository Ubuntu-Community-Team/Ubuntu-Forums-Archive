---
title: "Running script with sudo"
date: 2010-08-27
forum: General Help
---

### Post by |Enraiha on 2010-08-27
I'm trying to run a script (test1) that contains commands that need to be run with sudo. The script will run when I have sudo written in the script but I have removed these and want to run the script from the terminal with;

sudo test1

But this gives me 

sudo: test1: command not found

Can anyone tell me what's wrong? Thanks.

---

### Post by AlphaLexman on 2010-08-27
Assuming you are in the same directory as the script and it is executable ->
```
sudo ./test1
```

---

### Post by gzarkadas on 2010-08-27
Current path is not searched by default; use `sudo ./test1'  to run your script. Also, it has to be executable (has x permission enabled). 

If you do not run the command from the directory the script is located, that directory must be in your path; put the script then in a directory contained in the path (or change the path to contain the directory of your script).

@AlphaLexman: greetings, you are faster than me :) .

---

### Post by |Enraiha on 2010-08-27
Thanks a lot that worked:D

But I'm a little confused, the directory it's located in is listed in $PATH so why can't the shell recognise the command without "./"?

---

### Post by DaithiF on 2010-08-27
its in your path, but not in root's.  when you sudo you're executing it as root, so you inherit his or her path, not yours

---

### Post by DaithiF on 2010-08-27
just to add ... this can be confusing, because a simple test like:
sudo echo $PATH
results in your path, not roots being displayed, which might make you think (wrongly) that sudo doesn't mean a change.
but this is because in this example $PATH is being expanded by the shell before sudo is invoked.
if instead you do:
```
sudo bash -c 'echo $PATH'

```or
```
sudo ./pathtest
```
where pathtest contains:
```
echo $PATH
```
then you'll see that is in fact root's path rather than yours.

---

### Post by |Enraiha on 2010-08-27
Oh I see #-o
Thanks for your help.

---

