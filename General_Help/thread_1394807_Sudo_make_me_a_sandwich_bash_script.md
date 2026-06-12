---
title: "Sudo make me a sandwich bash script"
date: 2010-01-31
forum: General Help
---

### Post by VOLKOV9 on 2010-01-31
So everyone must have had the experience where we've told the terminal some command, but forgot to put sudo in front of it.  So you have to say sudo, then copy and paste it or something.  But presumably at some point this has happened to someone who knows bash scripting better than I do, and that person wrote a bash script (let's call it mmas) that would basicall look like:

```
$ls
thisfile
$mv thisfile there
mv: cannot move `thisfile' to `there': Permission denied
$sudo mmas
$ls
there
```

basically a script that says "look in the scrollback for the most recent command, and do that."

Does this sound possible / does it already exist?  I tried googling for it, but wasn't sure exactly what keywords to use.

Obviously not vital, but it'd be a neat trick / labor-saving device to have.

Thanks in advance!

---

### Post by chewearn on 2010-01-31
The command you are looking for is:
```
sudo !!
```

(Double exclamation marks means previous command.)

---

### Post by jocko on 2010-01-31
That's already possible.
Try this:
```
apt-get update ##gives permission error
sudo !! #repeats last command
```

To learn more about using the shell's history:
```
man history
```

---

### Post by hawthornso23 on 2010-01-31
There is already a mechanism for doing this using the bash history. 

An exclamation mark followed by one or more characters will search your bash command history for the most recent command starting with those characters. Just put sudo in front.

```

$ chown root documents
chown: changing ownership of `documents': Operation not permitted
$ sudo !c
sudo chown root documents
$

```


... or indeed ```
 sudo !! 
``` as others have said.

---

### Post by VOLKOV9 on 2010-01-31
lol thanks all three of you

---

### Post by ajlec2000 on 2010-01-31
Little bits like this is what makes this forum great. Thanks for the question and the answers.

---

### Post by falconindy on 2010-01-31
Make an alias:
```
alias !='sudo'
```
This way, when you want to repeat a command, simply do:
```
$ ! !!
```

---

### Post by audiomick on 2010-01-31
> **falconindy said:**
> Make an alias:
```
alias !='sudo'
```
This way, when you want to repeat a command, simply do:
```
$ ! !!
```

clever, but I think I prefer not having short cuts for "sudo". I like knowing that I am invoking it.

---

### Post by falconindy on 2010-01-31
In addition to being cognicent of the alias you've created, a prompt for your password isn't enough to let you know that you've invoked sudo?

---

